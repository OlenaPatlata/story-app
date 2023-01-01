<template>
  <section id="posts">
    <PostPreview
      v-for="post in posts"
      :id="post.id"
      :key="post.id"
      :title="post.title"
      :excerpt="post.excerpt"
      :thumbnail-url="post.thumbnailUrl"
    />
  </section>
</template>

<script>
import PostPreview from '@/components/blog/PostPreview.vue'
export default {
  name: 'IndexPage',
  components: {
    PostPreview,
  },
  asyncData(context) {
    // // This what would we do in real project
    // const version = context.query._storyblok || context.isDev ? 'draft' : 'published'
    // const fullSlug = (context.route.path == '/' || context.route.path == '') ? 'home' : context.route.path

    // Load the JSON from the API - loadig the home content (index page)
    return context.app.$storyapi
      .get('cdn/stories', {
        version: context.isDev ? 'draft' : 'published',
        starts_with: 'blog/',
      })
      .then((res) => {
        // eslint-disable-next-line no-console
        console.log(res.data.stories)
        return {
          posts: res.data.stories.map((story) => {
            return {
              id: story.slug,
              title: story.content.title,
              excerpt: story.content.summary,
              thumbnailUrl: story.content.thumbnail,
            }
          }),
        }
      })
      .catch((res) => {
        if (!res.response) {
          // eslint-disable-next-line no-console
          console.error(res)
          // eslint-disable-next-line no-console
          context.error({
            statusCode: 404,
            message: 'Failed to receive content form api',
          })
        } else {
          context.error({
            statusCode: res.response.status,
            message: res.response.data,
          })
        }
      })
  },
}
</script>

<style scoped>
#posts {
  display: flex;
  flex-direction: column;
  padding-top: 1rem;
  justify-content: center;
  align-items: center;
}

@media (min-width: 35rem) {
  #posts {
    flex-direction: row;
  }
}
</style>
