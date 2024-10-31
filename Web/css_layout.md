











### To vertically align a flex item in the middle of a flex container:

```css
.container {
	display: flex; /* turns the .container into a flex container. */
	height: 100vh; /* ensures the container fills the full height of the viewport. */
	align-items: center; /* Vertically centers the flex items */
}
```

If you want to centre just one specific flex item, you can also target it individually with align-self:

```css
.item {
	align-self: center;
}
```

x





Let me know if you need further adjustments!





```css
:where(#main) {
	container-type: inline-size;
	font-size: var(--font-medium-responsive);
	inline-size: 67ch;
	margin-inline: auto;
	max-inline-size: 100vw;
	padding-block-end: clamp(var(--block-space), 5%, calc(var(--block-space) * 3));
	padding-inline: clamp(var(--inline-space), 5%, calc(var(--inline-space) * 3));
	text-align: center;

}
```



