<template>
  <div class="header">
    <div class="header__menu" v-bind:class="[isToggled ? 'header__menu--open' : 'header__menu--closed']">
      <div class="header__menu-icon" v-on:click="toggleNav">
        <a href="#"><i class="material-icons">menu</i></a>      
      </div>

      <ul class="header__menu-items" v-bind:class="[isToggled ? 'header__menu-items--open' : 'header__menu-items--closed']">
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
    display: flex;
    flex-direction: column;
    transition: all 0.3s cubic-bezier(.86,.16,.12,.91);

    @include device-med {
      background-color: $bgColor;      
      border-right: 1px solid $borderColor;      
      border-bottom: none;
      height: 100vh;    
    }

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
      background-color: $bgColor;
      list-style-type: none;
      display: block;
      border-bottom: 1px solid $borderColor;
      width: 100vw;
      transition: all 0.5s cubic-bezier(.86,.16,.12,.91);

      @include device-med {
        width: unset;
        border: none;
        transform: none;
      }

      &--closed {
        transform: translateX(-100vw);

        @include device-med {
          transform: none;
        }
      }

      &--open {
        transform: translateX(0);

        @include device-med {
          transform: none;
        }
      }

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

      @include device-med {
        width: 6rem;
        overflow: hidden;
      }
    }

    &--open {

      @include device-med {
        width: 22rem;
        overflow: auto;
      }
    }

  }

  &__title {
    font-size: 2rem;
    color: $fontColor;
    letter-spacing: 0.1rem;
    margin-left: 7rem;
    transition: all 0.3s cubic-bezier(.86,.16,.12,.91);
  
    &--pushed {

      @include device-med {
        margin-left: 23rem;
      }
    }
  }
}

</style>