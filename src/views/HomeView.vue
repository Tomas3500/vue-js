<template>
  <div class="home">
    <add-user placeholder="add user" @add-user="addUser"></add-user>
    <list-users
      v-for="(item, index) in users"
      :key="item.id"
      :remove-user="index"
      :name="item.name"
      @remove-user="removeUser"
    >
    </list-users>
    <h2 v-if="users.length === 0">no users</h2>
  </div>
</template>

<script>
// @ is an alias to /src
import addUser from "@/components/addUser.vue";
import listUsers from "@/components/listUsers.vue";

export default {
  name: "addUsers",
  components: {
    addUser,
    listUsers,
  },
  data() {
    return {
      users: [
        {
          id: 1,
          name: "Alex",
          age: 20,
        },
        {
          id: 2,
          name: "Vasya",
          age: 23,
        },
        {
          id: 3,
          name: "Petya",
          age: 41,
        },
      ],
    };
  },

  methods: {
    addUser(event) {
      this.users.unshift({
        id: this.id,
        name: event.item,
      });
    },
    removeUser(event) {
      let index = this.users.findIndex((index) => index === event);
      this.users.splice(index, 1);
    },
  },
};
</script>
