<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <SearchBar @termChange="onTermChange" />
</template>

<script>
  import SearchBar  from "./components/SearchBar.vue";
  import VideoList from "./components/VideoList.vue"
  const API_KEY = 'AIzaSyB45Pox1wG4E1YXsNpsHX5Dd8y8PUvXnwA'

  export default {
    name: 'App',
    components: {
      SearchBar,
      VideoList
    },
    methods: {
      onTermChange(searchTerm) {
        fetch('https://www.googleapis.com/youtube/v3/search?' + new URLSearchParams({
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        })).then((response) => response.json()).then((data) => console.log(data))
      }
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
