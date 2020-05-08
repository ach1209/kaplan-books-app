<template>
  <div class="header">
    <div class="header__menu" :class="[isToggled ? 'header__menu--open' : 'header__menu--closed']">
      <div class="header__menu-icon" @click="toggleNav">
        <a href="#"><i class="material-icons">menu</i></a>      
      </div>
      <ul class="header__menu-items" :class="[isToggled ? 'header__menu-items--open' : 'header__menu-items--closed']">
        <li>
          <a href="#"><i class="material-icons">assignment</i>Project Management</a>
        </li>
        <li>
          <a href="#"><i class="material-icons">assessment</i>Configuration</a>
        </li>
      </ul>
    </div>
    <span class="header__title" :class="[isToggled ? 'header__title--pushed' : '']">Kaplan Books</span>
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
    toggleNav() {
      this.isToggled = !this.isToggled;
    }
  }
}
</script>

<style lang="scss" scoped>

.header {
  @include flex-center;  
  position: relative;
  min-height: 6rem;
  padding-right: 2rem;
  padding-left: 2rem;
  background-color: $bgColor;

  @include device-lg {
    position: unset;
  }

  &__menu {
    display: flex;
    flex-direction: column;    
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    cursor: pointer;    
    transition: all 0.3s cubic-bezier(.86,.16,.12,.91);

    @include device-lg {
      position: fixed;
      background-color: $bgColor;      
      border-right: 1px solid $borderColor;      
      border-bottom: none;
      height: 100vh;    
    }

    &-icon {
      @include flex-center;      
      height: 6rem;

      a {
        color: $fontColor;
        text-decoration: none;
        margin: 1.7rem;
      }
    }

    &-items {
      display: block;
      width: 100vw;         
      background-color: $bgColor;
      border-bottom: 1px solid $borderColor;      
      list-style-type: none;
      transition: all 0.5s cubic-bezier(.86,.16,.12,.91);

      @include device-lg {
        width: unset;
        border: none;
        transform: none;
      }

      &--closed {
        display: none;
        transform: translateX(-100vw);

        @include device-lg {
          display: block; 
          transform: none;
        }
      }

      &--open {
        transform: translateX(0);

        @include device-lg {
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
          @include flex-center;
          width: 20.2rem;
          margin-left: 1.7rem;
          font-size: 1.2rem;
          color: $fontColor;
          text-decoration: none;
          text-transform: uppercase;

          .material-icons {
            margin-right: 2rem;
          }
        }        
      }
    }

    &--closed {
      @include device-lg {
        width: 6rem;
        overflow: hidden;
      }
    }

    &--open {
      @include device-lg {
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
      @include device-lg {
        margin-left: 23rem;
      }
    }
  }
}

</style>