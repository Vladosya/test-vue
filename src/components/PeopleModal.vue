<template>
  <div class="modalWrapper" v-if="showModal">
    <div class="profilePeople">
      <div class="profilePeople__block">
        <div class="profilePeople__top">
          <div class="profilePeople__header">Профиль пользователя:</div>
          <button class="profilePeople__exit list-group-item-action" @click="$emit('closeModal')">
            <img
              class="profilePeople__exit-img"
              src="../img/exit.png"
              alt="btn-exit"
            />
          </button>
        </div>
        <div class="profilePeople__personStatic">
          <button class="profilePeople__person-btn">
            <img
              class="profilePeople__person-img"
              src="../img/Avatar-3.png"
              alt="avatar-one-one"
            />
          </button>
          <div>
            <div class="profilePeople__person-info">Имя:</div>
            <div class="profilePeople__person-name">{{people[idxPeople].name}}</div>
            <div class="profilePeople__person-number">Баллы:</div>
            <div class="profilePeople__person-score">{{people[idxPeople].rating}}</div>
            <div class="profilePeople__person-ratingInfo">
              Позиция в рейтинге:
            </div>
            <div class="profilePeople__person-ratingPosition">{{idxPeople + 1}}</div>
          </div>
        </div>
        <div class="profilePeople__aboutPerson">
          <div class="profilePeople__about">О себе:</div>
          <div class="profilePeople__about-info">{{ people[idxPeople].description }}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['closeModal'],
  data () {
    return {
      showModal: this.openModal
    }
  },
  props: ['openModal', 'people', 'idxPeople']
}
</script>

<style scoped>

</style>
