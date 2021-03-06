# Step 2.3: Theming and Styling

[Lessons](../) | [Exercise](./exercise/) | [Demo](./demo/)

Theming and Styling with UI Fabric. In this section, we will illustrate how to utilize some of the built-in theming and styling features right inside UI Fabric component library. UI Fabric exposes its own css-in-js library called `mergeStyles` that is very performant compared with other similar libraries.

A CodePen that illustrates what `mergeStyles` does: https://codepen.io/dzearing/pen/jGdgrE?editors=1011

There are three areas that we should focus on in this step:

1. Theming with Fabric
2. CSS-in-JS with mergeStyles
3. Customizing Fabric Components `styles` prop

## 1. Theming with Fabric

- Fabric applies themes by propagating the theme down the children through the React Context mechanism
- It is applied with the `<Customizer>` component
- There are some predefined themes within Fabric already, like Fluent (which will become the default in the next major), MDL2, Azure, and some other sample themes like Teams.
- Take a look at `demo/src/components/TodoApp.tsx`

## 2. CSS-in-JS with mergeStyles

- `mergeStyles` is a styling library that creates CSS class from styles that are expressed in JS
- These classes can be passed into `className` prop of any component like `<div>`
- This library replaces the need to import CSS stylesheets because they are bundled as normal JS code
- Take a look at `demo/src/components/TodoApp.tsx`

## 3. Customizing Fabric Controls

- calling `mergeStyles` is time consuming and very static
- Fabric components expose a `styles` prop (not to be confused with the React built-in one called `style`)
- You can use intellisense to discover which parts of the component you can to customize
- You can even use a style function to change the style based on some style prop
- Take a look at these customizations in `demo/src/components/TodoHeader.tsx`

# Exercises

## Themes - Using Predefined Theme

Apply some included and predefined themes from the UI Fabric package inside the `/step2-03/exercise/src/components/TodoApp.tsx`. Do this by replacing:

```ts
import { FluentCustomizations } from '@uifabric/fluent-theme';
```

with:

```ts
import { TeamsCustomizations } from '@uifabric/theme-samples';
```

## Themes - Customized Theme

Create your own theme and apply the color here: https://developer.microsoft.com/en-us/fabric#/styles/themegenerator

```ts
import { loadTheme } from 'office-ui-fabric-react';

loadTheme({
  palette: {
    themePrimary: '#0078d4',
    themeLighterAlt: '#eff6fc',
    themeLighter: '#deecf9',
    themeLight: '#c7e0f4',
    themeTertiary: '#71afe5',
    themeSecondary: '#2b88d8',
    themeDarkAlt: '#106ebe',
    themeDark: '#005a9e',
    themeDarker: '#004578',
    neutralLighterAlt: '#f8f8f8',
    neutralLighter: '#f4f4f4',
    neutralLight: '#eaeaea',
    neutralQuaternaryAlt: '#dadada',
    neutralQuaternary: '#d0d0d0',
    neutralTertiaryAlt: '#c8c8c8',
    neutralTertiary: '#c2c2c2',
    neutralSecondary: '#858585',
    neutralPrimaryAlt: '#4b4b4b',
    neutralPrimary: '#333333',
    neutralDark: '#272727',
    black: '#1d1d1d',
    white: '#ffffff'
  }
});
```

1. Delete the `Customizer` component

2. Paste in this code in the `TodoApp.tsx` before the `TodoApp` component definition

3. Play around with the values and use intellisense to discover the `ITheme` type within VS Code

## CSS in JS with MergeStyles

The styling library name is glamorous nor does it bring about emotion, but it is very quick and lightweight. `MergeStyles` turns CSS Rules into CSS class names to be applied to the components.

1. Try applying a merged style `className` as a prop inside `TodoApp`

```tsx
import { mergeStyles } from 'office-ui-fabric-react';

const className = mergeStyles({
  backgroundColor: 'red',
  selectors: {
    ':hover': {
      backgroundColor: 'blue'
    }
  }
});
```

2. Try to give a few components extra padding

## Customize the Fabric Components

1. Open `exercise/src/components/TodoFooter.tsx`

2. Find the `<DefaultButton>` and insert a `styles` prop

3. Try to customize this with a styles object (let the Intellisense of VS Code guide you on what you can use to customize)

4. Try to customize this with a styles function
