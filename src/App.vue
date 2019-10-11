<template>
  <div id="app">
    <article v-for="quote in quotes" class="message">
      <div class="message-header">
        <p>Perceval</p>
        <button class="delete" aria-label="delete"></button>
      </div>
      <div class="message-body">{{ quote.citation }}</div>
    </article>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "app",
  components: {},
  data() {
    return {
      quotes: null
    };
  },
  created() {
    axios
      .get(
        `${"https://cors-anywhere.herokuapp.com/"}https://kaamelott.chaudie.re/api/all/livre/1/personnage/Perceval`
      )
      .then(response => (this.quotes = response.data.citation));
  }
};
</script>

<style>
.message {
  margin: 20px 100px 20px 100px;
}
</style>
