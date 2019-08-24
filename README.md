
# Center problem

### Center text

To simply center texts we can use `text-align: center`.

If it's not text, we can trun it to be `inline block element`. 

### Using `position: absolute`

```css
position: absolute;
top: 50%;
left: 50%;
transform: translate(-50%, -50%);
```

![image-20190821095014568](/Users/haida/Library/Application Support/typora-user-images/image-20190821095014568.png)



# Animation

### `@ keyname moveFunctionName`



# Media query

deskTop first —— `max-width`	if <=, apply `@media`

mobile first ——` min-width`	if >=, apply `@media`

# `inline` & `block` element

`block element`: like `<div>`，可以换行，从新的一行开始，高度宽度边距可控。

`inline element`: like `<span>`，都在一行上，高度宽度边距不可变。

# Text aglin(Typograph)

### To put 2 text one under the other

Display them as `block level elements`

`block level elements`

- Occupy the entire width that they have been available.
- Create `line breaks` after and before them.

### `display: inline-block`

It's `inline element`.

Always do this if we want to give some `padding` or some `height` to elements.

Advantage:

- It's treated as if it was text even if it was a button, so we can use `text-aglin: center`.

# Selector

### &: 

相当于this

### Attribute selector



# Lose style problem

### Break parent style while using 2 `float`s

```css
nav {
	margin: 30px;
	background-color: $color-primary;
}

.navigation {
	float: right;
}

.buttons {
  float: left;
}
```

Solution:

- Create a class called a `clearfix`

  ```css
  .clearfix::after {
    content: "";
    clear: both;
    display: table;
  }
  ```

  Integrate with `mixin`

  ```css
  @mixin clearfix {
      &::after {
          content: "";
          display: table;
          clear: both;
      }
  }
  
  //Invoke in parent element
  .row {
      @include clearfix;
  }
  ```

# BEM (Block Element Modifier)

![image-20190821101849655](/Users/haida/Library/Application Support/typora-user-images/image-20190821101849655.png)



# Flexbox

### In the same line(a flex container), to put one item to be the last

By using `order: 1`

### To move one item to another line

By using `flex-wrap: wrap`. It allows the flex item to wrap into a new line if they don't have enough space in the flex container. And how to make it move to another line automatically? By using `flex: 0 0 100%`. It means to make it with a larger width.

### How we control the space between the rows of the container

By using `align-contents`

# CSS grid layout

```
display: grid;
grid-template-row:
```





# Codepen short-cut

`.container>.item.item--$*6`



# Others

### position: relative/absolute` 

Set `absolute` to parent tag for 选取其最近一个具有`relative`性质的父级对象进行绝对定位

### 

### Adjacent selector

```scss
&_button + &_input {
       background-color: var(--color-grey-light-3);
   }
```

### If you want to make an icon to cover an input like this

![image-20190815145933778](/Users/haida/Library/Application Support/typora-user-images/image-20190815145933778.png)

```scss
margin-right: -3.5rem;
```

### set svg color

```scss
 fill: var(--color-grey-dark-3)
```

### change placeholder style 

```scss
        &::-webkit-input-placeholder {
            font-weight: 100;
            color: var(--color-grey-light-4);
        }
```



### choose all the direct children

```scss
    & > * {
        padding: 0 2rem;
        cursor: pointer;// when hover it the mouse will be a finger
    }
```

### Use `<main>` and `<figure>`

![image-20190819110207213](/Users/haida/Library/Application Support/typora-user-images/image-20190819110207213.png)

### `Flexbox` and `Block`

- elements side by side is to use flexbox

- the image should be displayed in block and that's about having a small space underneath an image, which happens when we leave it as an inline element. So an image should always be a `block` or `inline block` if we don't want that wide space.

  For example:

  If we use `flexbox`

  ![image-20190819111003271](/Users/haida/Library/Application Support/typora-user-images/image-20190819111003271.png)

  If we use `block`

### In responsive design, we should always use percentage for `width` and `height`

### `flex: 1` means this flex item should grow and occupy all the avilable space.

Like this:

![image-20190820064521328](/Users/haida/Library/Application Support/typora-user-images/image-20190820064521328.png)

