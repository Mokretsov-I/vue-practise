<template>
  <textarea class="textarea" @input="updateTextarea"> </textarea>
</template>

<script>
  export default {
    name: "my-textarea",
    props: {
      modelValue: [String, Number],
    },
    methods: {
      updateTextarea(event) {
        this.$emit("update:modelValue", event.target.value);
      },
    },
  };
</script>

<style lang="scss" scope>
  .textarea {
    background: none;
    border: 2px solid teal;
    display: block;
    padding: 10px 15px;
    color: inherit;
    resize: none;
    width: 100%;

    &::selection {
      background: teal;
    }

    &:focus {
      outline: none;
    }
  }
</style>
