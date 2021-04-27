<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">Current Roster for TEAM SKYNITE</h1>
      <posts post-type="roster" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts
    try {
      posts = await $content('roster').fetch()
    } catch (e) {
      error({ message: 'Roster not found' })
    }
    return { posts }
  }
}
</script>
