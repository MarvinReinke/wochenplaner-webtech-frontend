<template>
  <div class="home">
    <HelloWorld msg="Willkommen bei WeePlan!"/>
     <img src="/src/assets/WeePlan_Logo.png" alt="WeePlanLogo">
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
