<template>
  <form @submit="checkForm">
    <div class="row">
      <div class="col-xl-12">
        <h1>Contact us</h1>
        <hr />

        <div class="mb-3">
          <label for="name">Name</label>
          <input type="text" id="name" class="form-control" v-model.lazy="formData.name" />
        </div>

        <div class="mb-3">
          <label for="email">Email</label>
          <input type="email" id="email" class="form-control" v-model="formData.email" />
        </div>

        <div class="mb-3">
          <label for="subject">Subject</label>
          <input type="text" id="subject" class="form-control" v-model="formData.subject" />
        </div>

        <div class="mb-3">
          <label for="message">Message</label>
          <textarea class="form-control" rows="3" id="message" v-model="formData.message"></textarea>
        </div>


        <div class="mb-3">
          <h5>Want more spam ? </h5>
          <div class="form-check">
            <input class="form-check-input" type="checkbox" value="Newsletter" id="newsletter"
              v-model="formData.extras">
            <label class="form-check-label" for="newsletter">
              Newsletter
            </label>
          </div>
          <div class="form-check">
            <input class="form-check-input" type="checkbox" value="Promotions" id="promotions"
              v-model="formData.extras">
            <label class="form-check-label" for="newsletter">
              Promotions
            </label>
          </div>
        </div>
        <div class="mb-3">
          <h5>What are you ? </h5>
          <div class="form-check">
            <input class="form-check-input" type="radio" id="human" value="human" name="origin"
              v-model="formData.gender">
            <label class="form-check-label" for="human">
              Human
            </label>
          </div>
          <div class="form-check">
            <input class="form-check-input" type="radio" id="alien" value="alien" name="origin"
              v-model="formData.gender">
            <label class="form-check-label" for="alien">
              Alien
            </label>
          </div>
        </div>
        <hr />

        <p v-if="errors.length">
          <b>oops, fix the error</b>
        <ul>
          <li v-for="error in errors" :key="error">
            {{ error }}
          </li>
        </ul>
        </p>

        <button class="btn btn-primary">
          Submit
        </button>

      </div>
    </div>
  </form>
</template>


<script setup>
    import { reactive } from 'vue';
    
    const errors = reactive([])
    const formData = reactive({
      name:'',
      email:'',
      subject:'',
      message:'',
      // newsletter: false,
      // promotions: false,
      extras:[],
      gender:''
    })

    const checkForm = (e) => {
      e.preventDefault();
      errors.splice(0) // reset array to []

      if (!formData.name) {
        errors.push('Sorry, the name is required')
      }

      if (!formData.email) {
        errors.push('Sorry, the email is required')
      }

      if (!errors.length) {
        submitForm()
      }
    }

    const submitForm = () => {
      // console.log(JSON.stringify(formData))
      console.log(formData)
    }
</script>