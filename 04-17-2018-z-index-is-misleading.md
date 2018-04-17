z-index is misleading
=====================

The css z-index property is extremely misleading. The definition on MDN is
"The z-index CSS property specifies the z-order of a positioned element and its descendants".

Some things can be naturally derived from that sentence, and these are usually the gotchas covered in many tutorials

It doesn't change the z-order of not explicitly positioned elements
-------------------------------------------------------------------

If the element you're setting the z-index of doesn't have a position of either relative, absolute, fixed, or sticky
the z-index property will be completely ignored. Period.

The decendents of the element are affected
------------------------------------------

If you set the z-index of an element, all children are affected. They don't have to have positioning of their own.

However there's one quirk with children that is rarely mentioned

Setting z-index on an element creates a new stack context, and children z-indexes are irrelevant outside of that stack context.
===============================================================================================================================

Some weird consequences:

Setting a higher z-index than the parent is unecessary
------------------------------------------------------

unless you have other children that also have z-indexes competing for space.

```scss
    #parent {
        z-index: 100;
        position: relative;
        #child {
            z-index: 150; // It doesn't do anything, it was already going to show on top of parent
        }
    }
```

Setting a lower z-index than the parent is useless
--------------------------------------------------

The child is inside the parent's stack context. It's z-index will be compared with the other children, not with the parent.

```scss
    #parent {
        z-index: 100;
        position: relative;
        #child {
            z-index: 50; // It doesn't do anything, it still show on top of parent
        }
    }
```

And the most bogus of them all

There is no way to overcome the parents z-index. At all.
--------------------------------------------------------

If your parent has a low z-index and is being covered by another element with a higher z-index, your element will be covered as well.
They are different stack contexts, raising the child z-index won't work.

```scss
    #parent-1 {
        z-index: 500;
        position: relative;
    }

    #parent-2 {
        z-index: 100;
        position: relative;
        #child-2 {
            z-index: 1000; // #child-2 will still be covered by #parent-1 and everything inside it.
        }
    }
```

![alt text](/pictures/z-indexes.png "z indexes")