# HTML & CSS Lab Exercises

## CSS Animation Examples (try to build similar effects by yourself!)
- [Animista](https://animista.net/)
- [Animate.css](https://animate.style/)

## Exercise 1: Basic HTML & CSS Formatting
Write a short text (3-5 paragraphs) and format it using HTML & CSS.  

### HTML Elements to Use
- `<h1>` to `<h6>` – Headings  
- `<p>` – Paragraphs  
- `<div>` – Grouping content  
- `<a>` – Links  

### CSS Styling Tasks
- Use an external font (Google Fonts or a font file).  
- Change the text colour and size.  
- Add a background colour to a `<div>`.  
- Style links (`<a>`), including:  
  - Default appearance  
  - Hover state (change colour when the cursor hovers over it)  

### Resources
- [CSS Text Styling](https://www.w3schools.com/css/css_text.asp)  
- [Adding Fonts in CSS](https://www.w3schools.com/css/css3_fonts.asp)  

## Exercise 2: CSS Box Model & Hover States
Apply different CSS box model properties and hover effects to style your text and layout.  

### Box Model Styling Tasks
- Add a **border** to a `<div>` and adjust its thickness and style.  
- Apply **padding** inside an element to control spacing.  
- Use **margin** to space elements apart.  
- Set a **specific width and height** for a box and make it responsive.  

### Hover Styling Tasks
- Change the **background colour** of a `<div>` on hover.  
- Add a **box-shadow** when an element is hovered over.  
- Make links **underline only when hovered**.  

### Resources
- [CSS Box Model](https://www.w3schools.com/css/css_boxmodel.asp)  
- [CSS Hover Effects](https://www.w3schools.com/cssref/sel_hover.asp)  

## Exercise 3: Make It Move — CSS Transitions & Transforms
### Part A — Smooth Out Your Hovers (Transitions)

Hover over the boxes you styled in Exercise 2. Notice how the colour and shadow jump instantly? Let’s fix that.
- Add a transition to your `<div>` so the background colour changes smoothly on hover.
- Add a second transition so the box-shadow changes at a different speed from the colour.
- Try three different easing values on the same element (linear, ease-in, ease-out). Which one feels most natural?
- Add a delay to one transition. How long can the delay be before it feels broken?

```css
.box {
  transition: background-color 0.4s ease, box-shadow 1s ease-out;
}
```

### Part B — Transform Playground

Give each of your boxes or paragraphs its own personality on hover. Use at least three of these:

- Lift (move it up a little): `transform: translateY(-10px);`
- Grow (make it bigger): `transform: scale(1.1);`
- Tilt (rotate it): `transform: rotate(-3deg);`
- Lean (skew it): `transform: skewX(10deg);`
- Combo (use two at once): `transform: translateY(-10px) rotate(2deg);`

Remember to add transform to your transition, or the movement will jump instead of glide:
```css
.box {
  transition: transform 0.3s ease-out;
}
.box:hover {
  transform: translateY(-10px) rotate(2deg);
}
```
Tip: Give each box its own class (.box-1, .box-2…) so each one can move differently. That’s a quick class selector review from Week 2.

Part C — Playful Challenge (choose one)

Option 1: The Shy Button
Add a `<button>` to your page that runs away when the cursor gets close.

```css
button {
  transition: transform 0.2s ease-out;
}
button:hover {
  transform: translate(150px, -40px) rotate(20deg);
}
```
Can you still click it? Try different distances and speeds to make it more (or less) annoying.

Option 2: The Flip Card 🃏
Make a card that flips over in 3D to show a hidden message on the back. This uses the parent/child relationship from Week 2: the parent sets the perspective, and the child does the flipping.

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
  perspective: 600px;              /* parent sets the 3D space */
}
.card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s ease-in-out;
  transform-style: preserve-3d;
}
.card:hover .card-inner {
  transform: rotateY(180deg);      /* child flips */
}
.card-front, .card-back {
  position: absolute;
  inset: 0;
  backface-visibility: hidden;     /* hide the side facing away */
}
.card-back {
  transform: rotateY(180deg);
}
```
Give the front and back different background colours, padding and borders so you can see which side is showing. That’s a box model review from Exercise 2. Then try changing perspective to 200px and then 2000px. What changes?


## Exercise 4: Responsive Design Basics
Make your Exercise 2 webpage responsive.  

### Responsive Styling Tasks
- Use media queries to adjust text size on smaller screens.  
- Make images scale properly using `max-width: 100%`.  
- Ensure the text does not overflow on small screens.  
- Stack content vertically on mobile but keep it horizontal on larger screens.  

### Resources
- [CSS Responsive Design Basics](https://www.w3schools.com/css/css_rwd_intro.asp)  
