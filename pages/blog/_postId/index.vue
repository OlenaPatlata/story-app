<template>
  <section v-editable="blok" class="post" >
    <div
      :style="{ backgroundImage: 'url(' + thumbnailUrl + ')' }"
      class="post-thumbnail"
    ></div>
    <div class="post-content">
      <h3 class="post-title">{{ title }}</h3>
      <p class="post-text">{{ text }}</p>
      <h3 class="post-title">Instructions</h3>
      <div class="post-instructions">{{ instructions }}</div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Post',
  asyncData(context) {
    return context.app.$storyapi
      .get('cdn/stories/blog/' + context.params.postId, {
        version: context.isDev ? 'draft' : 'published',
      })
      .then((res) => {
        return {
          blok: res.data.story.content,
          thumbnailUrl: res.data.story.content.thumbnail,
          title: res.data.story.content.title,
          text: res.data.story.content.text,
          instructions: res.data.story.content.instructions,
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
.post {
  border-radius: 3px;
  box-shadow: rgb(12 122 231 / 20%);
  width: 100%;
  padding-left: 30px;
  padding-right: 30px;
  margin: auto;
  background: rgb(212 244 207 / 50%);
}

.post-thumbnail {
  background-position: center;
  background-size: cover;
  width: 100%;
  height: 10rem;
}

.post-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  text-align: center;
  color: green;
  line-height: 1.2;
}

.post-title {
  font-weight: 600;
  margin-bottom: 1rem;
}

.post-text {
  white-space: pre-line;
  text-overflow: ellipsis;
  overflow: hidden;
  max-height: 6.6em;
  line-height: 1.35em;
  margin-bottom: 1rem;
}

.post-instructions {
  white-space: pre-line;
  text-overflow: ellipsis;
  overflow: hidden;
  line-height: 1.35em;
  text-align: left;
}

/* @media (min-width: 35rem) {
  .post {
    width: 25rem;
    margin: 1rem;
  }
} */
</style>
