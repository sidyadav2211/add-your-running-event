<template>
  <base-card>
    <base-button
      @click="handleTab('event-store')"
      :mode="isTabValue === 'event-store' ? null : 'flat'"
    >
      Stored Events</base-button
    >
    <base-button
      @click="handleTab('add-event')"
      :mode="isTabValue === 'add-event' ? null : 'flat'"
    >
      Add Event</base-button
    >
  </base-card>
  <keep-alive>
    <component :is="isTabValue" />
  </keep-alive>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import EventStore from './EventStore.vue';
import AddEvent from './AddEvent.vue';

export default {
  components: {
    BaseButton,
    EventStore,
    AddEvent,
  },
  data() {
    return {
      isTabValue: 'event-store',
      eventStoreData: [
        {
          id: '01',
          name: 'Tata Mumbai Marathon',
          type: 'Full',
          description: 'One of the best events in the india',
          link: 'https://tatamumbaimarathon.com',
        },
        {
          id: '02',
          name: 'Delhi Marathon',
          type: 'Half',
          description: 'To get your personal best',
          link: 'https://delhi.com',
        },
      ],
    };
  },
  provide() {
    return {
        eventStore: this.eventStoreData,
        addEventValue: this.addEventValue,
        deleteEvent: this.deleteEvent,

    }
  },
  methods: {
    handleTab(tab) {
      this.isTabValue = tab;
    },
    addEventValue(data){
        const payload={
            id:new Date().toISOString(),
            name: data.name,
            type: data.type,
            description: data.description,
            link: data.link,

        }
        this.eventStoreData.unshift(payload);
        this.isTabValue='event-store'
    },
    deleteEvent(id){
        const indexValue = this.eventStoreData.findIndex(item=> item.id===id);
        this.eventStoreData.splice(indexValue, 1);
    }
  },
};
</script>