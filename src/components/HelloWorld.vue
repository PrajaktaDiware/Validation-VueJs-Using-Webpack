
 <script src="path/to/vue.js"></script>
  <script src="path/to/vee-validate.js"></script>
<template>

  <div id="app">
    <form @submit.prevent="validateBeforeSubmit" >
    <h1>Form Validation with Vue 2</h1>
     <div class="column is-12">
    <div class="form-group" >
            <label class="control-label" for="name">Name</label>
               <p class="control has-icon has-icon-right">
            <input name="name" v-model="name" v-validate="'required|alpha|min:3|max:6'" :class="{'input': true, 'is-danger': errors.has('name') }" type="text" placeholder="Name">
            <p class="text-danger fa fa-warning" v-if="errors.has('name')">{{ errors.first('name') }}</p>
               </p>
        </div>
        </div>

        <div class="column is-12">
    <div class="form-group" >
            <label class="control-label" for="email">Email</label>
               <p class="control has-icon has-icon-right">
            <input name="email" v-model="email" v-validate="'required|email'" :class="{'input': true, 'is-danger': errors.has('email') }" type="text" placeholder="Email">
            <p class="text-danger fa fa-warning" v-if="errors.has('email')">{{ errors.first('email') }}</p>
               </p>
        </div>
        </div>

        <div class="column is-12">
    <div class="form-group" >
            <label class="control-label" for="phone">Phone</label>
               <p class="control has-icon has-icon-right">
            <input name="phone" v-model="phone" v-validate="'required|numeric'" :class="{'input': true, 'is-danger': errors.has('phone') }" type="text" placeholder="Phone">
            <p class="text-danger fa fa-warning" v-if="errors.has('phone')">{{ errors.first('phone') }}</p>
               </p>
        </div>
        </div>
         <div class="column is-12">
    <div class="form-group" >
            <label class="control-label" for="phone">Url</label>
               <p class="control has-icon has-icon-right">
            <input name="url" v-model="url" v-validate="'required|url'" :class="{'input': true, 'is-danger': errors.has('url') }" type="text" placeholder="Website">
            <p class="text-danger fa fa-warning" v-if="errors.has('url')">{{ errors.first('url') }}</p>
               </p>
        </div>
        </div>
  
   
        <button class="btn btn-primary" type="submit">Submit</button>
    </form>
   
  </div>
</template>

<script>
import Vue from 'vue'
import VeeValidate from 'vee-validate'

Vue.use(VeeValidate)

export default {
  name: 'HelloWorld',
  data: () => ({
    email: '',
    name: '',
    phone: '',
    url: ''
  }),
  methods: {
    validateBeforeSubmit () {
      this.$validator.validateAll().then(result => {
        if (result) {
          // eslint-disable-next-line
          alert('From Submitted!');
          return
        }

        alert('Correct them errors!')
      })
    }
  }
}
</script>

<style scoped>
/* .has-error .form-control {
  border-color: #a94442;
} */
body{
  margin-left: 0px;
}
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

</style>