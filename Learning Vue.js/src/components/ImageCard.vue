<template>
  <div class="card mt-5" :class="{ 'mb-5': !showSummary }" v-cloak>
    <img :src="photo.imgSrc" class="card-img-top" :alt="photo.imgTitle" />
    <div class="card-body">
      <h5 class="card-title">{{ photo.imgTitle }}</h5>
      <p class="card-text">
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </p>
      <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
  </div>
</template>

<script>
import axios from "axios";

const ImageCard = {
  props: ["showSummary"],
  data: () => ({ photo: { imgSrc: "", imgTitle: "" } }),
  created() {
    this.fetchPhoto();
  },
  methods: {
    fetchPhoto() {
      axios
        .get("https://jsonplaceholder.typicode.com/photos")
        .then(data => {
          this.photo = {
            imgSrc: data.data[0].url,
            imgTitle: data.data[0].title
          };
        })
        .catch(err => console.log(err));
    }
  }
};

export default ImageCard;
</script>
