<template>
  <div>
    <h1>{{ planet.title }}</h1>

    <img :src="planet.image" />

    <pre>{{ planet }}</pre>

    <nuxt-link to="/">home</nuxt-link>
  </div>
</template>

<script>
export default {
  async asyncData({ params }) {
    const planet = await fetch(`https://api.nuxtjs.dev/planets/${ params.slug }`).then((res) => {
      if (res.ok) {
        return res.json()
      }

      throw new Error(res.status)
    })

    return { planet }
    
  },
}
</script>

<style scoped>
  img {
    width: 80px !important;
    height: 80px;
  }
</style>
