<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'app-' + block.type"
        v-bind="{value: block.value}"
      >
      </component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import AppAvatar from './parts/AppAvatar'
import AppSubtitle from './parts/AppSubtitle'
import AppText from './parts/AppText'
import AppTitle from './parts/AppTitle'
export default {
  props: ['blocks'],
  components: { AppAvatar, AppSubtitle, AppText, AppTitle }
}
</script>
<style coped>
  h3{
    text-align: center;
  }
</style>>
