<template>
  <div>
    <Navbar />
    <SectionMovie title="Top Rated" url="/top-rated" />
    <SectionMovie title="Popular" url="/popular" />
    <SectionMovie title="Upcoming" url="/upcoming" />
    <SectionMovie title="Now Playing" url="/now-playing" />
    <Footer />
  </div>
</template>

<script>
import Footer from '~/components/Footer.vue'
import Navbar from '~/components/Navbar.vue'
export default {
  components: { Footer, Navbar },
}
</script>
