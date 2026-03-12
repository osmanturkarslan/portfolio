<template>
<section class="py-24 px-6 text-white">

<div class="max-w-5xl mx-auto">

<!-- Title -->
      <div class="text-center mb-16">
        <h1 class="text-4xl md:text-5xl font-bold mb-6 text-center">
          Contact
        </h1>
        <p class="text-gray-600 max-w-xl mx-auto">
          Feel free to contact me for collaborations, projects or job opportunities.
        </p>
      </div>

<div class="grid md:grid-cols-2 gap-12">

<!-- CONTACT INFO -->
 <div class="space-y-8">

          <div class="flex flex-col items-center text-center">
            <EnvelopeIcon class="w-8 h-8 text-blue-400 mb-2"/>
            <p class="text-gray-600">osmanturkarslan1620@gmail.com</p>
          </div>

          <div class="flex flex-col items-center text-center">
            <PhoneIcon class="w-8 h-8 text-blue-400 mb-2"/>
            <p class="text-gray-600">078 246 33 56</p>
          </div>

          <div class="flex flex-col items-center text-center">
            <MapPinIcon class="w-8 h-8 text-blue-400 mb-2"/>
            <p class="text-gray-600">Agarn, Switzerland</p>
          </div>


<!-- SOCIAL ICONS -->
<div class="flex justify-center items-center gap-6 pt-4">
  <a
    href="https://linkedin.com/in/osman-turkarslan"
    target="_blank"
    class="group"
  >
    <img
      src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg"
      class="w-8 transition duration-300 transform group-hover:scale-110 group-hover:-translate-y-1"
      alt="LinkedIn"
    />
  </a>

  <a
    href="https://github.com/"
    target="_blank"
    class="group"
  >
    <img
      src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg"
      class="w-8 transition duration-300 transform group-hover:scale-110 group-hover:-translate-y-1"
      alt="GitHub"
    />
  </a>
</div>

</div>

<!-- FORM -->
<form
@submit.prevent="sendEmail"
class="space-y-5"
>

<input
v-model="name"
type="text"
placeholder="Your name"
required
class="w-full bg-transparent border border-gray-500 px-4 py-3 rounded-lg focus:outline-none focus:ring-2 focus:ring-cyan-300/50 focus:border-cyan-300"
/>

<input
v-model="email"
type="email"
placeholder="Your email"
required
class="w-full bg-transparent border border-gray-500 px-4 py-3 rounded-lg focus:outline-none focus:ring-2 focus:ring-cyan-300/50 focus:border-cyan-300"
/>

<textarea
v-model="message"
rows="5"
placeholder="Your message"
required
class="w-full bg-transparent border border-gray-500 px-4 py-3 rounded-lg focus:outline-none focus:ring-2 focus:ring-cyan-300/50 focus:border-cyan-300"
></textarea>

<button
type="submit"
class="bg-cyan-500/85 hover:bg-cyan-400/90 text-white px-6 py-3 rounded-xl transition shadow-[0_10px_20px_rgba(34,211,238,0.25)] border border-cyan-200/25"
>
Send Message
</button>

</form>

</div>

</div>

</section>
</template>

<script setup>

import { ref } from "vue"
import emailjs from "@emailjs/browser"
import {
  EnvelopeIcon,
  PhoneIcon,
  MapPinIcon,
  LinkIcon
} from '@heroicons/vue/24/outline'

const name = ref("")
const email = ref("")
const message = ref("")

const sendEmail = () => {

const templateParams = {
name: name.value,
email: email.value,
message: message.value
}

emailjs.send(
"service_g7xbids",
"template_gku9fkm",
templateParams,
"SD0IsSH4ZWWdKB1on"
)
.then(() => {

alert("Message sent successfully 🚀")

name.value = ""
email.value = ""
message.value = ""

})
.catch(() => {
alert("Error sending message")
})

}

</script>