## Project Summary

In this project, we will learn how to create a side drawer that appears when clicking on a menu button. Since this module only covers HTML & CSS, I will show you a way to create a drawer with only HTML & CSS. There are other ways of creating a drawer using JavaScript as well.

## Steps

After each step, use git to add and commit the changes you have made to the project!

### Step 1.

Fork this repository to create your own copy.

### Step 2.

Make `index.html` and `style.css` files. Use HTML:5 snippet and link the style sheet to the html. We will also want to link the `reset.css` file that is included in the repo. Make sure to link `reset.css` before `style.css` so that the reset styled are applied first.

In this step, let's also go ahead and change the title for our website. You can make it whatever you want.

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Keyframes</title>
  </head>
  <body></body>
</html>
```

</details>

## Typewriter animation

The first Animation we are going to create is a typewriter effect. We want it to look like someone is typing a message across the screen like in the gif below.

![typewriter animation](https://github.com/pushcode-dev/html-css-keyframes-guided/blob/master/typwriter_animation.gif)

### Step 3

First, we will want to create a wrapper element that the message will be contained in. So, let's create a class called `.typewriter-wrapper`. We will give this class a display flex, and make it so the content (child elemenet) is centered on the row (hint: `justify-content` can be used to center elements in a display flex container).

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Keyframes</title>
  </head>
  <body>
    <div class="typewriter-wrapper"></div>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
.typewriter-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 48px;
}
```

</details>

### Step 4

Next we will create the message that we want to appear. You can use whatever message you want, but I will be using the text `Welcome to PushCode.dev`. We want this text to live within an element that we can target and give styles and animations to, so let's create a `div` with class `typewriter` and inside an `h1` with the text you choose.

We will also want to give the `h1` some styles to make our text look the way we want. You can follow along with what I am doing, or you can do what you want and get creative with it!

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Keyframes</title>
  </head>
  <body>
    <div class="typewriter-wrapper">
      <div class="typewriter">
        <h1>Welcome to PushCode.dev</h1>
      </div>
    </div>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
.typewriter-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 48px;
}

.typewriter h1 {
  font-size: 24px;
  letter-spacing: 0.15em;
}
```

</details>

### Step 5

In this step we will create a "cursor" by giving a `border-right` to our `h1`.

<details>
<summary>style.css</summary>

```css
.typewriter-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 48px;
}

.typewriter h1 {
  font-size: 24px;
  letter-spacing: 0.15em;
  border-right: 2px solid #5dc03e;
}
```

</details>

### Step 6

In this step we will make our cursor blink! Time to animate things!

We want to create a `@keyframe` to determine what properties we want to change and when. Let's create a `@keyframe` and call is `blink-cursor`. This keyfram will be applied to our `h1` and we want it to control the animation of our "cursor" which is the `border-right` for our `h1`. In the `blink-cursor` keyframe, we want to change the color of the border from transparent to it's original color. We will start and end the animation with the `border-color` being transparent, and at the halfway point of the animation we will want the `border-color` to show.

```css
@keyframes blink-cursor {
  0%,
  100% {
    border-color: transparent;
  }
  50% {
    border-color: #5dc03e;
  }
}
```

We then want to apply this animation to our `h1` and tell it how long we want the animtion to take, give it a timing-function and an iteration count. We want this animation to happen over and over again and never stop, so the iteration count will be `infinite`.

```css
.typewriter h1 {
  font-size: 24px;
  letter-spacing: 0.15em;
  border-right: 2px solid #5dc03e;
  animation: blink-cursor;
  animation-duration: 1s;
  animation-timing-function: steps(1, end);
  animation-iteration-count: infinite;
}
```

The `animation-timing-function` can be a little confusing at first. And here we are using the `steps` function which can also be confusing to understand. I'm not going to go into, because it is not necessary for you to fully understand at this point, and I want you to be able to focus on the other parts of animations right now. You can take that part out, and your animation will still work, but the cursor will fade in and out instead of blink. Give it a try to see what I mean.

We can also use shorthand and apply all of those styled to the `animation` property.

```css
.typewriter h1 {
  font-size: 24px;
  letter-spacing: 0.15em;
  border-right: 2px solid #5dc03e;
  animation: blink-cursor 1s steps(1, end) infinite;
}
```

<details > 
<summary > style.css</summary >

```css
.typewriter-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 48px;
}

