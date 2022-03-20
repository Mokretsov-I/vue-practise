<template>
  <div class="posts" v-if="posts.length > 0">
    <h2 class="posts__title">Список постов</h2>
    <transition-group
      @enter="enter"
      @leave="leave"
      :css="false"
      name="post-list"
    >
      <post-item
        class="posts__item"
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
      />
    </transition-group>
  </div>
  <h2 v-else class="posts__title">Список постов пуст</h2>
</template>

<script>
  import PostItem from "@/components/PostItem";
  export default {
    components: { PostItem },
    props: {
      posts: {
        type: Array,
        required: true,
      },
    },
    methods: {
      enter(el, done) {
        el.classList.add("enterPost");
        setTimeout(() => {
          el.classList.remove("enterPost");

          done();
        }, 1000);
      },
      leave(el, done) {
        el.classList.add("leavePost");
        setTimeout(() => {
          el.classList.remove("leavePost");
          done();
        }, 1000);
      },
    },
  };
</script>

<style lang="scss" scope>
  .posts {
    overflow: hidden;
    &__title {
      margin-bottom: 20px;
    }
    &__item {
      width: 100%;
    }
  }
  .enterPost {
    & h3,
    & p {
      animation: 1s animBody;
    }
    & button {
      animation: 1s animBtn;
    }
  }
  .leavePost {
    & h3,
    & p {
      animation: 1s reverse animBody;
    }
    & button {
      animation: 1s reverse animBtn;
    }
  }
  @keyframes animBody {
    0% {
      transform: translateX(-100%);
    }
    50% {
      transform: translateX(100px);
    }
    100% {
      transform: translateX(0);
    }
  }
  @keyframes animBtn {
    0% {
      transform: translateX(200px);
    }
    50% {
      transform: translateX(-100px);
    }
    100% {
      transform: translateX(0);
    }
  }
</style>
