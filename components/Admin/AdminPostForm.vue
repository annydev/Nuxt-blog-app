<template>
    <form @submit.prevent="onSave">
        <AppControlInput
            v-model="editedPost.author"
          >Author Name</AppControlInput
        >
        <AppControlInput v-model="editedPost.title">Title</AppControlInput>
        <AppControlInput
            v-model="editedPost.thumbnail"
          >Thumbnail Link</AppControlInput
        >
        <AppControlInput
            v-model="editedPost.previewText"
          >PreviewText</AppControlInput
        >
        <AppControlInput
            v-model="editedPost.content"
             control-type="textarea"
          >Content</AppControlInput
        >
        <AppButton type="submit">Save</AppButton>
        <AppButton
          type="button"
          style="margin-left: 10px"
          btn-style="cancel"
          @click="onCancel"
          >Cancel</AppButton
        >
      </form>
</template>

<script>

export default {
  props: {
    // eslint-disable-next-line vue/require-default-prop
    post: {
      type: Object,
      required: false
    }
  },
  data () {
    return {
      editedPost: this.post ? {...this.post} : {
        author: '',
        title: '',
        thumbnail: '',
        content: '',
        previewText: ''
      }
    }
  },
  methods: {
    onSave () {
      // Save the post
      // eslint-disable-next-line no-console
      console.log(this.editedPost);
      this.$emit('submit', this.editedPost)
      this.$router.push("/")
    },
    onCancel () {
      // Navigate back
      this.$router.push('/admin')
    }
  }
}
</script>
