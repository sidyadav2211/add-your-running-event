<template>
  <ul>
    <li>
      <base-card>
        <header>
          <h1>{{ eventVal.name }}</h1>
          <base-button mode="flat" @click="handleDelete(eventVal.id)">Delete</base-button>
        </header>
        <p>{{ eventVal.description }}</p>
        <p style="margin: 10px 0">
          <strong>{{ eventVal.type }} {{ 'Marathon' }}</strong>
        </p>
        <nav>
          <a :href="eventVal.link" v-if="eventVal.link.length > 0">View Resource</a>
        </nav>
      </base-card>
    </li>
  </ul>
</template>
<script>
import BaseButton from '../UI/BaseButton.vue';
export default {
  components: {
    BaseButton,
  },
  inject: ['deleteEvent'],

  props: {
    eventVal: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {};
  },
  methods: {
    handleDelete(id) {
      this.deleteEvent(id);
      },
      },
};

</script>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>