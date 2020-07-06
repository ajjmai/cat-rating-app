<template>
  <div>
    <div class="button-container">
      <button @click="liked()">Like!</button>
      <button @click="notLiked()">Nope</button>
    </div>
    <div>
      <p>
        You have liked {{ likedCats }} cats and not liked {{ notLikedCats }}.
      </p>
    </div>
    <div v-if="loading">
      Downloading cat photo ...
    </div>
    <div v-else>
      <img class="cat-image" :src="this.cat.url" alt="" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CatRating",
  data() {
    return {
      cat: null,
      loading: true,
      notLikedCats: 0,
      likedCats: 0
    };
  },
  created() {
    this.getCat();
  },
  methods: {
    notLiked() {
      this.notLikedCats++;
      this.loading = true;
      this.getCat();
    },
    liked() {
      this.likedCats++;
      this.loading = true;
      this.getCat();
    },
    getCat() {
      axios.defaults.headers.common["x-api-key"] =
        "574f7140-45cb-40bb-98ac-e6f8ea43fc3f";
      axios
        .get("https://api.thecatapi.com/v1/images/search", {
          params: { limit: 1, size: "full" }
        })
        .then(response => {
          this.cat = response.data[0];
          this.loading = false;
        });
    }
  }
};
</script>

<style scoped>
.cat-image {
  max-width: 40%;
  border: 1px solid #ddd;
  border-radius: 4px;
  padding: 5px;
  background-color: lavender;
}

.button-container {
  margin-bottom: 25px;
}

button {
  width: 80px;
  height: 50px;
  border-radius: 4px;
  margin: 5px;
  background-color: lavender;
  font-size: 20px;
  color: darkslateblue;
}
</style>
