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

![Home view](http://cdn.everything.io/chopin/home.png)

    [data-controller="home"] {
      background-color: blue;
    }

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

![Product index](http://cdn.everything.io/chopin/products_index.png)

    [data-component="product"] {
      background-color: violet;
    }

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
    
### Element

![Product page](http://cdn.everything.io/chopin/products_show.png)
![Product index](http://cdn.everything.io/chopin/products_index.png)

    [data-component="product"] {
      img {
        background-color: darkviolet;
      }
    }

Elements can be HTML elements or just very small sets of elements that don't qualify in one's mental model as a "component" ([I know it when I see It](http://en.wikipedia.org/wiki/I_know_it_when_I_see_it))

Element naming is stupidly simple, as it should be. Chopin's element naming leads to smaller, more readable HTML and more manageable, modular CSS.

Elements should be well-namespaced and simplistic

    [data-controller="products"] {
      [data-component="product"] {
        .title {
          // The title of only product thumbnails, but only on product pages.
        }
      }
    }
    
    [data-component="product"] {
      .title {
        // The title of only product thumbnails.
      }
    }
    
    .title {
      // Not recommended. Applies to all title classes.
    }

(Working on this draft. Thanks for your patience)
