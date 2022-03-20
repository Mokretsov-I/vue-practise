<template>
  <div class="App">
    <app-header />
    <div class="container">
      <post-form @create="createPost" />
      <post-list :posts="posts" @remove="removePost" />
    </div>
  </div>
</template>

<script>
  import PostForm from "@/components/PostForm";
  import PostList from "@/components/PostList";
  import AppHeader from "@/components/AppHeader";

  export default {
    components: {
      PostForm,
      PostList,
      AppHeader,
    },
    data() {
      return {
        posts: [],
      };
    },
    mounted() {
      new Promise(async (resolve, reject) => {
        try {
          const response = await fetch(
            `https://jsonplaceholder.typicode.com/posts?_limit=10`
          );
          resolve(await response.json());
        } catch {
          reject("Произошла ошибка(");
        }
      })
        .then((data) => {
          this.posts = [...this.posts, ...data];
        })
        .catch((error) => {
          console.error(error);
        });
    },
    methods: {
      createPost(post) {
        this.posts.push(post);
      },
      removePost(post) {
        this.posts = this.posts.filter((p) => p.id !== post.id);
      },
    },
  };
</script>

<style lang="scss">
  $white-color: #fff;
  $main-color: teal;

  $xl_container: 1440px;
  $lg_container: 992px;
  $md_container: 768px;
  $sm_container: 576px;

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .App {
    background-color: rgba(0, 0, 0, 0.7);
    width: 100%;
    height: 100%;
    min-height: 100vh;
    color: $white-color;

    .container {
      max-width: $xl_container;
      margin: 0 auto;
      padding: 0 15px;
    }
  }
</style>
