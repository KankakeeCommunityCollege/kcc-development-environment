# Global Navigation/Mega Nav

Global navigation uses a mega-nav style navigation. The functionality of our mega-nav is to display the navigation options on mouse hover.

## Functionality

Our custom mega-nav functionality works *with* Bootstrap 4's dropdown menu. The Bootstrap 4 dropdown menu uses `bootstrap.js` to target data-attributes in the HTML markup. With a little extra CSS, the mega-nav mouse-hover functionality can be achieved. This CSS-only approach allows us to augment the Bootstrap 4 dropdown system with a little extra functionality that won't interfere.
```scss
@media screen and (min-width: 992px) {
   .header-global__nav-bottom .dropdown:hover .dropdown-menu,
   .header-global__nav-bottom .dropdown .dropdown-menu:hover {
     display: block !important; // Because Bootstrap loves to use !important
   }
}
```

With the addition of CSS animation the mega-nav feels more reformed:
```scss
@keyframes meganav {
   0% {
     opacity: 0;
   }
   100% {
     opacity: 1;
   }
}

@media screen and (min-width: 992px) {
   .header-global__nav-bottom .dropdown:hover .dropdown-menu,
   .header-global__nav-bottom .dropdown .dropdown-menu:hover {
      animation-duration: .5s;
      animation-name: meganav;
      display: block !important; // Because Bootstrap loves to use !important
   }
}
```
