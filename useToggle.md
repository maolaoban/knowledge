```js
function useToggle(initialValue) {
 const [value, setValue] = React.useState(initialValue);

 const toggle = React.useCallback(() => {
  setValue(v => !v);
 }, []);

 return [value, toggle];
}
```