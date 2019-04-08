<template>
  <div id="app">
    <img src="./assets/logo.png">
    <div class="event" v-for="d in events" v-bind:key=d.event_id>
      <p>Name: <span>{{d.event_name}}</span></p>
      <p>Description: <span>{{d.event_desc}}</span></p>
      <p>Date: <span>{{d.event_date}}</span></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
    return {
      events: []
    }
  },
  methods: {
    fetchData: function () {
      fetch('http://localhost:8000/events/Kingswood')
        .then((response) => { return response.json() })
        .then((data) => {
          this.events = data
        }).catch(error => { console.log(error) })
    }
  },
  created () {
    this.fetchData()
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<style scoped>
  .event {border: 1px solid gray;}
</style>
