# scaleLinearly()

A Sass/Stylus mixin enabling swift, maintainable and performant implementation of responsive design mockups.

## Installation

1. Copy the source code of the [Sass](https://github.com/maninak/scaleLinearly/blob/master/scaleLinearly-demo-sass/src/mixins/scaleLinearlyBase.scss) or the [Stylus](https://github.com/maninak/scaleLinearly/blob/master/scaleLinearly-demo-stylus/src/mixins/scaleLinearlyBase.styl) implementation
2. Paste it in a file in your repo
3. Import the `scaleLinearlyBase()` mixin in a stylesheet where you want to use it.
4. Preferably wrap it with a new mixin called `scale()` initialised with your defaults, as shown in the example below
5. That's it, you're ready to scale!

## Usage example

In a global, or shared (one per UI module) file, import `scaleLinearlyBase()` and wrap it with the defaults of the mockups you're given by your designer. Here I assume I was given a small mockup of 320px width and a large mockup of 1440px width.

>_I usually try to keep most of my global or shared "magic" CSS values organised in separate files like `lengths.scss` and `colors.scss`, but for simplicity's sake I'll just inlined them in this example._

```scss
/* homepage.scss */

@import 'path/to/global/mixins/scaleLinearlyBase.scss';

$lengths-mockup-viewport-min: 320px;
$lengths-mockup-viewport-max: 1440px;

@mixin scale(
  $property,
  $lengthAtViewportSm,
  $lengthAtViewportLg,
  $capMaximum: true,
  $useImportant: false
) {
  @include scaleLinearlyBase(
    $property,
    $lengthAtViewportSm,
    $lengthAtViewportLg,
    $capMaximum,
    $useImportant,
    $lengths-mockup-viewport-min,
    $lengths-mockup-viewport-max,
  );
}
```

Then in your Sass stylesheet:

```scss
/* hero.scss */

@import '../homepage.scss';

h1 {
  @include scale(font-size, 26px, 48px);
}
```

Or with Stylus:

```stylus
/* hero.styl */

@import '../homepage.styl';

h1 {
  scale(font-size, 26px, 48px);
}

```

## Demo

I've setup a minimal [live demo app](https://todo-fix-link) implemented with the help of `scaleLinearly()`.<br>Resize your browser window and watch the design flow in response.

You can also check-out the [source code](https://github.com/maninak/scaleLinearly/tree/master/scaleLinearly-demo-sass) of the demo app.

## I wanna know more

Check the the announcement [article on Medium](https://todo-fix-link) for all the juicy details.

## NPM module

There's no NPM module to import at this time, since I prefer to keep it a simple copypasta file.

If enough people think it would be useful, sure, I'd be happy to! Just open an [issue](https://github.com/maninak/scaleLinearly/issues).

## Licence

Distributed under the MIT license. See [`LICENSE.md`](./LICENCE.md) for more information.

## Contributing

1. Fork it (<https://github.com/maninak/scaleLinearly/fork>)
2. Create your feature branch (`git checkout -b feature/fooBar`)
3. Commit your changes (`git commit -am 'Add some fooBar'`)
4. Push to the branch (`git push origin feature/fooBar`)
5. Create a new Pull Request