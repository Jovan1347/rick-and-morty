<template>
  <div class="cards-container">
    <div v-for="character in characters" :key="character.id" class="card">
      <div class="card-thumbnail">
        <div class="card-thumbnail-image">
          <img :src="character.image" :alt="character.name" />
        </div>
      </div>
      <div class="card-text">
        <div class="card-text-name">{{ character.name }}</div>
        <div class="card-text-status">{{ character.status }}</div>
        <div class="card-text-creation-time">{{ character.created }}</div>
        <div class="card-text-location">{{ character.location.name }}</div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      characters: [],
      page: 1
    }
  },

  created() {
    this.fetchCharacters()
    window.addEventListener('scroll', this.handleScroll)
  },

  methods: {
    fetchCharacters() {
      axios
        .get(`https://rickandmortyapi.com/api/character?page=${this.page}`)
        .then((response) => {
          this.characters = [...this.characters, ...response.data.results]
          this.page++
          console.log(this.characters)
        })
        .catch((error) => {
          console.error('Error fetching data:', error)
        })
    },

    handleScroll() {
      const bottomOfPage =
        window.innerHeight + window.scrollY >= document.documentElement.scrollHeight

      if (bottomOfPage) {
        this.fetchCharacters()
      }
    }
  },

  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="scss">
.cards-container {
  display: grid;
  grid-template-columns: auto;
  width: 100%;

  .card {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    margin-bottom: 50px;
    padding: 15px;
    border-radius: 10px;
    background-color: #202329;
    color: #fffafa;
    box-shadow:
      #00000029 0px 3px 6px,
      #0000003b 0px 3px 6px;
    transition:
      box-shadow 0.3s ease-out,
      scale 0.3s ease-out;

    &-thumbnail {
      margin-bottom: 30px;

      &-image {
        display: flex;
        width: 100%;

        img {
          border-radius: 10px;
          width: 100%;
        }
      }
    }

    &-text {
      display: flex;
      flex-direction: column;
      margin-left: 10px;
      text-align: center;
      font-size: 1.25rem;
      line-height: 35px;

      &-name {
        transition: color 0.3s ease-out;
      }
    }

    &:hover {
      box-shadow:
        #000 0px 50px 100px -20px,
        #000 0px 30px 60px -30px,
        #000 0px -2px 6px 0px inset;

      scale: 1.07;
    }

    &:hover .card-text-name {
      color: #f08d49;
    }
  }
}

@media (min-width: 768px) {
  .cards-container {
    grid-template-columns: auto auto;
    justify-content: space-between;

    .card {
      max-width: 315px;
    }
  }
}

@media (min-width: 1024px) {
  .cards-container {
    grid-template-columns: auto auto auto;
    justify-content: space-between;

    .card {
      max-width: 300px;
    }
  }
}

@media (min-width: 1360px) {
  .cards-container {
    grid-template-columns: auto auto auto auto;
    justify-content: space-between;
  }
}
</style>
