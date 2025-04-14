<template>
  <article class="contact card gradient-background border-radius-std">
    <h2 class="contact__heading">Get In Touch</h2>
    <form class="contact__form" method="POST" @submit.prevent="handleSubmit">
      <div class="contact__form-group">
        <label class="contact__form-label" for="contactName">Name</label>
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
        <label class="contact__form-label" for="contactEmail">Email</label>
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
        <label class="contact__form-label" for="contactComment">Comment</label>
        <textarea
          class="contact__form-textarea"
          id="contactComment"
          name="contactComment"
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
  height: 100%;
}
.contact__heading {
  text-align: center;
}
.contact__form {
  max-width: 800px;
  display: block;
  margin: 0 auto;
}
.contact__form-label {
  display: block;
  margin-left: 0.15rem;
}
.contact__form-input,
.contact__form-textarea {
  box-sizing: border-box;
  width: 100%;
  padding: 0.5rem;
  border-radius: 4px;
}

.contact__form-btn {
  display: block;
  margin: 0 auto;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  transition: all 0.3s;
  font-family: "Raleway", sans-serif;
}

.contact__form-btn:hover {
  background-color: rgb(187 187 187);
  color: #fff;
}
</style>
