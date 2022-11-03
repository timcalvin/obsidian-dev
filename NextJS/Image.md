Using the `Image` tag is not as straight forward as it would be in HTML. It requires several steps.

First you must import the image component.

```jsx
import Image from 'next/image';
```

Next you must permit the domains where you will be pulling images from in the `next.config.js` file.

```jsx
/** @type {import('next').NextConfig} */
const nextConfig = {
	reactStrictMode: true,
	images: {
		domains: ['links.papareact.com', 'image.tmdb.org'],
	},
};

module.exports = nextConfig;
```

Finally you must add the Image component to your file with the required tags.

```jsx
<Image src="https://links.papareact.com/ua6" width={200} height={100} />
```