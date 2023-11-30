---
title: Crosscutting concepts
---

# Crosscutting concepts


# Deployment view

## Frontend

### 8.1 Dependencies
For the UI components:<br>
https://ant.design/components/overview/

For routing: <br>
https://reactrouter.com/

I18N Internationalization: <br>
https://react.i18next.com/

MSAL User authentication: <br>
https://github.com/microsoft/Federal-App-Innovation-Community/tree/main/topics/modern-auth/React-MSAL-AAD


### 8.3 User Interface
The design was previously mapped in Figma to give the developer a clear idea of the final product and to create a common basis for discussion.

Link to Figma Design: <br>
https://www.figma.com/file/umOKw8yF0RbQyPkU4B7bIe/SmashGrade?type=design&node-id=111-2817&mode=design&t=JDM3bRnav0m3z2Re-0


As a UI library we use Antd, which allows us to use predefined base components such as forms, buttons, etc...

#### Global SCSS
In React we can define a global scss file to apply some styles to all pages, such as the font-color or text-size.

Example:
```scss
body {
  font-family: 'Roboto', sans-serif;
}
```

#### Colors Module SCSS
So that colors for backgrounds, buttons and validators have the same colors on all pages, a Colors module is also created in which the standard colors can be recorded and reused.

Example:
```scss
$colorPrimary: #c6264e;
$colorSecondary: #d9d9d9;
$colorTertiary: #ebebeb;
$colorTextHeading: #ffffff;
$colorBgContainer: #ffffff;
$colorBgContainerHighlight: lightgrey;
$colorLink: #c6264e;
$colorLinkHover: #3d3d3c;
$colorLinkActive: #95223f;
$colorRatingGood: #b1ffa5;
$colorRatingBad: #ff728b;
$colorRatingMedian: #ffd76f;

:export {
    colorPrimary: $colorPrimary;
    colorSecondary: $colorSecondary;
    colorTertiary: $colorTertiary;
    colorTextHeading: $colorTextHeading;
    colorBgContainer: $colorBgContainer;
    colorBgContainerHighlight: $colorBgContainerHighlight;
    colorLink: $colorLink;
    colorLinkHover: $colorLinkHover;
    colorLinkActive: $colorLinkActive;
    colorRatingGood: $colorRatingGood;
    colorRatingBad: $colorRatingBad;
    colorRatingMedian: $colorRatingMedian;
}
```

#### Color Schema
We developed the color scheme according to the HFTM corporate design.

| Farbvariable   | Hex-Wert  |
| -------------- | --------- | 
| Primary        | `#C6264E` | 
| On Primary     | `#FFFFFF` | 
| Secondary      | `#95223F` | 
| On Secondary   | `#FFFFFF` | 
| Background     | `#E4E4E4` | 
| On Background  | `#3D3D3C` |
| Neutral 300    | `#f2f2f2` | 
| Neutral 200    | `#f9f9f9` | 


| primary & secondary   | background & neutrals  |
| -------------- | --------- | 
| ![image](.\primary-secondary-color.png)| ![image](.\background-color.png) | 



#### SCSS Styles in React Components
Typical structure

components: <br>
├───SelectWithTitle.tsx <br>
├───SelectWithTitle.module.scss

Here you can see the structure of a typical React component in our project. To import and use the styles correctly, please note the following points:
- The SCSS files should have `.module.scss` in the name (e.g., `SelectWithTitle.module.scss`). This is the only way for autocomplete to work correctly and enable local scope for CSS class names.

- Import the styles with the following syntax:
```javascript
import styles from './SelectWithTitle.module.scss';
```

- To access SCSS elements, use the styles object:
```javascript
<div className={styles.selectWithTitleContainer}>
  {/* Here your content*/}
</div>
```

- When defining the SCSS elements, always use **camelCase**. This makes it easier to access via the styles object in React. For example:

This approach limits styles to the respective component, which avoids naming conflicts.

### 8.4 Validation
To validate the data in the frontend, we rely on the functions of Antd Forms. It is possible to use predefined functions such as required or to use CustomValidators.

Example:
```TS
const notNullValidator: Rule = {
    required: true,
    message: 'Input is required != null',
};
```

### 8.5 Error handling
We also rely on the Ant components to display error messages visually.

We can see relevant examples here:
https://ant.design/components/form#rule

### 8.7 Testability
Due to the amount of work involved, we will initially avoid unit tests and rely on manual system tests.


To test the different roles you can use the follwing script:
```PowerShell
# Define the user and application (replace with your values)
Install-Module AzureAD
```
```PowerShell
Connect-AzureAD
$app_role_name = "Kurs Admin" # Dozent | Kurs Admin | Student
$mail = "wanja.bachmann@hftm.ch"

$user = Get-AzureADUser -ObjectId $mail
$userdisplayname = (Get-AzureADUser -ObjectId $mail).displayname
$app_name = "transfer2023-smashgrade"
$appRegistrationObjectId = (Get-AzureADApplication -Filter "DisplayName eq 'transfer2023-smashgrade'").ObjectId


# Roles
# $user = Get-AzureADUser -ObjectId "$username"
$sp = Get-AzureADServicePrincipal -Filter "displayName eq '$app_name'"
$appRole = $sp.AppRoles | Where-Object { $_.DisplayName -eq $app_role_name }

# Get the App Role assignments for the user
$rmAppRoleAssignments = 
	Get-AzureADUserAppRoleAssignment -ObjectId $user.ObjectId |`
	Where-Object {($_.ResourceDisplayName -eq $app_name) -and ($_.PrincipalDisplayName -eq $userdisplayname)}

# Remove all direct assignments
foreach($assignment in $rmAppRoleAssignments){
	Remove-AzureADUserAppRoleAssignment -ObjectId $user.objectId -AppRoleAssignmentId $assignment.objectId
}

# Assign the user to the app role
New-AzureADUserAppRoleAssignment -ObjectId $user.ObjectId -PrincipalId $user.ObjectId -ResourceId $sp.ObjectId -Id $appRole.Id

# Get the App Role assignments for the user
$appRoleAssignments = 
	Get-AzureADUserAppRoleAssignment -ObjectId $user.ObjectId |`
	Where-Object {$_.ResourceDisplayName -eq $app_name}

# Create a dictionary to map App Role Id to Description
$roleDescriptions = @{}
$sp.AppRoles | ForEach-Object { 
	$roleDescriptions[$_.Id] = $_.Description 
}

# Initialize an array to store the results
$results = @()

# Loop through each App Role assignment
foreach ($assignment in $appRoleAssignments) {
    $roleDescription = $roleDescriptions[$assignment.Id]
    
    # Create a custom object with the App Role Description
    $result = [PSCustomObject]@{
        "RoleDescription" = $roleDescription
        "PrincipalDisplayName" = $assignment.PrincipalDisplayName
        "PrincipalType" = $assignment.PrincipalType
        "ResourceDisplayName" = $assignment.ResourceDisplayName
        "CreationTimestamp" = $assignment.CreationTimestamp
    }
    # Add the result to the array
    $results += $result
}

# Display the results
$results | Format-Table -AutoSize
```