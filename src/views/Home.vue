<template>
  <div class="home">
    <Select />
  </div>
</template>

<script>
// @ is an alias to /src
import Select from '@/components/Select.vue'

export default {
  name: 'Home',
  components: {
    Select
  }
}
</script>
<style scoped>
  .home{
    max-width: 1200px;
    margin: auto;
    text-align: center;
  }
</style>