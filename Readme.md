# SASS Snippets
## Table of Contents
1. [Spacing](#spacing)
## Spacing

### Snippet
``` scss 
$spacer: 5px !default;
$spacer-x: $spacer !default;
$spacer-y: $spacer !default;
$spacers: ( 0: ( x: 0, y: 0 ),
auto: ( x: auto, y: auto ),
              5: ( x: $spacer-x, y: $spacer-y ),
              10: ( x: ($spacer-x * 2), y: ($spacer-y * 2) ),
              15: ( x: ($spacer-x * 3), y: ($spacer-y * 3) ),
              20: ( x: ($spacer-x * 4), y: ($spacer-y * 4)) ,
              30: ( x: ($spacer-x * 6), y: ($spacer-y * 6)) ) !default;

@each $prop, $abbrev in (margin: m, padding: p) {
    @each $size, $lengths in $spacers {
        $length-x: map-get($lengths, x);
        $length-y: map-get($lengths, y);

        .#{$abbrev}-a-#{$size} {
            #{$prop}: $length-y $length-x !important;
        }

        .#{$abbrev}-t-#{$size} {
            #{$prop}-top: $length-y !important;
        }

        .#{$abbrev}-r-#{$size} {
            #{$prop}-right: $length-x !important;
        }

        .#{$abbrev}-b-#{$size} {
            #{$prop}-bottom: $length-y !important;
        }

        .#{$abbrev}-l-#{$size} {
            #{$prop}-left: $length-x !important;
        }

        // Axes
        .#{$abbrev}-x-#{$size} {
            #{$prop}-right: $length-x !important;
            #{$prop}-left: $length-x !important;
        }

        .#{$abbrev}-y-#{$size} {
            #{$prop}-top: $length-y !important;
            #{$prop}-bottom: $length-y !important;
        }
    }
}
```          

### Usage
Creates css classes for spacing (margin and padding)  
CSS Class Name : `(spacing-type)-(direction)-(size)`
* Spacing-type: `m` for margin or `p` for padding.
* Direction:
  * `t`,`b`,`l` or `r` (for top, bottom left or right). 
  * `x` for top and bottom,`y` for top and bottom.
* Size: `0`, `auto`, `5`, `10`, `15`, `20`, `30` (in px)  

``` html
<div class="m-x-10 p-t-0"></div> <!-- margin-left and margin-right :10; padding-top : 0; -->
```
  

**[Back to top](#table-of-contents)**

