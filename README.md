# Sass KickStarter `sks`
## _The Ultimate Sass bootstraping tool_

[![N|Solid](https://use.vormia.com/github/img/sass-less-1.png)](https://sass-lang.com/documentation/)

![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)

Sass is a stylesheet language that’s compiled to CSS. It allows you to use variables, nested rules, mixins, functions, and more, all with a fully CSS-compatible syntax. Sass helps keep large stylesheets well-organized and makes it easy to share design within and across projects.

This project consist of basic sass files for kickstarting a project. Tools like color, margin & padding, important(required) and many more.

- Easy to use
- Pre-compiled style.min.css
- Download and start to use

## Features

- Pre defined colors codes, ready to use ( You can add yours with ease)
- Pre defined Margin, Padding classes 
- Pre defiend Colors classes for font and background
- Pre defined shadow classes useful in html boxes/cards
- Pre defiend Font-size and Width
- Important * and error class

If you are not familiar with SASS/LESS kindly get started by reading the official [SASS DOCUMENTATION](https://sass-lang.com/documentation/) or other online tutorials

> Sass is a stylesheet language that’s compiled to CSS.
> Sass is not a new language
> Our kickstarter code is CSS written in SASS format which make it easy to read and modify

## INSTALLLATION

To get started simply download this repo `main branch` or **folk** and add it to your project.
Then link the `` *style.min.css*`` inside your project `<head>` tags.
```
<head>
<link rel="stylesheet" href=".../style.min.css?v=1.00">
</head>
```
Remember: *you must have a sass compiler in your editor* **if you are using VSCODE** then you can install this package [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=glenn2223.live-sass)

Once everything is ok, you can get started:

#### NOTE

`IT IS IMPORTANT TO INCLUDE` **_incl/incl** and **_incl/func** files after **_incl/_colors** 

## 1: COLOR
The color codes are located in `../style/_incl/_colors.scss` file.
To use the color inside you main sass file; simple include the **_colors.scss** file by using `sass import` mixin `@import "_incl/colors";`  

Once included you can now use `color(defined_key_name);`

_example_:
```
color: color(main-red);
``` 

```
background-color: color(main-red);
```
where: `color` is a mixin declared inside **_colors.scss** file `color($color_name, $map: $colors)`

**optional** you can use `sks-color` - `defined_key_name` (`sks-color-main-red`) as your class name inside a ``html element`` 

_example 1_: using `sks-color-main-red`
```
<span class="text-bold sks-color-main-red">This Text is Red</span>
```
_example 2_: using `sks-bg-color-main-red` for background color.
```
<div class="boxed-zone sks-bg-color-main-red">
    <p> This area has red blackground </p>
</div>
```

**above code** (_class names_) **are auto generated from colors** `key-names` **generated using mixin** `@mixin colorsCode($map: $colors)`

Note: **_about `color($color_name, $map: $colors)` mixin_**
- takes two arguments `color name` and `array of colors` called ***map*** is sass.

To add your own colors simple add new key inside `$colors: ();` array found in **_colors.scss** file.
*example*
```
$colors: (
	main-red: #bb2d3b,
	main-blue: #41b6ff,
	...
	//My own colors
	mr-white: #ffffff,
	men-in-black: #000000
);
```

## 2:MARGIN & PADDING

Inside `../style/_incl/_func.scss` file mixins `marginSet()` and `paddingSet()` are used to auto generate default _margin_ and _padding_ classes.

- to use marging classes simply call mixin `@include marginSet();` and `@include paddingSet();` for padding classes

**Note:** 
`t` : stands for **top**
`r` : stands for **right**
`b` : stands for **bottom**
`l` : stands for **left**

The dimension used are `rem` and `percentage`: _sks-rem-m_ when applying **_xx rem_** and _sks-m_ when using **_xx %_** percentage.

**_example_**:

`sks-rem-mt-5` = `margin-top: 5rem`
`sks-mt-5` = `padding-top: 5%`
```
<p class="p-text sks-rem-ml-5"> This paragraph has 5rem left margin</p>
```
`sks-rem-pt-5` = `padding-top: 5rem`
`sks-pt-5` = `padding-top: 5%`

**If you wish to customize these class name or switch rem with px, change `paddingSet` or `marginSet` mixin inside `_func.scss`**

**_minimum size_** `1rem and 1%` _**maximum size** is_ `10rem and 50%`

## 3:WIDTH

Classes for **width** are generated using mixin `widthSize()` inside `../style/_incl/_func.scss` file.
```
@mixin widthSize() {
	// loop from 10 to 100 in 10
	@for $i from 1 through 20 {
		$size: $i * 5;
		.sks-width-#{$size} {
			width: #{$size}%;
		}
	}
}
```
**_minimum size_** `10%` _**maximum size** is_ `100%`
to use width simply call mixin `@include widthSize();`

`sks-width-10` = `width: 10%`
```
<div class="boxed-zone sks-bg-color-main-red sks-width-50">
    <!-- This box has 50% width -->
    <p> This area has red blackground</p>
</div>
```

## 4:SHADOW

To apply shadow in you css code block simple add `@include shadow` or other shadow mixin offered.
**_example_**
```
div.single-listing-details {
	color: color(white);
	// Background
	.main-list,
	.sub-list {
		background-color: color(main-red);
	}
	//Shadow
	@include shadowRight();
}
```
`SHADOW CAN BE ADDED IN A CSS BLOCK AND DOES NOT HAVE GENERATED CLASS`

**HOWEVER YOU CAN GENERATE YOURS**
```
.my-custom-top-shadow {
	@include shadowTop();
}
```
when compiled the above code will generate class `my-custom-top-shadow` which can be used in **_html element_**

```
<div class="article-block my-custom-top-shadow">This section has shadow on top</div>
```

**Available Mixins for Shadow**

`shadowTop()` for -shadow on top of element/block
`shadowRight()` for -shadow on right of element/block
`shadowBottom()` for -shadow on bottom of element/block
`shadowLeft()` for -shadow on left of element/block
---------------------------
`shadow()` for -shadow around of element/block
`shadow1()` for -shadow at the `bottom` while floating `right`
`shadow2()` for -shadow at the `bottom` while floating `left`
---------------------------

To **learn** more about [`mixing`](https://sass-lang.com/documentation/at-rules/mixin) and [`function`](https://sass-lang.com/documentation/at-rules/function) revisit `sass documentation`

## 5:FONT SIZE

To utilize font-size classes remember to add `@include fontSize();` at the top of you `sass` file `../style/_incl/_func.scss`

Font size is in `pixels` starting from `10px` to `20px` as the **_maximum_**

`sks-font-15` = css code `font-size: 15px;`

_example 1_: using `sks-font-13`
```
<span class="sks-font-13">This Text Font Size 13px</span>
```

## 6:REQUIRED & ERROR

Required class `.reqired` should be added in <label>.
eg: `<label class="text-lable sks-required">Email</label>` this will add `<sub>*</sub>` after text **Email**.
- The `*` will be in **_subscript_** and **red**.

`THIS ONLY WORK WITH <LABEL> HTML ELEMENT`

To utilize `sks-required` and `sks-error` remember to add `@include required();` at the top of you `sass` file `../style/_incl/_func.scss`

```
<span class="sks-error">Error message in red</span>
```
- The error message will be in `red`,`itallic`,`12px`

`THIS ONLY WORK WITH <SPAN> & <P> HTML ELEMENT`

## BOOTSTRAP OVERWRITE

##### Sass KickStater also allow you to overwrite `BOOTSTRAP` classes.

* call `@include boostrap_bg();` to overwrite default `bg-primary`,`bg-success` etc with your own color codes
* call `@include boostrap_btn();` to overwrite default `btn-primary`,`btn-success` etc with your own color codes

`NB` this will only replace `color codes` with your defined  ***color_key_name*** `background-color: color(success)`;

## Development

Want to contribute? Great!

`Folk` do your improvement and documment changes/additions.
`Merge` request merge with the main project.

## License

MIT License

**Free Software, Hell Yeah!**

[![N|Solid](https://use.vormia.com/github/img/twitter-1.png)](https://twitter.com/joshminga) [`@joshlminga`](https://twitter.com/joshminga)
[![N|Solid](https://use.vormia.com/github/img/github.png)](https://github.com/joshlminga) [`@joshlminga`](https://github.com/joshlminga)
![N|Solid](https://use.vormia.com/github/img/gmail.png)  joshlminga@gmail.com

[//]: # (This is a personal fun side-project - www.vormia.com)

