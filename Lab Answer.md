# HTML & CSS Lab Exercises – Answers

Each exercise builds on the previous one. Only new or changed code is shown after Exercise 1.

## Exercise 1: Basic HTML & CSS Formatting

### HTML
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Page</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="intro">
    <h1>Motion on the Web</h1>
    <p>Websites used to be still, like pages in a book. Today, buttons lift and cards flip.</p>
  </div>

  <h2>Why does movement matter?</h2>
  <p>Movement guides attention. When something moves, our eyes follow it.</p>
  <p>In CSS, we can create movement without any JavaScript.</p>
  <p>Learn more on <a href="https://developer.mozilla.org">MDN Web Docs</a>.</p>
</body>
</html>
```

### CSS
```css
body {
  font-family: 'Inter', Arial, sans-serif;
  font-size: 18px;
  color: #222222;
}

h1 {
  font-size: 40px;
  color: #3a0ca3;
}

.intro {
  background-color: #e8e3ff;
}

a {
  color: #3a0ca3;
}

a:hover {
  color: #f72585;
}
```

## Exercise 2: CSS Box Model & Hover States

### HTML (add below your paragraphs)
```html
<div class="box-row">
  <div class="box">Box 1</div>
  <div class="box">Box 2</div>
  <div class="box">Box 3</div>
</div>
```

### CSS
```css
/* Box model */
.intro {
  padding: 20px;                 /* space inside */
  margin-bottom: 30px;           /* space outside */
}

.box-row {
  display: flex;
  gap: 20px;
}

.box {
  width: 300px;
  max-width: 100%;               /* responsive: never wider than the screen */
  height: 150px;
  padding: 20px;
  border: 3px dashed #3a0ca3;
}

/* Hover states */
.box:hover {
  background-color: #ffd6ec;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

a {
  text-decoration: none;
}

a:hover {
  text-decoration: underline;    /* underline only on hover */
}
```

## Exercise 3: Make It Move – CSS Transitions & Transforms

### Part A – Smooth Out Your Hovers
```css
.box {
  /* colour: 0.4s | shadow: 1s with 0.2s delay */
  transition: background-color 0.4s ease, box-shadow 1s ease-out 0.2s;
}

/* Try swapping the easing: linear, ease-in, ease-out */
```

### Part B – Transform Playground

Give each box its own class:
```html
<div class="box box-1">Lift</div>
<div class="box box-2">Grow</div>
<div class="box box-3">Tilt</div>
```

```css
.box {
  /* Add transform to the SAME transition line.
     A second "transition" line would replace the first! */
  transition: background-color 0.4s ease, box-shadow 1s ease-out 0.2s, transform 0.3s ease-out;
}

.box-1:hover { transform: translateY(-10px); }
.box-2:hover { transform: scale(1.1); }
.box-3:hover { transform: translateY(-10px) rotate(2deg); }
```

### Part C – Option 1: The Shy Button
```html
<button>Click me!</button>
```

```css
button {
  transition: transform 0.2s ease-out;
}

button:hover {
  transform: translate(150px, -40px) rotate(20deg);
}
```

### Part C – Option 2: The Flip Card
```html
<div class="card">
  <div class="card-inner">
    <div class="card-front">Hover me</div>
    <div class="card-back">Surprise! 🎉</div>
  </div>
</div>
```

```css
.card {
  width: 250px;
  height: 160px;
  perspective: 600px;
}

.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s ease-in-out;
  transform-style: preserve-3d;
}

.card:hover .card-inner {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  position: absolute;
  inset: 0;
  backface-visibility: hidden;
  padding: 20px;
  border: 3px solid #3a0ca3;
}

.card-front {
  background-color: #e8e3ff;
}

.card-back {
  background-color: #3a0ca3;
  color: #ffffff;
  transform: rotateY(180deg);
}
```

## Exercise 4: Responsive Design Basics

### HTML (add an image)
```html
<img src="https://picsum.photos/1200/500" alt="A landscape photo">
```

### CSS
```css
/* Images scale to fit */
img {
  max-width: 100%;
  height: auto;
}

/* Long words wrap instead of overflowing */
p, h1, h2 {
  overflow-wrap: break-word;
}

/* Small screens */
@media (max-width: 600px) {
  body {
    font-size: 16px;
  }

  h1 {
    font-size: 28px;
  }

  /* Stack vertically on mobile (horizontal on larger screens) */
  .box-row {
    flex-direction: column;
  }

  .box {
    width: 100%;
  }
}
```
