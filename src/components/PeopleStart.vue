<template>

  <people-modal
    :openModal="openModal"
    :people="people"
    :idxPeople="idxPeople"
    @closeModal="openModal = false"
    v-if="openModal"
  ></people-modal>

  <div class="ratingPeople">
    <div class="ratingPeople__block">
      <div class="ratingPeople__top">
        <div class="ratingPeople__header">Рейтинг Пользователей:</div>
        <div class="ratingPeople__sort">
          <button class="ratingPeople__btn-one" @click="sortRat">
            <img
              class="ratingPeople__btn-img"
              src="../img/Vector.png"
              alt="btn-vector"
            />
          </button>
        </div>
      </div>
      <div>
        <div
          v-for="(person, index) in people"
          :key="person"
          class="ratingPeople__personStatic list-group-item-action"
          @click="openModalWindow(index)"
        >
          <button class="ratingPeople__person-btn">
            <img
              class="ratingPeople__person-img"
              :style="person.rating === 67 ? 'ratingPeople__person-img-yellow' :
              person.rating === 65 ? 'ratingPeople__person-img-gray' :
              person.rating === 60 ? 'ratingPeople__person-img-brown' : ''"
              :src="person.avatar"
              alt="avatar-one"
            />
          </button>
          <div class="ratingPeople__person-information">
            <div class="ratingPeople__person-info">Пользователь:</div>
            <div class="ratingPeople__person-name">{{person.name}}</div>
          </div>
          <div class="ratingPeople__person-rating">
            <img
              class="ratingPeople__person-star"
              src="../img/star.png"
              alt="star-one"
            />
            <p class="ratingPeople__person-numberRat">{{ person.rating }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PeopleModal from '@/components/PeopleModal'

export default {
  data () {
    return {
      sortRating: this.sortByRating,
      openModal: false,
      idxPeople: ''
    }
  },
  props: ['people', 'sortByHigh', 'sortByLow', 'sortByRating'],
  methods: {
    sortRat () {
      if (!this.sortRating) {
        this.sortRating = true
        this.sortByLow()
      } else {
        this.sortRating = false
        this.sortByHigh()
      }
    },
    openModalWindow (idx) {
      console.log('this.people', this.people)
      this.idxPeople = idx
      this.openModal = true
    }
  },
  components: {
    PeopleModal
  }
}
</script>

<style scoped>

</style>
