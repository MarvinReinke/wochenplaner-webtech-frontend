<template>
  <h1>Hier findest du deine Einträge</h1>
  <div class="row row-cols-1 row-cols-md-2 g-4">
    <div class="col">
      <div class="col" v-for="entry in entries" :key="entry.id">
        <div class="card" style="margin-top: 50px">
          <div class="card-body">
            <h5 class="card-title">{{entry.name}}</h5>
            <p class="card-text">{{entry.beschreibung}}.</p>
            <p class="card-text">  Der Status dieser Aktivität befindet sich auf {{entry.status}}.
            Der Eintrag gehört zur folgenden Gruppe: {{entry.gruppe}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
  <entries-create-form></entries-create-form>
</template>

<script>
import EntriesCreateForm from '../components/createEntriesForm'

export default {
  name: 'Entries',
  components: { EntriesCreateForm },
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
    console.log(endpoint)
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
 .card {
   color: #000000;
   border-color: #42b983;
   width: 500px;
   margin-left: 700px;
 }
</style>
