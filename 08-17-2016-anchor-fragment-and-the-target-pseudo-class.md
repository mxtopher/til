Anchor, Fragment, and the :target Pseudo Class
==============================================

Everything you put after a # on an url is a fragment

[https://en.wikipedia.org/wiki/Fragment_identifier#Examples](https://en.wikipedia.org/wiki/Fragment_identifier#Examples)

If you put as fragment the id of an element on your page,
the page will automatically scroll to this element when loaded.

You can also style this element with css using the :target
pseudoclass.

```css
:target {
  border-color: red;
}
```

If you have many views in a Single Page Application, it is really easy
to just show one of them without any javascript:


```css
.view {
  display: none;
}

.view:target {
  display: block;
}
```

Then you just link to the id of the view you want, as in

```html
<a href="#nextview">Next</a>
```

and you will show the next view and hide the current one.
