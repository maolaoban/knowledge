URL参数

```javascript
const getURLParameters = url =>
  (url.match(/([^?=&]+)(=([^&]*))/g) || []).reduce(
    (a, v) => ((a[v.slice(0, v.indexOf('='))] = v.slice(v.indexOf('=') + 1)), a),
    {}
  )

// 事例
getURLParameters('http://url.com/page?n=Adam&s=Smith') // {n: 'Adam', s: 'Smith'}
getURLParameters('google.com') // {}
```

