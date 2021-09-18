<template>
  <div>
    <h1>Home</h1>
    <nuxt-link to="/about">about</nuxt-link>

    <p v-if="$fetchState.pending">Fetching planets...</p>
    <p v-else-if="$fetchState.error">Error while fetching planets ...</p>
    <ul v-else>
      <li>
        <nuxt-link to="/nuxt">Nuxt</nuxt-link>
      </li>
      <li v-for="planet in planets" :key="planet.id">
        <nuxt-link :to="planet.slug">{{ planet.title }}</nuxt-link>
      </li>
    </ul>

    <pre>{{ $data }}</pre>
  </div>
</template>

<script>
export default {
  data() {
    return {
      planets: []
    }
  },

  async fetch() {
    this.planets = await fetch("https://api.nuxtjs.dev/planets").then((res) => res.json());
  },
}
</script>
