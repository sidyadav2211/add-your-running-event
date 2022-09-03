<template>
    <base-dialog v-if="isDialog === true" title="Input Is Not Valid" @close="isDialog = false">
    <template #default>
        <p>Please provide enter event name and type</p>
    </template>
    <template #actions>
        <base-button @click="isDialog = false" > Okay </base-button>
    </template>
</base-dialog>
  <base-card>
    <form action="" @submit.prevent="handleSubmit">
      <div class="form-control">
        <label for="name">Event Name</label>
        <input
          type="text"
          name="name"
          id="name"
          placeholder="Please enter event name"
          ref="nameInput"
        />
      </div>
      <div class="form-control">
        <label for="type">Type</label>
        <input
          type="text"
          name="type"
          id="type"
          placehotype="Please enter event type full or half"
          ref="typeInput"
        />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          name="description"
          rows="3"
          placeholder="Please enter event description"
          ref="descriptionInput"
        />
      </div>
      <div class="form-control">
        <label for="link">Event Link</label>
        <input
          type="url"
          name="link"
          id="link"
          placeholder="Please enter event link"
          ref="linkInput"
        />
      </div>
      <div>
        <base-button type="submit">Add</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseDialog  from '../UI/BaseDialog.vue';
export default {
  components: {
    BaseButton,
    BaseDialog,
  },
  inject: ['addEventValue'],
  data() {
    return {
        isDialog:false,
    };
  },
  methods: {
    handleSubmit() {
      const data = {
      name : this.$refs.nameInput.value,
      type :this.$refs.typeInput.value,
      description : this.$refs.descriptionInput.value,
      link : this.$refs.linkInput.value,
      };
      if(this.$refs.nameInput.value === '' || this.$refs.typeInput.value ===''){
        this.isDialog = true
        return;
      }else{
        this.addEventValue(data);
        this.$refs.nameInput.value ='',
        this.$refs.typeInput.value ='';
        this.$refs.descriptionInput.value ='';
        this.$refs.linkInput.value ='';
      }
    },

  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}
input{
    padding: 0.50rem;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>