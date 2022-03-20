<template>
  <div class="post-item">
    <div class="post-item__body">
      <h3 class="post-item__title">Title: {{ post.title }}</h3>
      <p class="post-item__text">Body: {{ post.body }}</p>
    </div>

    <div class="post-item__controls">
      <my-button @click="$emit('remove', post)">Удалить</my-button>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      post: {
        type: Object,
        require: true,
      },
    },
    methods: {
      enter(el, done) {
        console.log(el);
      },
      leave(el, done) {
        console.log(el);
      },
    },
  };
</script>

<style lang="scss" scope>
  .post-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 2px solid teal;
    padding: 10px 15px;
    &:not(:first-child) {
      margin-top: 15px;
    }
    &__controls {
      display: flex;
    }
    &__title {
      font-size: 1.2em;
      font-weight: bold;
      margin-bottom: 15px;
    }
    &__text {
      font-size: 0.8em;
    }
  }
</style>
