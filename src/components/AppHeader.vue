<template>
  <div class="container">
      <div class="header">
          <a href="#" class="header__logo">
              <div class="header__image">
                <img :src="require('@/image/logo.png')" alt="">
              </div>
              <div class="header__title">
                <p>Vue project</p>
              </div>
          </a>
          <div class="header__links">
              <a href="#">Link</a>
              <a href="#">Link</a>
              <a href="#">Link</a>
              <a href="#">Link</a>
          </div>
      </div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang='scss' scope>
  .header{
    display: flex;
    justify-content: space-between;
    align-items: center;

    &__logo{
      display: flex;
      align-items: center;
      text-decoration: none;
      color: inherit;
    }

    &__image{
      display: block;
      max-width: 80px;
      max-height: 80px;
      overflow: hidden;

      img{
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    &__title{
      margin-left: 30px;

      p{
        font-size: 1.5em;
      }
    }

    &__links{
      display: flex;

      a{
        margin-left: 30px;
        text-decoration: none;
        color: inherit;
        font-size: 1.5em;
      }
    }
  }
</style>