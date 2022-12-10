<template>
  <div class="container">
    <h3>StarWars search</h3>
    <SearchBar @searchName="updateSearchName" :searchName="searchName" />
    <div v-if="(charactersList.length === 0 && searchName.length === 0)">
      <p>Enter search phrase</p>
    </div>
    <div v-if="(charactersList.length > 0)">
      <div v-for="character in charactersList" :key="character.index" class="search-phrase">
        <FoundCharacters :characterName="character.name" :searchName="searchName" />
      </div>
    </div>
    <div v-if="(charactersList.length === 0 && searchName.length > 0)">
      <p>Nothing found</p>
    </div>
  </div>

</template>



<script>
import axios from 'axios'
import SearchBar from 'src/components/SearchBar.vue'
import FoundCharacters from 'src/components/FoundCharacters.vue'

export default {
  name: 'PageIndex',
  components: {
    SearchBar,
    FoundCharacters
  },
  data: () => {
    return {
      arrayOfCharacters: [],
      searchName: ''
    }
  },
  mounted() {
    axios.get(`https://swapi.py4e.com/api/people/`).then((res) => {
      this.arrayOfCharacters = res.data.results
    })
  },
  methods: {
    updateSearchName(searchName) {
      this.searchName = searchName
    },
  },
  computed: {
    charactersList() {
      if (this.searchName.trim().length > 0) {
        return this.arrayOfCharacters.filter((hero) => hero.name.toLowerCase().includes(this.searchName.trim().toLowerCase()))
      }
      return []
    }
  }
}
</script>




<style>
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
  color: #2C3843
}

.container p {
  font-size: 0.7rem;
}

.search-phrase {
  width: 340px;
  margin-bottom: 3px;
  background-color: #2C3843;
  color: white;
  border-radius: 4px;
}
</style>
