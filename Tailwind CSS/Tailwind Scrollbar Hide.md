To hide scroll bars install:

```terminal
# Using npm
npm install tailwind-scrollbar-hide

# Using Yarn
yarn add tailwind-scrollbar-hide
```

Then add the plugin to your `tailwind.config.js` file:

```jsx
plugins: {
	require('tailwind-scrollbar-hide')
}
```

To use add `scrollbar-hide` to your classnames for the container that has a scrollbar you would like to hide.