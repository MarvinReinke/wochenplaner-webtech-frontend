<template>
  <div class="home">
    <HelloWorld msg="Willkommen bei WeePlan!"/>
    <h1> klicke auf den Button um einen neuen Wochenplan zu erstellen</h1>
    <img src="src/assets/WeePlan_Logo.png" alt="WeePlanLogo">
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld
  }
}
</script>

<style scoped>
</style>
