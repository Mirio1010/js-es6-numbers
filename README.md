# Number Counter Animation

## Overview
This function creates a smooth counting animation that increments from 0 to a target number, displaying the progress in real-time on a webpage element. 

Feel free to use this function for future projects! 



## Live Demo
👉 View the project here: **[NumbersAnimation](https://mirio1010.github.io/js-es6-numbers/)**

## How It Works

### 1. **Get the Target Value**
```javascript
const value = parseInt(element.dataset.value);
```
Extracts the final number from the element's `data-value` attribute and converts it to an integer.

### 2. **Calculate Increment Step**
```javascript
const increment = Math.ceil(value / 1000);
```
Determines how much to add each frame. The target value is divided by 1000, then rounded up. This means:
- Smaller numbers increment by at least 1
- Larger numbers increment faster (e.g., 5000 would increment by 5 each time)

### 3. **Initialize Counter**
```javascript
let initialValue = 0;
```
Starts the counter at zero.

### 4. **Animation Loop**
```javascript
const increaseCount = setInterval(() => {
  initialValue += increment;
  // ... update logic
}, 1);
```
Runs every 1 millisecond, continuously adding the increment value.

### 5. **Stop Condition**
```javascript
if (initialValue > value) {
    element.textContent = `${value}+`;
    clearInterval(increaseCount);
    return;
}
```
When the counter exceeds the target:
- Sets the display to the exact target value with a "+" suffix
- Stops the interval
- Exits the function

### 6. **Display Update**
```javascript
element.textContent = `${initialValue}+`;
```
Updates the element's text content with the current count plus a "+" symbol.

## Usage Example
```html
<span class="counter" data-value="5000"></span>

<script>
  const counter = document.querySelector('.counter');
  updateCount(counter);
</script>
```

This would animate from 0+ to 5000+ over approximately 1 second (1000 frames × 1ms).

## Notes
- Animation duration is roughly 1 second regardless of the target number
- The "+" suffix appears throughout the entire animation
- Larger numbers will appear to count faster due to larger increments
