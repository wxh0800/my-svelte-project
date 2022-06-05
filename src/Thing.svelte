<script>
  // 每当 prop 的值更改时，`current` 都会更新...
  export let current;

  // ...但 `initial` 初始化后就固定不变。
  const initial = current;
</script>

<p>
  <span style="background-color: {initial}">initial</span>
  <span style="background-color: {current}">current</span>
</p>

<style>
  span {
    display: inline-block;
    padding: 0.2em 0.5em;
    margin: 0 0.2em 0.2em 0;
    width: 4em;
    text-align: center;
    border-radius: 0.2em;
    color: white;
  }
</style>

