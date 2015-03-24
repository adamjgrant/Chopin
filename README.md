# Chopin
*Also see [Amadeus](https://github.com/ajkochanowicz/Amadeus) CSS variable conventions*

A CSS selector naming specification to replace BEM

## Why replace BEM?

[BEM](https://en.bem.info/method/) is a good naming strategy for a younger world of web development.
In this world, CSS preprocessors were not nearly as powerful or widely implemented and JavaScript libraries were not as component-sophisticaed as they are today.

Chopin is not just about CSS classes, but CSS selectors in general. It is designed for use with robust backend frameworks and DOM-building JavaScript libraries like **React**

## What does Chopin Do?

Chopin provides a convention for **succinct**, **namespaced**, **componentized** CSS classes. 

## How to use

The user should strive to write very simplistic, one or two word classes like

    `.bio`, `.news-item`, `.cancel`
    
This is made possible by namespacing with the following properties:

  - controller/action (optional)
  - component
  - element 

### Controller/Action

This is essentially the page or page class. If using a backend MVC framework like Rails, this should map directly to the respective controller and action.

    [data-controller="products"] {
      // Styles to be applied to all product pages
    }
        
    [data-controller="products"][data-action="show"] {
      // Styles to be applied only to a product view page.
    }
        
Of course, you shouldn't have to write your CSS page by page, so this is an optional namespace.

These selectors target the `data-[property]` attribute on HTML elements

    <body data-controller="products" data-action="show">
        
### Component

A component is a top-level controllable item having an aggregate of elements.

Examples: Slideshows, sidebars, message window, anything that is not a whole page or just a small element of the page.

    [data-controller="products"] {
      [data-component="product"] {
        // Applies only to a product thumbnail, but only on product pages.
      }
    }
    
    [data-component="product"] {
      // Applies to all product thumbnail components.
    }

(Working on this draft. Thanks for your patience)
