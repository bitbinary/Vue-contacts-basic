<template lang="">
  <th>{{ user.id }}</th>
  <td>{{ user.name }}</td>
  <td>{{ user.email }}</td>
  <td>{{ user.address.city }}</td>
</template>
<script>
export default {
  name: 'ContactRow',
  props: {
    user: {
      type: Object,
    },
  },
};
</script>
<style lang=""></style>
