<template>
  <div class="card h-90 border-0 shadow rounded-md">
    <div class="card-img">
      <img
        id="image"
        :src="'https://image.tmdb.org/t/p/original' + item.poster_path"
        :alt="item.original_title"
        height="300"
        class="rounded-t-md card-img-top"
      />
    </div>
    <div class="card-body">
      <div class="card-title font-weight-bold">
        {{ item.original_title }}
      </div>
      <b-card-text>{{ item.overview.substr(0, 50) }} ...</b-card-text>
      <b-button class="btn btn-success btn-md mt-3 btn-block shadow-md">
        Add to watch list
      </b-button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['item'],
}
</script>

<style>
</style>
