# Spacing

This snippets will create css classes for spacing (margin and padding)
CSS Class Name : 
```
(spacing-type)-(direction)-(size)
```

##Description
###spacing-type 
```[“m” for margin / “p” for padding]```
###direction 
```[“a” for all / “t” for top /b” for bottom /”r” for right /”l” for left /”x” for left and right /”y” for top and bottom]```
###size
```[0 / 5 / 10 / 15 / 20 / 30 / "auto" for auto]```

##Example
``` html
<div class="m-x-10 p-t-0"></div> <!-- margin-left and margin-right :10; padding-top : 0; -->
```
>Absolute numbers (5/10/15) could be replaced by bootstrap semantic sizes (xs/sm/md/lg/xl/xxl) to create semantic spacing snippets.
>Like m-x-lg p-y-sm.

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
