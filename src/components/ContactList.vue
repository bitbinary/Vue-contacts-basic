<template>
  <div class="container">
    <table class="table">
      <TableHead />
      <tbody>
        <tr v-for="user in users.slice(0, 2)" v-bind:key="user.id">
          <Contact
            :user="user"
            :editable="editable"
            :handleChange="detailsChange"
          />
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Contact from './Contact.vue';
import TableHead from './TableHead.vue';
export default {
  components: { Contact, TableHead },
  name: 'ContactList',
  methods: {
    detailsChange(newDetails) {
      this.updateContactDetails(newDetails);
    },
  },
  props: {
    users: {
      type: Array,
    },
    editable: {
      type: Boolean,
    },
    updateContactDetails: {
      type: Function,
    },
  },
};
</script>
