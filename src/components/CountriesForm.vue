<script>
//import axios from 'axios';
import Toast from "./Toast.vue";
import { useVuelidate } from '@vuelidate/core'
import { required, maxLength, minLength, minValue, maxValue, alpha, numeric} from '@vuelidate/validators'

export default{
  setup(){
        return{
            v$:useVuelidate()
        }
    },

  data(){
    return{
      codeIso:'',
      country: '',
      population:0,
      superficie:0
    }
  },
  validations(){
    return{
      codeIso:{
        required,
        minLength: minLength(2),
        maxLength: maxLength(2),
        alpha
      },
      country:{
        required,
        minLength: minLength(1),
        maxLength: maxLength(255),
        alpha
      },
      population:{
        required,
        minValueValue: minValue(1),
        maxValueValue: maxValue(5000000000),
        numeric
      },
      superficie:{
        required,
        minValueValue: minValue(1),
        maxValueValue: maxValue(800000),
        numeric
      }
    }

  },
  methods:{
    async createNewcountry(){
      if(await this.v$.$validate()){
        /* try{
        const data = await axios({
          method:'post',
          url:''
        });
      } catch{
        console.log("axios error")
      } */
      const toast = bootstrap.Toast.getOrCreateInstance('#showToast', {
                            delay: 2500
                        });
                    toast.show()
        console.log(this.codeIso, this.country, this.population, this.superficie)
      } else{
        console.log("pas valide")
      }
     
    }
  }
}
</script>

<template>
  <div  class="container">
    <h1 class="text-center">PAYS</h1>
    <form  @submit.prevent="createNewcountry">
      <div class="row mb-3">
        <div class="col-md-3">
            <label for="codeIso" class="form-label">CODE ISO</label>
            <input v-model="codeIso" name="codeIso" type="text" id="codeIso" :class="{'is-invalid' : v$.codeIso.$error}"
                class="form-control my-2" />
        </div>
        <div class="col-md-9">
            <label for="country" class="form-label">PAYS</label>
            <input v-model="country" name="country" type="text" id="country" :class="{'is-invalid' : v$.country.$error}"
                class="form-control my-2" />
        </div>
      </div>
      <div class="row mb-3">
        <div class="col-md-6">
            <label for="population" class="form-label">POPULATION</label>
            <input v-model="population" name="population" type="number" id="population" :class="{'is-invalid' : v$.population.$error}"
                class="form-control my-2" />
        </div>
        <div class="col-md-6">
            <label for="superficie" class="form-label">SUPERFICIE en m2</label>
            <input v-model="superficie" name="superficie" type="number" id="superficie" :class="{'is-invalid' : v$.superficie.$error}"
                class="form-control my-2" />
        </div>
      </div>
      <div class="row mb-3">
        <div class="col d-flex justify-content-end content">
            <button type="submit" class="btn btn-dark col-12 col-md-2">Créer</button>
        </div>
      </div>
    </form>
</div>
</template>
