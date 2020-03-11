<template>
  <div>
    <div>
      <img :src="this.cat.url" alt="" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "CatRating",
  data() {
    return {
      cat: null
    };
  },
  created() {
    this.getCat();
  },
  methods: {
    getCat() {
      axios.defaults.headers.common["x-api-key"] =
        "574f7140-45cb-40bb-98ac-e6f8ea43fc3f";
      axios
        .get("https://api.thecatapi.com/v1/images/search", {
          params: { limit: 1, size: "full" }
        })
        .then(response => {
          this.cat = response.data[0];
        });
    }
  }
};
</script>

<style scoped></style>
