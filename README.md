# LESS-Neat

## A semantic and fluid grid framework on top of LESS

LESS-Neat is a fluid grid framework built with the aim of being easy enough to use out of the box and flexible enough to customize down the road.

## Using LESS-Neat

If you are planning to override the default grid settings (12 columns, and etc.), it is easier to create a copy of an existing [_variables.less](/stylesheets/core/_variables.less) file for that purpose. Make sure to replace existing import to your version of variables in [_less-neat.less](/stylesheets/_less-neat.less):

```less
@import "core/_local_variables";
```

See the [demo page](http://less-neat.azurewebsites.net/demo/index.html) for a full list of features.

Let's walk through a simple example. Include the `outer-container` mixin in the topmost container (to which the `max-width` setting will be applied):

```less
.container {
  .outer-container();
}
```

Then use `span-columns` on any element to specify the number of columns it should span:

```less
.element {
  .span-columns(6);
}
```

If the element's parent isn't the top-most container, you need to add the number of columns of the parent element to keep the right proportions:

```less
.container {
  .outer-container();

  .parent-element {
    .span-columns(8);

    .element {
      .span-columns(6, 8);
    }
  }
}
```

To make your layout responsive, use the LESS built-in nested media queries functionality to modify both the grid and the layout:

```less
.container {
  .span-columns(4);

  @media (min-width: 768px) {
    .span-columns(2);
  }
}
```

## Credits

LESS-Neat is created and maintained by Alexandr Marinenko. The project is heavily inspired by amazing Sass framework [Bourbon Neat](http://neat.bourbon.io). Tweet your questions or suggestions to @jo_asakura.

## License

Copyright © 2015 Alexandr Marinenko. Neat is free software, and may be redistributed under the terms specified in the [license](LICENSE).
