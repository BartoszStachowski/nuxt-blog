<template>
  <form @submit.prevent="onSave">
    <AppControlInput v-model="editPost.author">Author Name</AppControlInput>
    <AppControlInput v-model="editPost.title">Title</AppControlInput>
    <AppControlInput v-model="editPost.thumbnail">Thumbnail url</AppControlInput>
    <AppControlInput
      control-type="textarea"
      v-model="editPost.content">Content
    </AppControlInput>
    <AppControlInput
      control-type="textarea"
      v-model="editPost.previewText">Preview Text
    </AppControlInput>
    <AppButton type="submit">Save</AppButton>
    <AppButton
      type="button"
      style="margin-left: 10px"
      btn-style="cancel"
      @click="onCancel">Cancel
    </AppButton>
  </form>
</template>

<script>
export default {
  name: "AdminPostForm",
  props: {
    post: {
      type: Object,
      required: false,
    }
  },
  data() {
    return {
      editPost: this.post ? { ...this.post } : {
        author: '',
        title: '',
        thumbnail: '',
        content: '',
        previewText: ''
      }
    }
  },
  methods: {
    onSave() {
      this.$emit('submit', this.editPost)
    },
    onCancel() {
      this.$router.push('/admin');
    }
  }
}
</script>

<style scoped>

</style>
