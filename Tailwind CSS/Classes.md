## Samples of standard classes
---
- h-8 == Height of 8
- mb-1 == margin bottom of 1
- opacity-0 == opacity of 0
- tracking-widest == widest tracking

## Hover state
---
To add a class to a hover state, add `hover:` before the class name.

```jsx
<p className="opacity-0 hover:opacity-100 tracking-widest">
```

## Groups
---
To group multiple items together, give the container a class name like this:

```jsx
<div className="group">
	<Icon className="h-8 mb-1" />
	<p className="opacity-0 group-hover:opacity-100 tracking-widest">
		{title}
	</p>
</div>
```