<template>
    <article class="user__content text-center">
      <div class="user__photo rounded-circle">
        <img
          :src="data.photo || 'assets/img/photo-cover.svg'"
          alt="photo">
      </div>
      <div class="user__name mockup-heading2">
        <p class="mb-0 text-overflow">{{data.name}}</p>
      </div>
      <div class="user__position mockup-p">
        <p class="mb-0 text-overflow">{{data.position}}</p>
      </div>
      <div class="user__email mockup-p">
        <a :href="'mailto:' + data.email" class="text-dark text-decoration-none">{{data.email}}</a>
      </div>
      <div class="user__phone mockup-p">
        <a :href="'tel:' + data.phone" class="text-dark text-decoration-none">{{data.phone}}</a>
      </div>
    </article>
</template>

<script>
    export default {
      props: [
        'data'
      ],
    }
</script>

<style lang="scss" scoped>
  .user {
    &__content {
      width: 200px;
      margin: 1em auto 3.9em;
      @media only screen and (max-width: 768px){
        margin: 0.7em auto 2.9em;
      }
    }
    &__photo {
      display: flex;
      margin: 0 auto;
      width: 70px;
      height: 70px;
      overflow: hidden;
      background-image: url('/assets/img/photo-cover.svg');
    }
    &__name {
      margin-top: 15px;
      letter-spacing: -0.3px;
    }
    &__position {
      margin-top: 10px;
    }
    &__email {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }
    &__phone {
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
    }
  }
</style>
