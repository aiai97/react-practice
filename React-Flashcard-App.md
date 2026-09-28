project: https://github.com/WebDevSimplified/React-Flashcard-App/tree/master 


I use `useRef` to access the user's selected query conditions. 
This is a great tool to access dom values.

`categoryEl.current.value` → the selected category
`amountEl.current.value` → the number of questions

I use `useEffect` to fetch the data when the app first loads.
I need to get the categories first, so I can provide them for the user to choose from.

