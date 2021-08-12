<template lang="">
  <ContactRow :user="user" v-if="!editable" />
  <ContactRowEditable
    :user="user"
    v-if="editable"
    :updateContact="updateContact"
  />
</template>
<script>
import ContactRow from './ContactRow.vue';
import ContactRowEditable from './ContactRowEditable.vue';
export default {
  name: 'Contact',
  components: {
    ContactRow,
    ContactRowEditable,
  },
  methods: {
    updateContact(newDetails) {
      this.handleChange(newDetails);
    },
  },
  props: {
    user: Object,
    editable: Boolean,
    handleChange: Function,
  },
};
</script>
<style lang=""></style>
