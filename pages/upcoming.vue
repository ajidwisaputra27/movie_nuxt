<template>
  <div>
    <Navbar />
    <div class="container menu">
      <div class="row">
        <div class="col">
          <h2>
            Movie
            <strong>Upcoming</strong>
          </h2>
        </div>
      </div>

      <div class="row mt-5">
        <div class="col-md-12 mb-5">
          <input
            type="text"
            placeholder="Find Your Favorite Movie..."
            v-model="search"
            class="form-control search"
          />
        </div>
      </div>

      <div class="row mb-5">
        <template v-if="loading">
          <div class="col-12 col-md-3 mt-4" v-for="p in 8" :key="p">
            <content-placeholders rounded>
              <content-placeholders-img />
              <content-placeholders-text :lines="3" />
            </content-placeholders>
          </div>
        </template>
        <template v-else-if="resultQuery.length == 0">
          <div class="col-md-6 offset-3 text-center">
            <img src="/empty.svg" width="100%" alt="" />
            <h2>Movie Not Found!</h2>
          </div>
        </template>
        <template v-else>
          <div
            class="col-12 col-md-3 mb-4"
            v-for="item in resultQuery"
            :key="item.id"
          >
            <CardMovie :item="item" />
          </div>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      search: '',
      loading: false,
    }
  },
  created() {
    this.createItems()
  },
  computed: {
    resultQuery() {
      if (this.search) {
        return this.items.filter((item) => {
          return this.search
            .toLowerCase()
            .split(' ')
            .every((v) => item.original_title.toLowerCase().includes(v))
        })
      } else {
        return this.items
      }
    },
  },
  methods: {
    createItems() {
      this.loading = true
      this.$axios
        .get(
          '/movie/upcoming?api_key=5f49291f3aa8ba5ccb190a5ee78f2569&language=en-US&page=1'
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
.menu {
  padding-top: 50px;
}
.search {
  border-radius: 20px;
}
</style>
