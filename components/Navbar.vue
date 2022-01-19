<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand class="font-weight-bold" href="/">
        <i class="baseline-invert_colors_off"></i>AJDev
      </b-navbar-brand>
      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item-dropdown>
            <template slot="button-content">
              <i class="fa fa-list-ul"></i> MOVIE
            </template>
            <div>
              <b-dropdown-item to="/top-rated">
                Top Rated Movies
              </b-dropdown-item>
              <b-dropdown-item to="/upcoming">
                Upcoming Movies
              </b-dropdown-item>
              <b-dropdown-item to="/now-playing">
                Now Playing Movies
              </b-dropdown-item>
              <b-dropdown-item to="/popular"> Populer Movies </b-dropdown-item>
            </div>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {}
</script>

<style>
</style>
