<template>
  <main class="gallery">
    <PhotoCard v-for="item in items" :key="item.title" :item="item" />
  </main>
</template>

<script>
import PhotoCard from "./PhotoCard.vue";
import axios from "axios";
// import doc from "./doc.json";

export default {
  name: "SpaceGallery",
  components: {
    PhotoCard,
  },
  data() {
    return {
      // apis: [`https://api.nasa.gov/planetary/apod?api_key=DEMO_KEY`, `https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&page=2&api_key=DEMO_KEY`],
      // data: doc,
      date: new Date(),
      dateString: String,
      api: `https://api.nasa.gov/planetary/apod`,
      keys: {
        start_date: "",
        api_key: "DEMO_KEY",
      },
      items: [],
    };
  },
  methods: {
    getData(url, keys) {
      url =
        url +
        "?" +
        "start_date=" +
        keys.start_date +
        "&api_key=" +
        keys.api_key;
      axios
        .get(url)
        .then((response) => {
          console.log(response.data);
          console.log(typeof response.data === "object");
          this.items.push(...response.data);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    // getLocal(data) {
    //   console.log(Array.isArray(data));
    //   this.items.push(...data);
    // },
    // viewKey( obj, newKey ){
    //         newKey = obj[newKey];
    //         console.log(newKey);
    //         return newKey;
    //     },
    // renameKey(oldObj, oldKey, newKey, newObj) {
    //   if (!oldObj[newKey]) {
    //     oldObj[newKey] = newObj[oldKey];
    //     delete newObj[oldKey];
    //   }
    // },

    // createItems() {
    //   console.log("created");
    //     for (let index = 0; index < this.apis.length; index++) {
    //     this.getData(this.apis[index]);
    // }
    // this.getLocal(doc);
    // console.log(this.items);
    // this.items.forEach((element) => {
    //   this.renameKey(element, "img_src", "url", element);
    //   this.renameKey(element, "name", "title", element.rover);
    //   this.renameKey(element, "full_name", "explanation", element.camera);
    // });
    // },
  },
  beforeMount() {
    this.date.setDate(this.date.getDate() - 35);
    // console.log(this.dateString);
    // this.getLocal(doc);
    // console.log(this.api);
    this.keys.start_date = this.date.toISOString().substring(0, 10);
    console.log(this.keys);
    this.getData(this.api, this.keys);
    // this.createItems();
    // this.getData(this.apis[0])
  },
};
</script>

<style lang="stylus">
.gallery
    display flex
    flex-wrap wrap
    gap 16px
    padding 10px 10%
</style>
