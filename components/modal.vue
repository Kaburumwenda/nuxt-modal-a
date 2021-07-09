<template>
  <div>
    <b-button
      @click="showModal"
      id="show-btn" 
      :disabled="disabled"
      :variant="lbTheme"
      :pill="pill"
      :squared="squared"
      >{{ label }}
      </b-button>
      <!-- <p>v-b-modal.modal-scrollable </p> -->
      <!-- <p>@click="showModal"</p> -->
<!-- <p>id="modal-scrollable"</p> -->
    <b-modal  scrollable ref="my-modal" hide-footer 
       :title="title"
       :size="size"
       :id="'modal-'+effect"
       >
      <b-container fluid>
          <div class="d-block text-left">
                <div v-if="mode === 'form'">
                    <b-form @submit="formSubmit">
                    <div>
                        <b-row v-for="rs in formFields" :key="rs">
                            <b-col cols="3"><label class="form-label">{{rs}}</label></b-col>
                            <b-col cols="9">
                                <b-form-input class="form-input" type="text" :v-model="rs" :placeholder="'Enter ' + rs">
                                    </b-form-input></b-col>
                        </b-row>
            
                    </div>
                    <br>
                    <!-- <b-form-select
                    v-model="formSelectItem"
                    :options="formSelect"
                    ></b-form-select> -->
                    <b-button class="mt-3" :variant="sbTheme" :block="sbBlock" :type="sbType">{{ sbTitle }}</b-button>
                    </b-form>                             
                </div>

                <div v-else-if="mode==='custom'">
                    <slot> 
                        <p style="color:orange">Design form fields</p> 
                        </slot>
                </div>

                <div v-else>
                    <slot> <p style="color:orange">{{ content }}</p></slot>
                </div>
        <!-- <p class="my-4" v-for="i in 10" :key="i">
            Cras mattis consectetur purus sit amet fermentum. Cras justo odio, dapibus ac facilisis
            in, egestas eget quam. Morbi leo risus, porta ac consectetur ac, vestibulum at eros.
            </p> -->
      </div>
      </b-container>

    </b-modal>
  </div>
</template>

<script>
  export default {
      name:"DcModal",
    data(){
        return{
            formSelectItem:'',
        }
    },
    props:{
        getData:{default:null},
        formSubmit:{
            default:null
        },
        content:{
            default:'Enter modal body content'
        },
        effect:{
            type:String,
            default:null
        },
        label:{
            type:String,
            default:'modal Label'
        },
        title:{
            type:String,
            default:'Modal Title'
        },
        mode:{
            type:String,
            default:null
        },
        formFields:{
            type:[],
            default:null
        },
        formSelect:{
            type:[],
            default:null
        },
        disabled:{
            type:Boolean,
            default:false
        },
        lbTheme:{
            type:String,
            default:'info'
        },
        pill:{
            type:String,
            default:null
        },
        squared:{
            type:String,
            default:null
        },
        size:{
            type:String,
            default:'md'
        },
        sbTitle:{
            type:String,
            default:'Submit'
        },
        sbTheme:{
            type:String,
            default:'info'
        },
        sbBlock:{
            type:Boolean,
            default:true
        },
        sbType:{
            type:String,
            default:'submit'
        },

    },  
    methods: {
      showModal() {
        this.$refs['my-modal'].show()
      },
      hideModal() {
        this.$refs['my-modal'].hide()
      },
      toggleModal() {
        this.$refs['my-modal'].toggle('#toggle-btn')
      }
    }
  }
</script>

<style scoped>
.form-input{
    margin-top: 10px !important;
}
.form-label{margin-top: 10px !important;}
</style>