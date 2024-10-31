### em

The em in CSS originated from metal typography unit "em quadrat". A quadrat is a metal spacer used in typesetting, and its height equals to the line height of the metal body from which the letter rises. A quadrat of em size is a square, and a quadrat of en size is half width of em.

A digital typography, an **em** is a grid with arbitrary resolution. Scaling the em to a particular point size is how imaging systems work, whether for screen or print. In digital type, the relationship of the height of particular letters to the em is that, as a very rough guideline, an "average" font might have a cap height of 70% of the em, and an x-height of 48% of the em.

In Cascading Style Sheets, the em unit is the height of the font in nominal points or inches. The actual, physical height of any given portion of the font depends on the user-defined DPI setting, current element font-size, and the particular font being used.

### rem

To make style rules that depend only on the default font size, another unit was developed: the rem. The rem «rem Unite», or root-em, is the font size of the root element of the document. Unlike the em, which may be different for each element, the rem is constant throughout the document.



### Make Chinese or Japanese text vertically

```css
.container {
	writing-mode: vertical-rl;
	text-orientation: upright;
}
```



