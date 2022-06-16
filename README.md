# useSfx-react-hook
More granular useEffet() hook replacement

```javascript
const [someValue1, setSomeValue1] = useState(null);
const [someValue2, setSomeValue2] = useState(false);
const anotherValueThatCanChange = "some other value";
const [someValue0, setSomeValue0] = useState(true); // Some state that we don't necessarily want to track changes


// This hook will run on every render... similar to useEffect(()=>{})
useSfx((prev) => {
        if (prev.hasChanged({someValue1}, {anotherValueThatCanChange})) {
                // Do stuff if someValue1 or anotherValueThatCanChange is updated
        }
        if (prev.hasChanged({someValue2})) {
                // Do stuff if someValue2 got updated ...
                
                if (someValue0) { // Access an untracked state and always be confident that it is the fresh value.
                        // Do stuff with someValue0's value. This value will always be the fresh value even though the hook
                        // is not tracking its changes.
                }
        }
}, {someValue1, someValue2, anotherValueThatCanChange}); // Tell the hook to track the changes of these variables
```
