Bootstro.js
========
Tiny JS library taking advantage of bootstrap's popover to help guide your users around. 

Forked from <a href="https://github.com/clu3/bootstro.js">clu3/bootstro.js</a>, original documentation and demo <a href='http://clu3.github.com/bootstro.js'>here</a>.


## Changes and additions
* Removed backdrop (dark overlay)
* Added support for dynamic content when using selectors.
* Added triggers for "next" step when clicking custom elements.
* Added custom top positioning for popovers placed on left or right of an element. Useful when you want a popover to point at a dropdown itself, not in the middle of its content when expanded.
* width attribute sets max-width instead of width. (it wasn't working for me)

## Documentation
*Only listing newly added options, see <a href='http://clu3.github.com/bootstro.js'>original documentation</a> for the basics.*
* **top** : For popovers placed on left or right of an element, override its top (relative to element) using this value.
* **action** : Atm, it can only take one value: "next". If specified, bootstro.nextWithDelay() will be triggered on click. This trigger will only be active while this "tour step" is active. This actions are delayed 500ms by default (explicitly added to wait for dropdown animations).
* **selector-next** : By default, the element that triggers `action: "next"` is the selector itself. You can specify another selector that will be used to trigger the action instead.
* **dynamic** : Must contain an html tag that will be used to hold all data attributes while the dynamic element is not yet added to the DOM. When using dynamic elements, add `<div class="hidden bootstro-dynamic-elements"></div>` just after the `<body>` tag.


*Example:*
```
{
 "selector": ".selector01",
 "title": "Title goes here.",
 "content": "Content goes here.",
 "top": "20px", //override popover's top position relative to the element matching the selector
 "nextButton": "<span></span>", //hide next button
 "prevButton": "<span></span>", //hide prev button
 "step": "0",
 "action": "next", //it will automatically trigger "next" action after 500ms when clicking the selector
 "selector-next": ".selector01 > a", //overrides the selector that will trigger "next" action.
 "placement": "right"
},
{
 "selector": ".selector02:last", //Since a dummy element is added (hidden) at the beggining of the body, you have to add ":last" to the selector so it won't select the dummy when the dynamic one is already present.
 "title": "Title goes here.",
 "content": "Content goes here.",
 "width": "600px",  //equivalent to "max-width: 600px;"
 "step": "1",
 "dynamic": "<li class=\".selector02\"></li>", //will be used to hold all data attributes while the dynamic element is not yet added to the DOM
 "placement": "bottom"
}
```
#### Fully working example can be found <a href="https://github.com/Theadd/TorrentzRSS/blob/master/js/rssz-tour.js">here</a>, which can be tested by taking a tour on <a href="http://theadd.github.io/TorrentzRSS/">this page</a>.


License 
========
<a href='http://opensource.org/licenses/MIT'>MIT</a>
