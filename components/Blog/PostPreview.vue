<template>
  <nuxt-link :to="id">
    <article class="post-preview">
      <div
        :style="{ backgroundImage: 'url(' + thumbnailUrl + ')' }"
        class="post-preview-thumbnail"
      ></div>
      <div class="post-preview-content">
        <h3 class="post-preview-title">{{ title }}</h3>
        <div class="post-preview-text">{{ excerpt }}</div>
      </div>
    </article>
  </nuxt-link>
</template>

<script>
export default {
  name: 'PostPreview',
  props: {
    title: {
      type: String,
      required: true,
    },
    excerpt: {
      type: String,
      required: true,
    },
    thumbnailUrl: {
      type: String,
      required: true,
    },
    id: {
      type: String,
      required: true,
    },
  },
}
</script>

<style scoped>
.post-preview {
  border-radius: 3px;

  /* box-shadow: rgb(1px 1px 1px / 20%); */

  /* box-shadow: 12px 12px 2px 1px rgba(0, 0, 255, 20%); */

  box-shadow: rgb(12 122 231 / 20%);
  width: 90%;
  margin: auto;
  height: 20rem;
  background: rgb(212 244 207 / 50%);
}

.post-preview-thumbnail {
  background-position: center;
  background-size: cover;
  width: 100%;
  height: 10rem;
}

.post-preview-content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 1rem;
  text-align: center;
  color: green;
  line-height: 1.2;
}

.post-preview-title {
  font-weight: 600;
}

.post-preview-text {
  text-overflow: ellipsis;
  overflow: hidden;
  max-height: 6.6em;
  line-height: 1.35em;
}

@media (min-width: 35rem) {
  .post-preview {
    width: 25rem;
    margin: 1rem;
  }
}
</style>
