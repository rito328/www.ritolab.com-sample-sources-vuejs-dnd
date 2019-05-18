<template>
  <div>
    <gp-a></gp-a>
    <gp-b></gp-b>
  </div>
</template>

<script>
  import gpA from './gpA'
  import gpB from './gpB'

  export default {
      name: "root",
      components: { gpA, gpB }
  }
</script>

<style>
  .item {
    display: inline-block;
    margin: 10px;
    padding: 10px;
    border: 1px solid #7f7f7f;
    border-radius: 10px;
    background-color: #ffffff;
  }
  .item:hover {
    cursor: grab;
  }
  .item:active {
    cursor: grabbing;
  }
</style>