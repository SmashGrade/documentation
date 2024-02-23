---
title: Architecture decisions
---

# Architecture decisions

## Internationalization

### Question
There should be the possibility of internationalization for the UI. But which module should we use?

### Decision
The following table serves as a quick comparison of 5 of the most popular I18N solutions for React:

| Name | Stars | Forks | Contributors | Commits | Alter | Snyk Score |
| --- |-------|-------|--------------|---------|---------|------------|
| react-i18next | 8.5k  | 1k    | 177          | 1'630   | 8 years | 94/100     |
| FormatJS | 13.9k | 1.4k  | 283          | 4'688   | 9 years | 98/100     |
| react-native-localization | 893   | 120   | 41           | 239     | 8 years | 73/100     |
| typesafe-i18n | 1.8k  | 65    | 33           | 1'582   | 3 years | 81/100     |
| js-lingui | 3.9k  | 354 | 188 | 2'283   | 6 years | 95/100     |

The current downloads of the packages can be seen under the following link:
[Link](https://npmtrends.com/@lingui/react-vs-react-i18next-vs-react-intl-vs-react-native-localization-vs-typesafe-i18n) 
Based on this comparison and the number of downloads, we decided to analyze `react-i18next` and `react-intl` in more detail.

We recommend using `react-intl` as the included functionality is sufficient for our project out-of-the-box and the bundle size is comparatively smaller.

### Usage
Under [FormatJS Components](https://formatjs.io/docs/react-intl/components) und [FormatJS Imperative API](https://formatjs.io/docs/react-intl/api) are the most important components and functions  described.

Use the components by default if possible. If the translation cannot be implemented with components, you have to use the `useIntl()` function.
The following three properties must always be set within the translation:
- `id`: Should be given in the context of the translation
- `defaultMessage`: The fallback translation, always specified in German
- `description`: A detailed description of the translation in German

Extract translation:  
```shell
npm run extract-de # extract German messages
npm run extract-en # extract English messages
npm run extract-fr # extract French messages
```
Compile tranlsation:  
```shell
npm run compile-de # compile German messages
npm run compile-en # compile English messages
npm run compile-fr # compile French messages
```


## Routing
### Question
These two routers were implemented and compared with each other:
- [https://reactrouter.com/](https://reactrouter.com/)
- [https://reactrouter.com/](https://tanstack.com/router/v1)

The branches can be found here:
- React-Router: [https://github.com/SmashGrade/SmashGrade-App/tree/%2312-react-router-dom](https://github.com/SmashGrade/SmashGrade-App/tree/%2312-react-router-dom)
- TanStack-Router: [https://github.com/SmashGrade/SmashGrade-App/tree/%2312-tanstack-routing](https://github.com/SmashGrade/SmashGrade-App/tree/%2312-tanstack-routing)

### Decision
Based on the comparison on the page [https://tanstack.com/router/v1/docs/comparison](https://tanstack.com/router/v1/docs/comparison) we would use the TanStack router. In our opinion, the overview of the route tree is also better than with the “classic” React router

### Usage
The documentation can be found here:
[https://tanstack.com/router/v1/docs/guide/routes](https://tanstack.com/router/v1/docs/guide/routes)

