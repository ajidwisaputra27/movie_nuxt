<template>
  <div class="container">
    <div class="row mt-4">
      <div class="col">
        <h2>
          <strong>Movie</strong>
          {{ title }}
        </h2>
      </div>
      <div class="col">
        <NuxtLink :to="url" class="btn btn-primary float-right">
          <i class="far fa-eye"></i> Lihat Semua
        </NuxtLink>
      </div>
    </div>

    <div class="row mt-4">
      <template v-if="loading">
        <div class="col-12 col-md-3 mt-4" v-for="p in 4" :key="p">
          <content-placeholders rounded>
            <content-placeholders-img />
            <content-placeholders-text :lines="3" />
          </content-placeholders>
        </div>
      </template>
      <template v-else>
        <div
          class="col-12 col-md-3 mb-4"
          v-for="item in items.slice(0, 4)"
          :key="item.id"
        >
          <CardMovie :item="item" />
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  props: ['title', 'url'],
  data() {
    return {
      items: [],
      path: '',
      loading: false,
    }
  },
  created() {
    this.createItems()
  },
  methods: {
    createItems() {
      this.loading = true

      if (this.title == 'Top Rated') {
        this.path = 'top_rated'
      } else if (this.title == 'Popular') {
        this.path = 'popular'
      } else if (this.title == 'Now Playing') {
        this.path = 'now_playing'
      } else if (this.title == 'Upcoming') {
        this.path = 'upcoming'
      }

      this.$axios
        .get(
          `/movie/${this.path}?api_key=5f49291f3aa8ba5ccb190a5ee78f2569&language=en-US&page=1`
        )
        .then((response) => {
          this.items = response.data.results
          this.loading = false
        })
        .catch((error) => {
          console.log(error.response.data)
        })
    },
  },
}
</script>

<style>
</style>
