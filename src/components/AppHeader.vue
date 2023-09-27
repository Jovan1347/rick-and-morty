<template>
  <div class="header-wrapper">
    <div class="header-content">
      <div class="header-content-logo">
        <img src="../assets/images/rick-and-morty-logo.png" alt="" />
      </div>
      <div class="header-content-nav">
        <router-link to="/" class="header-content-nav-item">Characters</router-link>
        <router-link to="/planets" class="header-content-nav-item">Planets</router-link>
      </div>
    </div>
  </div>
</template>

<script>
import { RouterLink } from 'vue-router'

export default { components: { RouterLink } }
</script>

<style lang="scss">
.header-wrapper {
  width: 100%;
  padding: 20px 50px;
  background-color: #fffafa;
  border-bottom: 1px solid #46494d5b;

  .header-content {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;

    &-logo {
      width: 100px;

      img {
        width: 100%;
      }
    }

    &-nav {
      display: flex;
      justify-content: space-between;

      &-item {
        font-size: 1.25rem;
        font-weight: bold;
        text-decoration: none;
        color: #202329;
        margin-left: 20px;
        cursor: pointer;
        transition: color 0.2s ease-out;

        &:hover {
          color: #f08d49;
        }
      }

      .router-link-active {
        color: #f08d49;
      }
    }
  }
}

@media (min-width: 768px) {
  .header-wrapper {
    .header-content {
      &-logo {
        width: 150px;
      }

      &-nav {
        &-item {
          font-size: 1.5rem;
        }
      }
    }
  }
}
</style>
