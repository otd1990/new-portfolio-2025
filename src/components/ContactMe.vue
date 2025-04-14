<template>
  <article class="contact">
    <h2 class="contact__heading">Get In Touch</h2>
    <p class="contact__desc">Got a question? Please fill out the form below:</p>
    <form class="contact__form" method="POST" @submit.prevent="handleSubmit">
      <div class="contact__form-group">
        <label class="contact__form-label sr-only" for="contactName"
          >Name</label
        >
        <input
          type="text"
          class="contact__form-input"
          id="contactName"
          name="contactName"
          placeholder="Name"
          v-model="contactName"
          required
        />
      </div>
      <div class="contact__form-group">
        <label class="contact__form-label sr-only" for="contactEmail"
          >Email</label
        >
        <input
          type="email"
          class="contact__form-input"
          id="contactEmail"
          name="contactEmail"
          placeholder="Email"
          v-model="contactEmail"
          required
        />
      </div>
      <div class="contact__form-group">
        <label class="contact__form-label sr-only" for="contactComment"
          >Comment</label
        >
        <textarea
          class="contact__form-textarea"
          id="contactComment"
          name="contactComment"
          placeholder="Your Message"
          rows="4"
          cols="50"
          v-model="contactComment"
        />
      </div>
      <div class="contact__form-button-container">
        <button class="contact__form-btn">Submit</button>
      </div>
    </form>
  </article>
</template>

<script setup>
import emailjs from "emailjs-com";
import { ref } from "vue";

const contactName = ref("");
const contactEmail = ref("");
const contactComment = ref("");

const handleSubmit = (e) => {
  if (contactName.value === "" && contactEmail.value === "") return;

  emailjs
    .sendForm(
      import.meta.env.VITE_EMAIL_SERVICE_ID,
      import.meta.env.VITE_EMAIL_TEMPLATE_ID,
      e.target,
      import.meta.env.VITE_EMAIL_PUBLIC_KEY,
      {
        name: contactName.value,
        email: contactEmail.value,
        message: contactComment.value,
      }
    )
    .then((response) => console.log(response));

  // Reset form field
  contactName.value = "";
  contactEmail.value = "";
  contactComment.value = "";
};
</script>

<style>
.contact {
  min-height: 15rem;
  padding: 2rem 0;
  height: 100%;
  background-color: #232328;
}
.contact__heading {
  text-align: center;
  font-size: 2rem;
}

.contact__desc {
  text-align: center;
  margin-bottom: 1.5rem;
  color: #fff;
}

.contact__form {
  max-width: 1200px;
  display: block;
  margin: 0 auto;
  padding: 0 4rem;
}
.contact__form-label {
  display: block;
  margin-left: 0.15rem;
}

.contact__form-input {
  margin-bottom: 0.5rem;
}

.contact__form-input,
.contact__form-textarea {
  box-sizing: border-box;
  width: 100%;
  padding: 0.5rem;
  border-radius: 4px;
  background-color: #1f1f23;
  border: none;
  color: #fff;
  font-family: "Poppins", serif;
  min-height: 3rem;
}

::-webkit-input-placeholder {
  color: rgb(117, 117, 117);
}

.contact__form-btn {
  display: block;
  border: none;
  margin-left: auto;
  padding: 0.5rem 1rem;
  cursor: pointer;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  transition: all 0.3s;
  background-color: #1f1f23;
  color: #fff;
  border: 1px solid #fff;
  min-width: 7rem;
  font-family: "Poppins", serif;
  margin-top: 0.5rem;
}

.contact__form-btn:hover {
  background-color: rgb(187 187 187);
  color: #1f1f23;
}
</style>
