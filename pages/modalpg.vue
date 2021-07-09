<template>
    <div class="modal-con">
      
        <DcModal size="sm">
            <b-form @submit="handleSubmit">
                <b-form-input v-model="testform.firstname" placeholder="enter firstname"></b-form-input>
                <b-form-input v-model="testform.lastname" placeholder="enter lastname"></b-form-input>
                <b-button variant="info" block type="submit">Submit</b-button>
            </b-form>
        </DcModal>
        <br>
        <br>
        <DcModal 
          mode="form"
          :formFields="formFields"
        />

    </div>
</template>

<script>
import DcModal from '../components/modal.vue'
export default {
  components: { DcModal },
  data(){
      return{
          variants: ['primary', 'secondary', 'success', 'warning', 'danger', 'info', 'light', 'dark'],
          formFields:['firstname', 'lastname', 'phone',  'email', ],

          testform:{
              firstname:'',
              lastname:''
          },
          demo:[
              {firstname:''},
              {lastname:''},
          ]
        
      }
  },
  methods:{
      handleSubmit(e){
          e.preventDefault();
          console.warn(this.testform)
      }
  }
    
}
</script>

<style scoped>
.modal-con{
    margin: 20px 20px 20px 20px;
}
</style>