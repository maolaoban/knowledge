# 使用grid布局进行重叠

```html
<figure>
    <img src="11.jpg">
    <figcaption>上海钓鱼自然风景 by zhangxinxu</figcaption>
</figure>
```

```css
figure {
    display: inline-grid;
}
figure > img,
figure > figcaption {
    /* 还可以简写为 grid-area: 1 / 2 */
    grid-area: 1 / 1 / 2 / 2;
}
```

