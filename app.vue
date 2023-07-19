<template>
  <div>
    <h1>Hello Narhwal Web</h1>
    <div v-for="hero in data?.data">
      <h2>Name: {{ hero.attributes.HeroName }}</h2>
      <h3>Civil name: {{ hero.attributes.RealName }}</h3>
      <img v-bind:src="hero.attributes.Picture.data.attributes.url" />
    </div>
  </div>
</template>

<script setup lang="ts">
  import type { Hero } from '~/types'
  const { find } = useStrapi()

  const { data, pending, refresh, error } = await useAsyncData(
    'heroes',
    () => find<Hero>('heroes', {
            populate: '*',
          })
  )
</script>
