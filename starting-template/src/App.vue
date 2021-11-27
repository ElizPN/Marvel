<template>
  <div id="app">
    <app-header :changeSearch="changeSearch"/>

    <div class="container">
      <h1 class="pt-3 pb-3">Персонажи Marvel</h1>

        <!-- <pre>  searchCharacters : {{ searchCharacters }}</pre> -->
            <pre>search: {{search}}</pre>
        <!-- <pre>characterIndex:{{characterIndex}}</pre> -->
      <!-- <pre>characters: {{ characters }} </pre> -->
    <!-- <pre>person: {{person}}</pre> -->
    <!-- <pre>loading: {{loading}}</pre> -->
      <app-modal :person="person"/>

      <spinner v-if="loading"/>

    <div class="row">
        <h5 v-if="!searchCharacters.length && !loading ">Nothing found...</h5>

        <div 
            v-for="(el, idx) in searchCharacters"
            :key="idx"
            class="card mb-3 col-sm-12 col-md-6 col-lg-4">
            <div class="row g-0">
                <div class="col-4">
                <img
                    :src="el.thumbnail"
                    :alt="el.name"
                    style="max-width: 100%;"
                />
                </div>
                <div class="col-8">
                <div class="card-body">
                    <h5 class="card-title">{{el.name}}</h5>
                    <button
                    type="button"
                    data-bs-toggle="modal"
                    data-bs-target="#exampleModal"
                    class="btn btn-secondary btn-sm"
                    @click="characterIndex = idx" 
                    >
                    Подробнее
                    </button>
                </div>
                </div>
            </div>
            </div>
        </div>
        </div>
  </div>
</template>

<script>
import Spinner from "./components/Spinner";
import AppModal from "./components/AppModal";
import AppHeader from "./components/AppHeader";

export default {
  name: "App",
  components: {
    AppHeader,
    AppModal,
    Spinner,
  },
  data() {
    return {
      loading: false,
      characters: [],
      characterIndex: 0,
      search: '',
    };
  },
  methods: {
    fetchCharacters: function() {
      return fetch(`https://netology-api-marvel.herokuapp.com/characters`)
        .then((res) => res.json())
        .then((json) => (this.characters = json));
    },
    changeSearch: function (value) {
        this.search = value;
    }

  },
  computed: {
      person: function () {
          return this.characters[this.characterIndex] || null
      },
      searchCharacters : function() {
          const {characters, search} = this
          return characters.filter((person) => {
              return person.name.toLowerCase()
              .indexOf(search.toLowerCase()) !== -1
          })
          
      },
  },
  async mounted() {
    this.loading = true;
    await this.fetchCharacters();
    this.loading = false;
  },
};
</script>

<style></style>
