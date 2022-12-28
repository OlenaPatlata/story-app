<template>
  <section id="posts">
    <PostPreview
      v-for="post in posts"
      :id="post.id"
      :key="post.id"
      :title="post.title"
      :excerpt="post.previewText"
      :thumbnail-url="post.thumbnailUrl"
    />
  </section>
</template>

<script>
import PostPreview from '../components/Blog/PostPreview.vue'
export default {
  name: 'IndexPage',
  components: {
    PostPreview,
  },
  data() {
    return {
      posts: [
        {
          title: 'Sweet potato, salmon and corn fritters',
          previewText:
            'A belly-friendly, low-FODMAP fritter recipe, packed full of flavour and quick to make in just 20 minutes. With 2 ½ serves of vegetables, these vegetable fritters make a healthy brunch, dinner or light supper. Plus, they are high in calcium and protein and can be made gluten free. A belly-friendly, low-FODMAP fritter recipe, packed full of flavour and quick to make in just 20 minutes. With 2 ½ serves of vegetables, these vegetable fritters make a healthy brunch, dinner or light supper. Plus, they are high in calcium and protein and can be made gluten free',
          thumbnailUrl:
            'https://media.healthyfood.com/wp-content/uploads/2016/11/Kumara-salmon-and-corn-fritters-1-1024x665.jpg',
          id: 'a-new-beginning',
        },
        {
          title: 'Chicken pot pies',
          previewText:
            'Sink your teeth into a hearty chicken pie. This healthy pie recipe is so easy to make and takes just 35 minutes. High in fibre, diabetes-friendly and so delicious, this will quickly become a family favourite. Plus it freezes well so you can make an extra one for later.',
          thumbnailUrl:
            'https://media.healthyfood.com/wp-content/uploads/2016/11/Chicken-pot-pies-1-1024x672.jpg',
          id: 'a-second-beginning',
        },
      ],
    }
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