.typewriter h1 {
  font-size: 24px;
  letter-spacing: 0.15em;
  border-right: 2px solid #5dc03e;
  animation: blink-cursor 1s steps(1, end) infinite;
}

@keyframes blink-cursor {
  0%,
  100% {
    border-color: transparent;
  }
  50% {
    border-color: #5dc03e;
  }
}
```

</details>

### Step 7

In this step we are going to animate the text so it looks like it is being typed. Let's first create the keyframe and think about what we want to have happen here. So at first we don't want the text to appear, and then we want it to look like it is appearing letter by letter. How could we make that happen? Think through it for a minute. Even if you don't have a clue, it's still good to think through it.

If the `width` of the `h1` is `0`, and the `overflow` for the `h1` is hidden, what would happen? We wouldn't see anything. And then if the `width` was `100%` and the `overflow` is `hidden`, we would see all of the text.

So we know we want the overflow to be hidden. let's go ahead and add `overflow: hidden;` to our `h1`.

But what happens if the width is 50%? Give it a try. Add `width: 50%;` to your `h1`.

The words wrap! That's not the effect we want. We can add `white-space: nowrap;` to make sure the words all stay on the same line. Add that to the `h1` and see what happens.

Awesome! Now it looks like only part of the test is visible, and it's all in one line. We are on the right track! We will have the keyframe animation control the width of the `h1`, so we can go ahead and remove that property for now.

Let's create the `keyframe`. Add the following to your css file.

```css
@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}
```

This `typing` keyframe is saying that we want to start the animation with a `width` of `0` and end it with a `width` of `100%`. We could also write this like:

```css
@keyframes typing {
  0% {
    width: 0;
  }
  100% {
    width: 100%;
  }
}
```

We want to apply this animation to our `h1` and give it a duration, timing-function, a delay (if we want), and an interval (we only want this to happen 1 time, so we can actually leave off the interval).

But how do we do this if we already have an animation applied to our `h1`, since we have the `blink-cursor` also applied to the `h1`?

like this:

```css
animation: typing 3.5s steps(50, end) 2s, blink-cursor 0.75s step-end infinite;
```

We can apply multiple animations by separating them with a comma. For the `typing` animation, we are saying we want to animation to take 3.5 seconds, have 50 steps in the timing-function, have a 2 second delat and since we didn't specify an interval, it will only happen 1 time. Remember, I don't want you to focus too much on the steps function. The number of steps should be double the number of characters in your text that you want "typed" out, including white spaces.

Now give it a try! You might notice that the text is visible at first, and then disappears and the animation happens. That is because of the animation-delay. You can add the following to the `h1` to fix the problem.

```css
animation-fill-mode: both;
```

And now we have a typing animation! Super cool!

One last thing. Add `margin: 0 auto;` to your `h1` to always have the content centered horizontally.

<details > 
<summary > style.css</summary >

```css
.typewriter-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 48px;
}

.typewriter h1 {
  font-size: 24px;
  letter-spacing: 0.15em;
  border-right: 2px solid #5dc03e;
  animation: typing 3.5s steps(50, end) 2s, blink-cursor 0.75s step-end infinite;
  animation-fill-mode: both;
  overflow: hidden;
  white-space: nowrap;
  margin: 0 auto;
}

@keyframes blink-cursor {
  0%,
  100% {
    border-color: transparent;
  }
  50% {
    border-color: #5dc03e;
  }
}
```

</details>

### Moving Ball Animation

Here's another fun animation that you can make. We won't go through all of the steps, just add the html and css to your files and you can see the animation. Then, read through the code until you understand how it is working.

```html
<div class="balls-container">
  <div class="ball"></div>
  <div class="ball"></div>
  <div class="ball"></div>
  <div class="ball"></div>
  <div class="ball"></div>
  <div class="ball"></div>
  <div class="ball"></div>
</div>
```

```css
.balls-container {
  margin: 0 auto;
  background: black;
  padding: 80px;
}

