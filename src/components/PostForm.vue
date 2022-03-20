<template>
  <form @submit.prevent class="main-form">
    <my-input v-model="post.title" class="main-form__input" />
    <my-textarea v-model="post.body" class="main-form__input"></my-textarea>
    <my-button @click="createPost" class="main-form__btn main-form__input"> Add post </my-button>
  </form>
</template>

<script>
  export default {
    data() {
      return {
        post: {
          title: "",
          body: "",
        },
      };
    },
    methods: {
      createPost() {
        this.post.id = Date.now();
        this.$emit("create", this.post);
        this.post = {
          title: "",
          body: "",
        };
      },
    },
  };
</script>

<style lang="scss" scope>
  .main-form {
    display: flex;
    flex-direction: column;
    margin: 20px auto;
    max-width: 90%;

    &__input:not(:first-child) {
      margin-top: 20px;
    }

    &__btn {
      align-self: flex-end;
    }
  }
</style>
