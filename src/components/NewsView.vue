<template>
  <p>{{ description }}</p>
</template>

<script>
  export default {
    name: 'NewsView',
    props: {
      title: String,
      description: String,
      url: String,
      urlToImage: String,
    },
    data: () => ({}),
  }
</script>
