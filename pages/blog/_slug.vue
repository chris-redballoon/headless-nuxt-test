<script>
export default {
computed: {
  posts() {
    return this.$store.state.posts;
  },
  post() {
    return this.posts.find(el => el.slug === this.slug);
  }
},
created() {
  this.$store.dispatch("getPosts");
},
data() {
  return {
    slug: this.$route.params.slug
  };
}
};
</script>

<template>
<main class="post individual">
  <h1>{{ post.title.rendered }}</h1>
  <section v-html="post.content.rendered"></section>
</main>
</template>