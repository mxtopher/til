overflow-x and overflow-y aren't independent
============================================

When you have a block element with width or height specified, and it's content is larger than the specified sizes, you have some options to handle the overflow. The `overflow` property accepts the following values:

- **visible (default):** The content is shown, regardless of container size.
- **hidden:** The content is clipped. Everything beyond the container size is invisible.
- **scroll:** The content is clipped but a scrollbar is added to show the rest of the content. It will always show the scrollbar.
- **auto:** The content is clipped but a scrollbar is added to show the rest of the content. It will only show the scrollbar when necessary.
- **initial and inherit**, as usual.

If you want the overflow behavior to be different on vertical and horizontal dimensions, you have `overflow-x` and `overflow-y`, which accept the same values.

The problem is that `visible` doesn't work well with others. If you are using visible for either `overflow-x` or `overflow-y` and something other than `visible` for the other, the `visible` value is interpreted as `auto`. Moreover, since `visible` is the default value, simply setting one or another as anything but `visible` sets the other one as `auto`.

```css
.some-div {
    overflow-x: scroll;
    overflow-y: visible; /* It will be auto */
}

.some-other-div {
    overflow-x: visible; /* It will be auto */
    overflow-y: hidden;
}

.yet-another-div {
    overflow-x: hidden;
    /* overflow-y is now auto (!!!) */
}
```

You can circumvert it by adding `overflow-x` and `overflow-y` to different elements. It may require adding a wrapping container to your html.
