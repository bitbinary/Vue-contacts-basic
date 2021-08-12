<template>
  <div class="hello">
    <h1>{{ msg1 || 'Contacts' }}</h1>
    <ContactList v-bind:users="users" :editable="false" />
    <h1>{{ msg2 || 'Editable Contacts' }}</h1>
    <ContactList
      v-bind:users="users"
      :editable="true"
      :updateContactDetails="updateContactDetails"
    />
  </div>
</template>

<script>
import ContactList from './ContactList.vue';
import { getUsers } from '../services/userClient';

export default {
  name: 'HelloWorld',
  data() {
    return {
      users: [],
    };
  },
  methods: {
    updateContactDetails({ type, id, value }) {
      this.users = this.users.map((user) => {
        if (user.id === id) {
          let updatedUser = { ...user };
          updatedUser[type] = value;
          return updatedUser;
        } else {
          return user;
        }
      });
    },
  },
  props: {
    msg1: String,
    msg2: String,
  },
  components: {
    ContactList,
  },
  created: function() {
    getUsers().then((res) => {
      this.users = res;
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin: 40px 0 10px;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
