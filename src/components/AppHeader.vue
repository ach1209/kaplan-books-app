<template>
  <div class="header">
    <div class="header__menu" v-bind:class="[isToggled ? 'header__menu--open' : 'header__menu--closed']">
      <div class="header__menu-icon">
        <a href="#"><i class="material-icons" v-on:click="toggleNav">menu</i></a>      
      </div>

      <ul class="header__menu-items">
        <li>
          <a href="#"><i class="material-icons">assignment</i>Project Management</a>
        </li>
        <li>
          <a href="#"><i class="material-icons">assessment</i>Configuration</a>
        </li>
      </ul>
    </div>

    <span class="header__title" v-bind:class="[isToggled ? 'header__title--pushed' : '']">Kaplan Books</span>
  </div>
</template>

<script>
export default {
  name: 'AppHeader',
  data() {
    return {
      isToggled: false
    }
  },
  methods: {
    toggleNav: function() {
      this.isToggled = !this.isToggled;
    }
  }
}
</script>

<style lang="scss">

.header {
  background-color: $bgColor;
  min-height: 6rem;
  padding-right: 2rem;
  padding-left: 2rem;
  @include flex-center-align;

  &__menu {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1;
    height: 100vh;
    background-color: $bgColor;
    border-right: 1px solid #e0e0e0;
    display: flex;
    flex-direction: column;
    transition: all 0.3s cubic-bezier(.86,.16,.12,.91);

    &:hover,
    &:focus {
      cursor: pointer;
    }

    &-icon {
      @include flex-center-align;      
      height: 6rem;

      a {
        color: $fontColor;
        text-decoration: none;
        margin: 1.7rem;
      }
    }

    &-items {
        list-style-type: none;
        display: block;

      li {
        padding: 1rem 0;        
        margin-bottom: 1.5rem;
        transition: all 0.3s cubic-bezier(.86,.16,.12,.91);

        &:hover,
        &:focus {
          background-color: rgba($bgColor2, 0.5);
        }

        a {
          width: 20.2rem;
          font-size: 1.2rem;
          color: $fontColor;
          text-decoration: none;
          margin-left: 1.7rem;
          text-transform: uppercase;
          @include flex-center-align;

          .material-icons {
            margin-right: 2rem;
          }
        }        
      }
    }

    &--closed {
      width: 6rem;
      overflow: hidden;
    }

    &--open {
      width: 22rem;
      overflow: auto;
    }

  }

  &__title {
    font-size: 2rem;
    color: $fontColor;
    letter-spacing: 0.1rem;
    margin-left: 7rem;
    transition: all 0.3s cubic-bezier(.86,.16,.12,.91);
  
    &--pushed {
      margin-left: 23rem;
    }
  }
}

</style>