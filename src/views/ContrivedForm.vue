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
        <b-form-textarea id="message" v-model="message" rows="6" max-rows="8"></b-form-textarea>
      </b-form-group>
      <div class="input-section">
        <b-form-checkbox id="delete-checkbox" v-model="deleted" name="delete-checkbox">
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
import axios from 'axios';
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
        //TODO validate data
        let reqBody = {
            name: this.name,
            email: this.email,
            message: this.message,
            deleted: this.deleted
        }
        this.sendData(reqBody);
    },
    async sendData(reqBody){
        //Call POST API with the form data and show modal on Success
        try{
            //Check if atleast name and email are entered before calling API
            if(this.name && this.email){
                const response = await axios.post('https://00dbbb1f-643b-43ed-be1e-ccfe0ab05b32.mock.pstmn.io/user', reqBody);
                if(response && response.data && response.data.success)
                    this.$bvModal.msgBoxOk('We received your message and will respond accordingly',{
                        title: 'We read you load and clear',
                        okTitle: 'Take me home, country road'
                    })
                    .then(value =>{
                        //Redirect to Home 
                        if(value) this.$router.push({ name: 'Home' });
                    })
                    .catch(err => {
                        console.log(err)
                    })
            }     
        }  
        catch(err){
            console.log(err);
        }
      
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
