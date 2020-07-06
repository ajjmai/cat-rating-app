<template>
  <div>
    <h1>Rate this cat:</h1>
    <div><cat-rating></cat-rating></div>
  </div>
</template>

<script>
import CatRating from "../components/CatRating";
export default {
  name: "CatRatings",
  components: { CatRating }
};
</script>

<style scoped></style>
