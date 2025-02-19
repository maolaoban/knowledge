下凹tabbar

```vue
<template>
  <div class="g-container">
    <div class="g-content">
      <div class="g-filter"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
};
</script>

<style>
.g-container {
  width: 100%;
  height: 50px;
  background: #000;
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  overflow:hidden;
}
.g-content {
  height: 100px;
  filter: contrast(20);
  background: #fff;
}
.g-filter {
  filter: blur(10px);
  height: 100px;
  background: radial-gradient(
    circle at 50% -10px,
    transparent 0,
    transparent 40px,
    #000 20px,
    #000
  );
}
</style>

```

