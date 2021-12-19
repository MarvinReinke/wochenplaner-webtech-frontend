<template>
  <div class="home">
    <img alt="Vue Logo" src="src/assets/WeePLan_Logo.png">
    <HelloWorld msg="Willkommen bei WeePlan!"/>
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
