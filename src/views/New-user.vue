<template>
  <div class="about">
    <h1>Add New User</h1>
    <NewUserFrm />
  </div>
</template>
<script>
import NewUserFrm from '@/components/NewUserFrm.vue'
export default {
  name:'NewUser',
  components:{
    NewUserFrm
  }
}
</script>
