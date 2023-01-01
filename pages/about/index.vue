<template>
  <section class="about-page">
    <h2>Hello everyone, it is test app</h2>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Ad perferendis
      omnis hic dolorum modi incidunt doloribus pariatur delectus. Minus ipsam
      corrupti a aperiam blanditiis veniam, accusamus nesciunt ut dolorem
      obcaecati!
    </p>
  </section>
</template>

<script>
export default {
  asyncData (context) {
    return context.app.$storyapi
      .get('cdn/stories/about', {
        version: context.isDev ? 'draft' : 'published'
      })
      .then((res) => {
        return {
          blok: res.data.story.content,
          title: res.data.story.content.title,
          content: res.data.story.content.content
        }
      })
  },
  mounted () {
    this.$storyblok.init()
    this.$storyblok.on('change', () => {
      location.reload(true)
    })
  }
}
</script>

<style>
#about-page {
  width: 80%;
  max-width: 500px;
  margin: auto;
}

#about-page p {
  white-space: pre-line;
}
</style>
