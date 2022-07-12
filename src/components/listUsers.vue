<template>
  <div class="list_users">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-5">
          <hr />
          <div class="input-group mb-3">
            <input
              :disabled="!isEditing"
              type="text"
              class="form-control"
              v-model="carentName"
              aria-label="Recipient's username"
              aria-describedby="basic-addon2"
            />
            <button
              type="button"
              class="btn btn-outline-primary"
              v-on:click="editName(carentName)"
            >
              edit
            </button>
            <button
              type="button"
              class="btn btn-outline-danger"
              v-on:click="removeUser(index)"
            >
              delete
            </button>
            <button
              v-if="isEditing"
              type="button"
              class="btn btn-dark"
              v-on:click="saveName()"
            >
              save
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
  props: ["name"],
  data() {
    return {
      isEditing: false,
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

    editName() {
      this.isEditing = true;
    },

    saveName() {
      this.isEditing = false;
    },
  },

  created() {
    this.carentName = this.name;
  },
};
</script>