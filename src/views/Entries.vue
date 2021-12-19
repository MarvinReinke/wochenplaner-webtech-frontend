<template>
  <h1>Welcome to Entries</h1>
  <div class="row row-cols-1 row-cols-md-2 g-4">
    <div class="col">
      <div class="col" v-for="entry in entries" :key="entry.id">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">{{entry.name}}</h5>
            <p class="card-text">{{entry.beschreibung}} . Der Status dieser Aktivität befindet sich auf {{entry.status}}</p>
          </div>
        </div>
      </div>
<!--      <div class="card">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Card title</h5>
          <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
        </div>
      </div>
    </div>
    <div class="col">
      <div class="card">
        <img src="..." class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">Card title</h5>
          <p class="card-text">This is a longer card with supporting text below as a natural lead-in to additional content. This content is a little bit longer.</p>
        </div>
      </div>-->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Entries',
  data () {
    return {
      entries: []
    }
  },
  mounted () {
    const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/entries'
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }
    fetch(endpoint, requestOptions)
      .then(response => response.json())
      .then(result => result.forEach(entry => {
        this.entries.push(entry)
      }))
      .catch(error => console.log('error', error))
  }
}
</script>

<style scoped>

</style>
