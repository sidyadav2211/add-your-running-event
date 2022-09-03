<template>
  <ul>

    <event-list
      v-for="(res, i) in eventStore" :key="i"
      :event-val="res"
    ></event-list>
  </ul>
</template>

<script>
import EventList from './EventList.vue';

export default {
  components: {
    EventList,
  },
  inject: ['eventStore'],
};
</script>
<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  margin: auto;
  max-width: 40rem;
}
</style>