### Install
```
npm i map-all
```



### Promise.all + map
```js
const urls = [
  'api/posts/1',
  'api/posts/1/comments'
]

// before
const posts = await Promise.all(urls.map(async (url) => {
  const res = await fetch(url);
  return res.json();
}))

// after
const posts = await all(urls, async (url) => {
  const res = await fetch(url);
  return res.json();
})
```

### can also resolve an object of promises

```js
const results = await all({
  one: Promise.resolve('one!'),
  two: Promise.resolve('two!'),
})

results // { one: 'one!', two: 'two!' }
```

