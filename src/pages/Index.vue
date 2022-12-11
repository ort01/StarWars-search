<template>
  <div class="container">
    <h3>StarWars search</h3>
    <SearchBar @searchName="searchCharacters" :searchName="searchName" />
    <div v-if="(arrayOfCharacters.length === 0 && searchName.length === 0)">
      <p>Enter search phrase</p>
    </div>
    <div v-if="(arrayOfCharacters.length > 0)" style="margin-bottom: 150px">
      <div v-for="character in arrayOfCharacters" :key="character.index">
        <SearchedPhrase :foundName="character.name" :searchName="searchName" />
      </div>
    </div>
    <div v-if="(arrayOfCharacters.length === 0 && searchName.length > 0)">
      <p>Nothing found</p>
    </div>
  </div>

</template>



<script>
import axios from 'axios'
import SearchBar from 'src/components/SearchBar.vue'
import SearchedPhrase from 'src/components/SearchPhrase.vue'

export default {
  name: 'PageIndex',
  components: {
    SearchBar,
    SearchedPhrase
  },
  data: () => {
    return {
      arrayOfCharacters: [],
      searchName: ''
    }
  },
  methods: {
    async searchCharacters(name) {
      this.searchName = name
      if (name.trim().length > 0) {
        axios.get(`https://swapi.py4e.com/api/people/?search=${name}`).then((res) => {
          this.arrayOfCharacters = res.data.results
        })
      } else {
        this.arrayOfCharacters = []
      }
    }
  },
}
</script>




<style>
body {
  height: 100vh;
  margin: 0;
}

.container {
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.container h3 {
  font-weight: 300;
  display: block;
  color: #2C3843;
  cursor: default;
}

.container p {
  font-size: 0.7rem;
}
</style>
