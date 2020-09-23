<template>
  <div class="container mt-3">
    <h3 class="title">Contrived Form</h3>
    <b-form @submit="submitForm">
      <b-form-group label="Name" label-for="name">
        <b-form-input v-model="name" type="text"></b-form-input>
      </b-form-group>
      <b-form-group label="Email" label-for="email">
        <b-form-input v-model="email" type="email"></b-form-input>
      </b-form-group>
      <b-form-group label="Message" label-for="message">
        <b-form-textarea
          id="message"
          v-model="message"
          rows="6"
          max-rows="8"
        ></b-form-textarea>
      </b-form-group>
      <div class="input-section">
        <b-form-checkbox
          id="delete-checkbox"
          v-model="deleted"
          name="delete-checkbox"
        >
          Delete my account
        </b-form-checkbox>
      </div>
      <div>
        <b-button id="send-button" type="submit" variant="primary">Send</b-button>
      </div>
    </b-form>
  </div>
</template>

<script>
export default {
  name: 'ContrivedForm',
  data(){
    return{
      name: '',
      email: '',
      message: '',
      deleted: false
    }
  },
  methods: {
    submitForm(e){
      e.preventDefault();
    }
  }
}
</script>

<style scoped>
.title{
  margin: 25px 0px 25px 0px;
  font-weight: 700;
}
.input-section{
  margin-bottom: 10px;
}
#send-button{
  width: 100%;
}
.container{
  width: 60%;
}

@media screen and (max-width: 468px) {
  .container{
    width: 100%;
  }
}
</style>
