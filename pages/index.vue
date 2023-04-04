<template>
  <div>
    <ul v-for="mountain in mountains" :key="mountain.id">
      <NuxtLink :to="`${mountain.continent.toLowerCase()}/${mountain.slug}`">
        <li>{{ mountain.title }}</li>
      </NuxtLink>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData() {
    const mountains = await fetch(
      'https://foodtoken.club/mountains.php',{mode: "cors"}
    ).then((res) => res.json())

    return { mountains }
  }
}
</script>
