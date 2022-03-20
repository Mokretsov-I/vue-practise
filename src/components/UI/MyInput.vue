<template>
  <input type="text" class="input" @input="updateInput" />
</template>

<script>
  export default {
    name: "my-input",
    props: {
      modelValue: [String, Number],
    },
    methods: {
      updateInput(event) {
        this.$emit("update:modelValue", event.target.value);
      },
    },
  };
</script>

<style lang="scss" scope>
  .input {
    background: none;
    border: 2px solid teal;
    display: block;
    padding: 10px 15px;
    color: inherit;
    width: 100%;

    &::selection {
      background: teal;
    }

    &:focus {
      outline: none;
    }
  }
</style>
