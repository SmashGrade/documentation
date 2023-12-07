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
https://tanstack.com/router/v1

I18N Internationalization: <br>
https://react.i18next.com/

MSAL User authentication: <br>
https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react


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
So that colors for backgrounds, buttons and other UI components have the same colors on all pages, a Colors module is also created in which the standard colors can be recorded and reused.

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

| Color variable   | Hex-Value  |
| -------------- | --------- | 
| <span style="color:#C6264E">Primary</span> | `#C6264E` | 
| <span style="color:#FFFFFF">On Primary</span> | `#FFFFFF` | 
| <span style="color:#95223F">Secondary</span> | `#95223F` | 
| <span style="color:#FFFFFF">On Secondary</span> | `#FFFFFF` | 
| <span style="color:#E4E4E4">Background</span> | `#E4E4E4` | 
| <span style="color:#3D3D3C">On Background</span> | `#3D3D3C` |
| <span style="color:#f2f2f2">Neutral 300</span> | `#f2f2f2` | 
| <span style="color:#f9f9f9">Neutral 200</span> | `#f9f9f9` | 


| Primary & Secondary   | Background & Neutrals  |
| -------------- | --------- | 
| ![image](..\assets\crosscutting_concepts\primary-secondary-color.png)| ![image](..\assets\crosscutting_concepts\background-color.png) | 



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
https://github.com/SmashGrade/SmashGrade-App/wiki/Entra-ID-Authentication