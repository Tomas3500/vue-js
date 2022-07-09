<!-- add_users -->
<template>
  <div class="add_users">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-5">
          <h3>Please add user</h3>
          <hr>
          <div class="input-group mb-3">
            <input type="text" class="form-control" v-model="inputValue"
                   :placeholder="placeholder"
                   aria-label="Recipient's username" aria-describedby="basic-addon2">
            <button type="button" @click="addUser" class="btn btn-outline-dark">add</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {

  name: 'addUser',
  props: ['placeholder'],
  data() {
    return {
      inputValue: '',
    }
  },
  methods: {

    addUser() {
      if (this.inputValue !== '') {
        this.$emit('add-user', {item: this.inputValue.trim()});
        this.inputValue = '';
      }
    },

  },

  watch: {
    inputValue(sting) {
      if (sting.length > 20) {
        this.inputValue = '';
      }
    }
  }

}
</script>