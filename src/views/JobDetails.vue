<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>{{ job.details }}</p>
  </div>
  <div v-else>
    <p>Loading</p>
  </div>
</template>

<script>
export default {
    props: ['id'],
    data(){
        return {
            job : null
        }
    },
    async mounted(){
      const res = await fetch(`http://localhost:3000/jobs/${this.id}`)
      this.job = await res.json()
    }
}
</script>

<style>

</style>