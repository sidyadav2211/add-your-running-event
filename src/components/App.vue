<template>
  <the-header title="Events You Like To Do"></the-header>
  <the-event></the-event>
  <the-footer></the-footer>
</template>

<script>
import TheHeader from './layout/TheHeader.vue';
import TheFooter from './layout/TheFooter.vue';

import TheEvent from './Events/TheEvents.vue';
export default {
  components: {
    TheHeader,
   TheFooter,
    TheEvent,
  },
  data() {
    return {
     
    };
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>