project: https://github.com/WebDevSimplified/React-Flashcard-App/tree/master 

1) for app states
I use `useRef` to access the user's selected query conditions. 
This is a great tool to access dom values.

`categoryEl.current.value` → the selected category
`amountEl.current.value` → the number of questions

I use `useEffect` to fetch the data when the app first loads.
I need to get the categories first, so I can provide them for the user to choose from.

2) for flashcard component, 
To adapt to different screen sizes.

To recalculate and apply the appropriate height to the DOM element
whenever flashcard.question, flashcard.answer, or flashcard.options changes.

useEffect(setMaxHeight, [flashcard.question, flashcard.answer, flashcard.options])

To recalculate the height whenever the window is resized.

useEffect(() => {
  window.addEventListener('resize', setMaxHeight)
  return () => window.removeEventListener('resize', setMaxHeight)
}, [])

Keep `flip` and `height` as state because `flip` needs to control which face is showing or hiding.

I want each card to have a minimum height. If the question or answer is long, let the content determine the card's height. There could be very lengthy questions or answers.

Keep the height from the beginning because the card has a fixed height when it is initially loaded. But when the user changes the question or clicks the card, I want the card to be able to change its height and flip state.

`useEffect(setMaxHeight, [flashcard.question, flashcard.answer, flashcard.options])`
→ Recalculate the height whenever the question, answer, or options change.

`window.addEventListener('resize', setMaxHeight)`
→ Recalculate the height to adapt to different screen sizes.

`onClick={() => setFlip(!flip)}`
→ Change the flip state when the user clicks the card.
3) css:

box-shadow: X Y blur spread color
Direction → Blur → Size → Darkness
Header → Card → Dropdown → Dialog
Light  → Medium → Strong → Strong

FLEX: display:flex → 1D layout | justify-content → main axis | align-items → cross axis
       flex-direction → direction | flex-wrap → wrap | gap → spacing
Example: display:flex; justify-content:space-between; align-items:center; gap:1rem;

GRID: display:grid → 2D layout | grid-template-columns → columns | grid-template-rows → rows
       gap → spacing
Example: display:grid; grid-template-columns:repeat(3,1fr); gap:1rem;

Goal: A clickable flashcard that slightly lifts on hover and smoothly flips in 3D when clicked.
transition → HOW FAST the change happens
transform  → WHAT movement/rotation happens
/* Animation */
transition: 150ms;                 /* smooth change */
transform: translateY(-2px);       /* move */
transform: rotateY(180deg);        /* rotate */
transform: perspective(1000px);   /* 3D perspective */

/* 3D */
transform-style: preserve-3d;      /* keep 3D children */
backface-visibility: hidden;       /* hide back side */