but the element should only be the size of its content. So in this case the size of these stars. We don't want it to have all of this size. Imagine that we would have a hover effect on this and then all of this entire element here would be hoverd and would change the background. We only want the hypothetical hover effect to occur right here on this box where the stars actually are. So what we want is a way to create this space here without actually stretching out this entire element. So we can use `margin: auto`. It's a great trick. The same result but our element only occupies the space that it needs here. Like this:

![image-20190820065200908](/Users/haida/Library/Application Support/typora-user-images/image-20190820065200908.png)

### Set margin-bottom for paragraph

```scss
.paragraph:not(:last-of-type) {
    margin-bottom: 2rem;
}
```

`last-of-type` and `last-child`

### How to add a line for a block

![image-20190820181256018](/Users/haida/Library/Application Support/typora-user-images/image-20190820181256018.png)

```scss
    border-top: var(--line);
    border-bottom: var(--line);
```

### Align for the elements in a list

```scss
.list {
    list-style: none;
    margin: 3rem 0;
    padding: 3rem 0;

    display: flex;
    flex-wrap: wrap;
  
      &_item {
        flex: 0 0 50%;
    }
}
```

​	The effect only with `flex-wrap: wrap`:

![image-20190820181716743](/Users/haida/Library/Application Support/typora-user-images/image-20190820181716743.png)

And when we add `flex: 0 0 50%` for items

![image-20190820181803525](/Users/haida/Library/Application Support/typora-user-images/image-20190820181803525.png)

### How to add a svg icon in each list icon —— using `::before`

```scss
    &_item::before {
        content: "";
        display: inline-block;
        height: 2rem;
        width: 2rem;
        margin-right: .7rem;
        background-image: url(../img/chevron-thin-right.svg);
    }
```

But in this way, we can't fill color in a svg, so we use `mask`. It's a way for newer browers

```scss
        background-color: var(--color-primary);
        -webkit-mask-image: url(../img/chevron-thin-right.svg);
        -webkit-mask-size: cover;
```

`-webkit-mask-size: cover` means that the icon can cover the entire element

### Prevent img shrinking while adding a border

By using `box-sizing`.

We set `box-sizing` to all the elements to `border-box`. And what `border-box` does is that it includes the padding and the border into the width and height of the element. That's the general case, and here, in this situation, we want the border to be added on top of our height and the width, so we can set it to be the default.

`box-sizing: content-box` which is the dafault

### HTML5: `figure`

It's for pictures, images, text and descriptions

### Seprate figures into 2 blocks —— `margin-bottom`

![image-20190821041539972](/Users/haida/Library/Application Support/typora-user-images/image-20190821041539972.png)

### When we use `z-index` to set order, the heigher layer should add `position: relative`

### Button animation for a arrow `span`

Like this:

![image-20190821075006689](/Users/haida/Library/Application Support/typora-user-images/image-20190821075006689.png)

```html
            <button class="btn-inline">
              Show all
              <span>&rarr;</span>
            </button>
```



```scss
.btn-inline {
    transition: all .2s;

    & span {
        margin-left: 3px; // default style
        transition: all .2s; //To tell him that it's an animation.
    }

    &:hover {
        span {
            margin-left: 8px; //hover style
        }
    }

}
```



### While using `flex-firection: colum`

Maybe we will meet this situation:

![image-20190821075900936](/Users/haida/Library/Application Support/typora-user-images/image-20190821075900936.png)

Because the `aglin-items` set it to stretch.

### Span style

Since it's a `span`, it's an `inline` element. But we want it to be an `inline block`. So in order that we can use a `padding` in there.

### Add hover style for invisible class in btn

```scss
.btn {
   ...
    &_invisible {
        display: inline-block;
        padding: 2rem 0rem;
        position: absolute;
        height: 100%;
        width: 100%;
        left: 0;
        top: -100%;
        transition: all .2s
    }

    &:hover &_invisible{
            top: 0;
    }

}
```

### Different browser —— by using `@supports`

```scss
        //For older browsers
        background-image: url(../img/chevron-thin-right.svg);
        background-size: cover;

        //For newer browsers -- masks
        @supports (-webkit-mask-image: url()) or (mask-image: url()) {
            background-color: var(--color-primary);
            -webkit-mask-image: url(../img/chevron-thin-right.svg);
            -webkit-mask-size: cover;
            mask-image: url(../img/chevron-thin-right.svg);
            mask-size: cover;
        }
```

