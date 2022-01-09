<template>
  <button class="btn btn-primary" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasRight" aria-controls="offcanvasRight">Neuen Eintrag erstellen</button>

  <div class="offcanvas offcanvas-end" tabindex="-1" id="offcanvasRight" aria-labelledby="offcanvasRightLabel">
    <div class="offcanvas-header">
      <h5 id="offcanvasRightLabel">Neuen Eintrag erstellen</h5>
      <button type="button" class="btn-close text-reset" data-bs-dismiss="offcanvas" aria-label="Close"></button>
    </div>
    <div class="offcanvas-body">
      <form class="text-start">
        <div class="mb-3">
          <label for="Bezeichnung" class="form-label">Bezeichnung</label>
          <input type="text" class="form-control" id="bezeichnung" v-model="name" required>
        </div>
        <div class="mb-3">
          <label for="Beschreibung" class="form-label">Beschreibung</label>
          <input type="text" class="form-control" id="beschreibung" v-model="beschreibung" required>
        </div>
        <div class="mb-3">
          <label for="Status" class="form-label">Status</label>
          <select id="Status" class="form-select" v-model="status" required>
            <option value="aktiv"> aktiv </option>
            <option value="abgeschlossen"> abgeschlossen </option>
          </select>
        </div>
        <div class="mb-3">
          <label for="Gruppe" class="form-label">Zu welcher Gruppe gehört dein Eintrag?</label>
          <select id="Gruppe" class="form-select" v-model="Gruppe" required>
            <option value="Modul"> Modul </option>
            <option value="Sport"> Sport </option>
            <option value="Freizeit"> Freizeit </option>
          </select>
        </div>
        <div class="mt-5">
          <button type="submit" class="btn btn-primary" @click="createEntry">erstellen</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EntriesCreateForm',
  data () {
    return {
      name: '',
      beschreibung: '',
      status: '',
      gruppe: ''
    }
  },
  methods: {
    createEntry () {
      const endpoint = process.env.VUE_APP_BACKEND_BASE_URL + '/api/v1/entries'

      const headers = new Headers()
      headers.append('Content-Type', 'application/json')

      const payload = JSON.stringify({
        name: this.name,
        beschreibung: this.beschreibung,
        status: this.status,
        gruppe: this.gruppe
      })

      const requestOptions = {
        method: 'POST',
        headers: headers,
        body: payload,
        redirect: 'follow'
      }

      fetch(endpoint, requestOptions)
        .catch(error => console.log('error', error))
    }
  }
}
</script>

<style scoped>
.btn-primary{
  margin-top: 50px;
}
</style>
