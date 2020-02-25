# W4 D1

* [teacher notes](https://github.com/Eric-Lombardo/w4d1_2020-02-24)

## AJAX
* its not a programming language but tisa  technique for accessing web servers from a webpage.
* stands for ASYNCHRONOUS JAVASCRIPT AND XML

## semantic HTML
* sematic html like header, main, footer, strong is good for: 
1. accessibility
2. web crawlers

## block vs inline block elements
* `<div>` is a block element
* `<span>` is a inline block element
  * `<strong>`
  * `<emphasis>`
  * `<images>`
  * `<a>` 
  * are all examples of inline blocks

## HTML 5
* headers/footers/articles are considered block level elements

## CSS normalize
* to reset the browser's default styles use npm normalize by linking the normalize stylesheet in the head of your html document

## content-box vs border-box
* by default its set to content-box which doesnt inlcude border in the final size of an element
* borderbox will include the border in the final size of the element by shrinking the content accordingly

## CSS
* the order of styles makes a difference.
* the lower one will take precendence

## CSS selectors
* there is a precendence for the pwoer of css slectors
  1. inline style attributes (1000 points)
  2. ids
  3. classes
* use commas between CSS selectors to just add 1 or more selectors to share the same styles. ex:
```CSS
h1, article {
  // some styles
}
```
* having a space between selectors scans for all descendents that match
* having a `>` selects ONLY direct descendents
* having a `*` astericks is for any element ex:
```css
nav > * {
  // some styles
}
```

## helper apps
* [lorem ipsum](https://loremipsum.io/ultimate-list-of-lorem-ipsum-generators/	)
* [placehold.it](https://place-hold.it/)
* [place kitten](https://placekitten.com/)

## float
* float will allow paragraphs to flow better around images for example
* default is inlien block and looks liek this
```js
|-----------|
| image     |
|-----------| textetextetxttextetxe
```
* but with float it can look liek this:
```js
|-----------| texttexttexttexttext
| image     | textetxtexttxetttextt
|-----------| textetextetxttextetxe
```
* if you want some text to ignore the floats you can use style
  1. `clear: both`
  2. `clear: left`
  2. `clear: right`

## position
* the position style will take that element out of the flow from the rest.
* pair it with `top: 0` or `bottom: 0` to say where it should stay fixed
* click [here](https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/) to elarn more about relative/absoloute/fixed

## flexbox
* to use flexbox: `display: flex`
* flexbox doesnt care if the elements are block or inline beacuase this will place all children in a row/column when using flexbox
* MAIN AXIS: is always controlled with `justify-content`
* CROSS AXIS: is always controlled with `align-items`
* in flexbox when using `auto` it will take all the space for ex:
  * `margin-left: auto` wil move that element all the way to the right

## padding vs margin
* `padding` will contain the background color and `margin` will not
* if you want to separete 2 elemens with space in the middle use `margin`

## IDs vs classes
* an elemtn can only have 1 id but many classes
* classes imply stylistic or behavioral properties about an element
* general rule: classes shoudl be used way more frequently than ids
* ids can be used to reference them from URLs ex:
  * `www.domain.com#comments` will jump to the element with the id `comments`
* suing ids is more performant and browsers can work faster because it only has 1 element to target and can stop searching ince it finds that 1 instance
* use neither unless neccessary unless it gets to verbose to target ex: `div > p > div > a`
* information that is reusable shoudl be stored in a class and info that is completley unique should be kept in an id

## em and rem
* em: element's original font size
* rem: root element's font size

## @media
* sue this for styles that change for different circumstances like adjusting styles for different screen sizes (desktop and mobile)
