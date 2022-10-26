## Filtering

```javascript
const words = [
	'spray',
	'limit',
	'elite',
	'exuberant',
	'destruction',
	'present'
];

const filteredWords = words.filter(function (word) {
	return word.length > 6;
});

// OR

const filteredWords = words.filter((word) =>
	word.length > 6;
);
```

It is a good idea, when filtering strings, to convert both string to lowercase, unless you are specifically looking for a case sensitive match.