<template>
  <div class="menu-btn" @click="toggleMobileMenu()">
    <div class="menu-btn__hamburger" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      showMobileMenu: false,
    }
  },
  watch: {
    $route: {
      handler() {
        this.showMobileMenu = false
        const MENU_BTN = document.querySelector('.menu-btn')
        MENU_BTN.classList.remove('open')
      },
    },
  },
  methods: {
    toggleMobileMenu() {
      const MENU_BTN = document.querySelector('.menu-btn')
      this.showMobileMenu = !this.showMobileMenu
      this.$emit('toggle-mobile-menu', this.showMobileMenu)
      if (this.showMobileMenu) {
        MENU_BTN.classList.add('open')
      } else {
        MENU_BTN.classList.remove('open')
      }
    },
  },
}
</script>

<style scoped>
.menu-btn {
  position: relative;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 60px;
  height: 60px;
  transition: all 0.5s ease-in-out;
  border-radius: 50%;
  display: none;
  transform: scale(0.8);
}

.menu-btn__hamburger {
  width: 28px;
  height: 4px;
  background: var(--gray-dark);
  transition: all 0.5s ease-in-out;
}

.menu-btn__hamburger::before,
.menu-btn__hamburger::after {
  content: '';
  position: absolute;
  background: var(--gray-dark);
  width: 32px;
  height: 3px;
  transition: all 0.5s ease-in-out;
}

.menu-btn__hamburger::before {
  transform: translateY(-8px);
}

.menu-btn__hamburger::after {
  transform: translateY(8px);
}

.menu-btn.open .menu-btn__hamburger {
  transform: translateX(-50px);
  background: transparent;
  box-shadow: none;
}

.menu-btn.open .menu-btn__hamburger::before {
  transform: rotate(45deg) translate(35px, -35px);
}

.menu-btn.open .menu-btn__hamburger::after {
  transform: rotate(-45deg) translate(35px, 35px);
}

.menu-btn:active {
  background: #476bd2;
}

@media screen and (max-width: 1000px) {
  .menu-btn {
    display: flex;
  }
}
</style>
