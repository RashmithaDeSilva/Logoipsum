<script setup>
import { reactive, ref } from 'vue'

const form = reactive({
  firstName: '',
  lastName: '',
  email: '',
  telephone: '',
  message: '',
  agree: false,
})

const errors = reactive({
  firstName: '',
  lastName: '',
  email: '',
  message: '',
  agree: '',
})

const validateForm = () => {
  let isValid = true

  errors.firstName = form.firstName ? '' : '* First name is required'
  errors.lastName = form.lastName ? '' : '* Last name is required'
  errors.email = form.email ? '' : '* Email is required'
  errors.message = form.message ? '' : '* Message is required'
  errors.agree = form.agree ? '' : '* You must agree to the Terms & Conditions'

  if (!form.firstName || !form.lastName || !form.email || !form.message || !form.agree) {
    isValid = false
  }

  return isValid
}

const submitForm = (e) => {
  e.preventDefault()
  if (validateForm()) {
    alert(`
      First Name: ${form.firstName}
      Last Name: ${form.lastName}
      Email: ${form.email}
      Telephone: ${form.telephone}
      Message: ${form.message}
    `)
  }
}
</script>

<template>
  <section class="contact-map-section">
    <h1>How to reach us</h1>
    <h4>Lorem ipsum dolor sit amet, consetetur.</h4>
    <div class="contact-map-container">
      <div class="form-container">
        <form @submit="submitForm">

          <div class="input-row">
            <div class="form-group">
              <label for="firstName">First name</label>
              <input
                id="firstName"
                type="text"
                v-model="form.firstName"
                :class="{ error: errors.firstName }"
              />
              <p v-if="errors.firstName" class="error-text">{{ errors.firstName }}</p>
            </div>

            <div class="form-group">
              <label for="lastName">Last name</label>
              <input
                id="lastName"
                type="text"
                v-model="form.lastName"
                :class="{ error: errors.lastName }"
              />
              <p v-if="errors.lastName" class="error-text">{{ errors.lastName }}</p>
            </div>
          </div>

          <div class="form-group">
            <label for="email">Email</label>
            <input
              id="email"
              type="email"
              v-model="form.email"
              :class="{ error: errors.email }"
            />
            <p v-if="errors.email" class="error-text">{{ errors.email }}</p>
          </div>

          <div class="form-group">
            <label for="telephone">Telephone</label>
            <input id="telephone" type="text" v-model="form.telephone" />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              rows="4"
              v-model="form.message"
              :class="{ error: errors.message }"
            ></textarea>
            <p v-if="errors.message" class="error-text">{{ errors.message }}</p>
          </div>

          <div class="form-group checkbox-group">
            <input
              id="agree"
              type="checkbox"
              v-model="form.agree"
            />
            <label for="agree">I agree to the <span>Terms & Conditions</span></label>
            <p v-if="errors.agree" class="error-text">{{ errors.agree }}</p>
          </div>

          <div class="btn-group">
            <button type="submit">Submit</button>
          </div>
        </form>
      </div>

      <div class="map-container">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2992.5876748429524!2d2.279773115421303!3d43.6013668791225!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x12ae096e6c682b1d%3A0x9ff35e1f07cbb2d8!2sAmadeus%20IT%20Group%20SA!5e0!3m2!1sen!2sus!4v1664645651822!5m2!1sen!2sus"
          width="100%"
          height="300"
          style="border:0;"
          allowfullscreen=""
          loading="lazy"
        ></iframe>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-map-section {
  background-color: black;
  color: white;
  padding: 5rem 2rem;
}
h1 {
  font-size: 2rem;
}
h4 {
  color: gray;
  margin-bottom: 2rem;
}
label {
    color: grey;
}
.contact-map-container {
  display: flex;
  flex-wrap: wrap;
  gap: 4rem;
}
.form-container {
  flex: 1;
  min-width: 300px;
}
.input-row {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  width: 100%;
}
.input-row .form-group {
  width: 100%;
}
.form-group {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}
input,
textarea {
  padding: 0.5rem;
  border: 1px solid black;
  border-radius: 4px;
  background-color: gray;
  color: white;
}
input.error,
textarea.error {
  border-color: red;
}
.error-text {
  color: red;
  font-size: 0.875rem;
}
.checkbox-group {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: start;
  gap: 0.5rem;
}
button {
  padding: 0.75rem 1.5rem;
  border: none;
  background-color: orange;
  color: white;
  font-weight: bold;
  cursor: pointer;
  border-radius: 10px;
}
.map-container {
  flex: 1;
  min-width: 300px;
}
.btn-group {
    width: 100%;
    display: flex;
    justify-content: center;
}
span {
    color: white;
}

@media (min-width: 768px) {
    .input-row {
        flex-direction: row;
        gap: 1rem;
    }
    .input-row .form-group {
        width: 50%;
    }
    .btn-group {
        justify-content: end;
    }
}

@media (min-width: 1536px) {
  .contact-map-section {
    padding: 5rem 10rem;
  }
}
</style>