.ball {
  width: 10px;
  height: 10px;
  margin: 10px auto;
  border-radius: 50px;
}

.ball:nth-child(1) {
  background: #ffffff;
  animation: right 1s infinite ease-in-out;
}

.ball:nth-child(2) {
  background: #ffffff;
  animation: left 1.1s infinite ease-in-out;
}

.ball:nth-child(3) {
  background: #ffffff;
  animation: right 1.05s infinite ease-in-out;
}

.ball:nth-child(4) {
  background: #ffffff;
  animation: left 1.15s infinite ease-in-out;
}

.ball:nth-child(5) {
  background: #ffffff;
  animation: right 1.1s infinite ease-in-out;
}

.ball:nth-child(6) {
  background: #ffffff;
  animation: left 1.05s infinite ease-in-out;
}

.ball:nth-child(7) {
  background: #ffffff;
  animation: right 1s infinite ease-in-out;
}

@keyframes right {
  0% {
    transform: translate(-15px);
  }
  50% {
    transform: translate(15px);
  }
  100% {
    transform: translate(-15px);
  }
}

@keyframes left {
  0% {
    transform: translate(15px);
  }
  50% {
    transform: translate(-15px);
  }
  100% {
    transform: translate(15px);
  }
}
}
```

## Solution

<details>
<summary>index.html</summary>

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="reset.css" />
    <link rel="stylesheet" href="style.css" />
    <title>Keyframes</title>
  </head>
  <body>
    <div class="typewriter-wrapper">
      <div class="typewriter">
        <h1>Welcome to PuschCode.dev</h1>
      </div>
    </div>
    <div class="balls-container">
      <div class="ball"></div>
      <div class="ball"></div>
      <div class="ball"></div>
      <div class="ball"></div>
      <div class="ball"></div>
      <div class="ball"></div>
      <div class="ball"></div>
    </div>
  </body>
</html>
```

</details>

<details>
<summary>style.css</summary>

```css
.typewriter-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 48px;
}

.typewriter h1 {
  font-size: 24px;
  letter-spacing: 0.15em;
  border-right: 2px solid #5dc03e;
  animation: typing 3.5s steps(50, end) 2s, blink-cursor 0.75s step-end infinite;
  animation-fill-mode: both;
  overflow: hidden;
  white-space: nowrap;
  margin: 0 auto;
}

.balls-container {
  margin: 0 auto;
  background: black;
  padding: 80px;
}

.ball {
  width: 10px;
  height: 10px;
  margin: 10px auto;
  border-radius: 50px;
}

.ball:nth-child(1) {
  background: #ffffff;
  animation: right 1s infinite ease-in-out;
}

.ball:nth-child(2) {
  background: #ffffff;
  animation: left 1.1s infinite ease-in-out;
}

.ball:nth-child(3) {
  background: #ffffff;
  animation: right 1.05s infinite ease-in-out;
}

.ball:nth-child(4) {
  background: #ffffff;
  animation: left 1.15s infinite ease-in-out;
}

.ball:nth-child(5) {
  background: #ffffff;
  animation: right 1.1s infinite ease-in-out;
}

.ball:nth-child(6) {
  background: #ffffff;
  animation: left 1.05s infinite ease-in-out;
}

.ball:nth-child(7) {
  background: #ffffff;
  animation: right 1s infinite ease-in-out;
}

@keyframes typing {
  from {
    width: 0;
  }
  to {
    width: 100%;
  }
}

@keyframes blink-cursor {
  0%,
  100% {
    border-color: transparent;
  }
  50% {
    border-color: #5dc03e;
  }
}

@keyframes right {
  0% {
    transform: translate(-15px);
  }
  50% {
    transform: translate(15px);
  }
  100% {
    transform: translate(-15px);
  }
}

@keyframes left {
  0% {
    transform: translate(15px);
  }
  50% {
    transform: translate(-15px);
  }
  100% {
    transform: translate(15px);
  }
}
```

</details>

## Submit project

Use git to add and commit any new changes, then push those changes to your reposiroty on github.

Make sure you submit this project in the `Guided project(s)` section for this unit. Just copy the url for your repository, paste it and click send!
