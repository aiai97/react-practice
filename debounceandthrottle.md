# Debounce and Throttle

**Debounce** waits until events stop for a certain time before running the function.  
**Throttle** limits how many times a function can run within a time period.  
Debounce is useful for fast typing, while throttle is useful for fast clicks or hot APIs.  
a single function < a single component / lib . the best is the component

I like the code in https://medium.com/@ignatovich.dm/debouncing-and-throttling-in-react-whats-the-difference-and-how-to-implement-them-0a500b649235
This one is good too. https://medium.com/@gabrielmickey28/using-debounce-with-react-components-f988c28f52c1

```js
function debounce(fn, wait) {
  let timer;

  return (...args) => {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), wait);
  };
}

function throttle(fn, limit) {
  let lastTime = 0;

  return (...args) => {
    const now = Date.now();

    if (now - lastTime >= limit) {
      lastTime = now;
      fn(...args);
    }
  };
}
```
