<template>
  <div class="list_users">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-5">
          <hr />
          <div class="input-group mb-3">
            <input
              type="text"
              class="form-control"
              v-model="carentName"
              v-bind:placeholder="placeholder"
              aria-label="Recipient's username"
              aria-describedby="basic-addon2"
            />
            <button type="button" class="btn btn-outline-primary">edit</button>
            <button
              type="button"
              class="btn btn-outline-danger"
              v-on:click="removeUser(index)"
            >
              delete
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "listUsers",
  props: ["placeholder", "name"],
  data() {
    return {
      input: "",
      carentName: "",
      index: {
        type: Number,
      },
    };
  },

  methods: {
    removeUser(index) {
      this.$emit("remove-user", index);
    },
  },

  created() {
    this.carentName = this.name;
  },
};
</script>