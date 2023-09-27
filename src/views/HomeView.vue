<template>
  <header class="home-page-header">
    <app-header></app-header>
  </header>

  <div class="home-page-wrapper">
    <section class="home-page-article-section">
      <article class="home-page-article">
        <h1>Rick and Morty characters</h1>
      </article>
    </section>

    <section class="home-page-characters-section">
      <app-character-card></app-character-card>
      <app-back-to-top class="home-page-wrapper-back-to-top"></app-back-to-top>
    </section>
  </div>
</template>

<script>
import AppCharacterCard from '../components/AppCharacterCard.vue'
import AppHeader from '../components/AppHeader.vue'
import AppBackToTop from '../components/AppBackToTop.vue'

export default {
  components: { AppCharacterCard, AppHeader, AppBackToTop }
}
</script>

<style lang="scss">
.home-page-wrapper {
  display: flex;
  flex-direction: column;
  width: 100%;
  position: relative;

  .home-page-wrapper-back-to-top {
    position: sticky;
    bottom: 25px;
    left: 100%;
  }

  .home-page-article-section {
    background-color: #fffafa;

    .home-page-article {
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      width: 100%;
      padding: 100px 0;

      h1 {
        font-size: 3rem;
        font-weight: bold;
        color: #f08d49;
        text-shadow: 5px 3px 6px #272b33;
      }
    }
  }

  .home-page-characters-section {
    background-color: #272b33;
  }
}

section {
  padding: 50px;
}

@media (min-width: 1024px) {
  .home-page-wrapper {
    .home-page-article-section {
      .home-page-article {
        padding: 150px 0;
        h1 {
          font-size: 5.5rem;
        }
      }
    }
  }
}
</style>
