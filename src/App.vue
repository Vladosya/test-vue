<template>
  <people-start
  :people="people"
  :sortByHigh="sortByHigh"
  :sortByLow="sortByLow"
  :sortByRating="sortByRating"
  ></people-start>
</template>

<script>
import axios from 'axios'
import PeopleStart from '@/components/PeopleStart'

export default {
  data () {
    return {
      people: [],
      order: 1,
      sortByRating: false
    }
  },
  mounted () {
    this.getPerson()
  },
  methods: {
    getPerson () {
      axios.get('https://my-json-server.typicode.com/Vespand/crmm-tasks/users').then(({ data }) => {
        data.map((p) => {
          this.people.push({
            id: p.id,
            name: p.name,
            description: p.description,
            avatar: p.avatar,
            rating: p.rating
          })
          this.sortByHigh()
        })
      })
    },
    sortByLow () {
      const order = this.order
      return this.people.sort((a, b) => {
        return (a.rating - b.rating) * order
      })
    },
    sortByHigh () {
      const order = this.order
      return this.people.sort((a, b) => {
        return (b.rating - a.rating) * order
      })
    }
  },
  components: {
    PeopleStart
  }
}
</script>

<style scoped>

</style>
