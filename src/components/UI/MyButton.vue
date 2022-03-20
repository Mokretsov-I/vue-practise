<template>
  <button class="btn">
    <slot />
  </button>
</template>

<script>
  export default {
    name: "my-button",
  };
</script>

<style lang="scss" scoped>
  .btn {
    background: none;
    padding: 10px 15px;
    color: inherit;
    border: 2px solid teal;
    cursor: pointer;
    transition: all 0.4s ease 0s;

    &:hover {
      transform: scale(1.1);
    }
  }
</style>
