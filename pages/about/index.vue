<template>
  <section v-editable="blok" class="about-page">
    <h2 class="about-title">{{ title }}</h2>
    <p>
      {{ content }}
    </p>
  </section>
</template>

<script>
export default {
  name: 'AboutPage',
  asyncData(context) {
    return context.app.$storyapi
      .get('cdn/stories', {
        version: context.isDev ? 'draft' : 'published',
        starts_with: 'about/',
      })
      .then((res) => {
        return {
          blok: res.data.stories[0].content,
          title: res.data.stories[0].content.title,
          content: res.data.stories[0].content.text,
        }
      })
  },
  mounted(){
    this.$storyblok.init()
    this.$storyblok.on('change', ()=>{
      location.reload(true)
    })
  }
}
</script>

<style scoped>
.about-page {
  padding: 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.about-title {
  font-weight: 700;
  font-size: 24px;
  text-align: center;
  margin-bottom: 20px;
}
</style>
