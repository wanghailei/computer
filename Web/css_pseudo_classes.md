





### :is

The `:is` pseudo-class can be used to write large selectors more concisely.

```css
.contact-form input,
.contact-form textarea,
.contact-form select,
.contact-form button {
	border: 1px solid var(--brand-color);
}

/* :is makes writing selectors easier. */
.contact-form :is(input, textarea, select, button) {
	border: 1px solid var(--brand-color);
}
```

The `:is()` selector does not work with pseudo-element selectors, but only with pseudo-classes.

```css
:is(div::before, div::after)  /* This is invalid. */
:is(:first-child) /* This is valid. */
```



### :where







