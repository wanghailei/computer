

## 





Of all the grid setup syntax, I think the best one is using `span`.

```css
.card {
     grid-column: span 4;
     grid-row: span 2
}
```





## [Introduction to subgrid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Subgrid#introduction_to_subgrid)

When you add `display: grid` to a grid container, only the direct children become grid items and can then be placed on the grid you created. ==The children of these items display in normal flow.==

You can "nest" grids by making a grid item a grid container. These grids, however, are independent of the parent grid and of each other, meaning that they do not take their track sizing from the parent grid. ==This makes it difficult to line nested grid items up with the main grid.==

If you set the value `subgrid` on `grid-template-columns`, `grid-template-rows` or both, instead of creating a new track listing the nested grid uses the tracks defined on the parent.

For example, if you use `grid-template-columns: subgrid` and the nested grid spans three column tracks of the parent, the nested grid will have three column tracks of the same size as the parent grid. Gaps are inherited but can also be overridden with a different [`gap`](https://developer.mozilla.org/en-US/docs/Web/CSS/gap) value. Line names can be passed from the parent into the subgrid, and the subgrid can also declare its own line names.

## [Subgrid for columns](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Subgrid#subgrid_for_columns)

In the example below, I have a grid layout with nine `1fr` column tracks and four rows that are a minimum of 100px tall.

I place `.item` from column lines 2 to 7 and rows 2 to 4. I then make this grid item into a grid, giving it column tracks that are a subgrid and defining rows as normal. As the item spans five column tracks, this means that the subgrid has five-column tracks. I can then place `.subitem` on this grid.

The rows in this example are not a subgrid, and so behave as a nested grid does normally. The grid area on the parent expands to be large enough for this nested grid.

Note that line numbering restarts inside the subgrid — column line 1, when inside the subgrid, is the first line of the subgrid. The subgridded element doesn't inherit the line numbers of the parent grid. This means that you can safely lay out a component that may be placed in different positions on the main grid, knowing that the line numbers on the component will always be the same.

## [Subgrid for rows](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Subgrid#subgrid_for_rows)

The next example is the same setup; however, we are using `subgrid` as the value of `grid-template-rows` and defining explicit column tracks. So, the column tracks behave as a regular nested grid, but the rows are tied to the two tracks that the child spans.













## [Using subgrids](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout/Subgrid#using_subgrids)

Other than needing to take care of items that do not fit in your subgrid, ==a subgrid acts very similarly to any nested grid; the only difference is that the track sizing of the subgrid is set on the parent grid.== As with any nested grid, however, the size of the content in the subgrid can change the track sizing, assuming a track sizing method is used that allows content to affect the size. In such a case, auto-sized row tracks, for example, will grow to fit content in the main grid and content in the subgrid.

As the subgrid value acts in much the same way as a regular nested grid, it is easy to switch between the two. For example, if you realize that you need an implicit grid for rows, you would need to remove the `subgrid` value of `grid-template-rows` and perhaps give a value for `grid-auto-rows` to control the implicit track sizing.









```css
.container {
     display: grid;
     grid-template-columns: repeat( 3, minmax(100px, 1fr) );
     grid-template-rows: repead( 2, auto ) 1fr auto;
}
.card {
     display: grid;
     grid-tempalte-rows: subgrid;
     grid-row: span 4; /* Without this, all divs will be squezed into the first row. */
}
.card h1 {
     align-self: start;
}
.card nav {
}
.card p {
}
.card button {
}
```



## Implicit Grid

You might even have an unknown number of items retrieved from a database. In these cases, it’ll probably make more sense to loosely define a grid and then allow the grid item placement algorithm to fill it for you. This will require you to rely on an **implicit grid**.

Uses `grid-auto-rows` to specify a `1 fr` size for all implicit grid rows, so each row will be the same height.

The properties `grid-auto-columns` and `grid-auto-rows` can be applied to the grid container to specify a different size for all implicit grid tracks (for example, `grid-auto-columns: 1fr;`).

## `repeat()`

```css
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
```

The `auto-fill` keyword is a special value you can provide for the `repeat()` function. With this set, the browser will place as many tracks onto the grid as it can fit, without violating the restrictions set by the `minmax()` values.
