<template>
  <div class="container column">
    <app-form @block-added="addBlock"></app-form>
    <app-view :blocks="blocks"></app-view>
  </div>
  <div class="container">
    <app-loader v-if="loading"></app-loader>
    <app-comments
      v-else
      :comments="comments"
      @load-comments="loadComments"
    ></app-comments>
  </div>
</template>

<script>
import AppView from './components/AppView.vue'
import AppLoader from './components/AppLoader'
import AppForm from './components/AppForm'
import AppComments from './components/AppComments'

export default {
  data () {
    return {
      blocks: [],
      loading: false,
      comments: []
    }
  },
  methods: {
    async loadComments () {
      this.loading = true
      const result = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await result.json()
      this.loading = false
    },
    addBlock (block) {
      this.blocks.push(block)
    }
  },
  components: { AppView, AppLoader, AppForm, AppComments },
  created () {
    document.title = 'Summary'
  }
}
</script>
