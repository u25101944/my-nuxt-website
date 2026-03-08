<!--Uthi Leseo Njokweni u25101944-->

<template>
     <header>
        <nav>
            <ul>
                <li><NuxtLink to = "/" class="nav">Home</NuxtLink></li>
                <li><NuxtLink to = "/projects" class="nav">Projects</NuxtLink></li>
                <li class="active"><NuxtLink to = "/contact"class=nav>Contact</NuxtLink></li>
                <li><NuxtLink to = "/APIs" class="nav">API</NuxtLink></li>
            </ul>
        </nav>
    </header>

    <main>
        <h1>Contact Us!</h1>
        <form 
            data-netlify="true" 
            method="POST" 
            id="contactForm" 
            name="contact"
            @submit.prevent="handleSubmit"
            class="contact-form"
          >
            <input type="hidden" name="form-name" value="contact" />
            
            <div class="form-row">
              <div class="form-group">
                <label :style="{ color: '#494429' }">Name *</label>
                <input 
                  type="text" 
                  name="name" 
                  id="name"
                  v-model="formData.name"
                  required
                  :style="{ borderColor: '#947268' }"
                  placeholder="Your first name"
                />
              </div>

              <div class="form-group">
                <label :style="{ color: '#494429' }">Surname *</label>
                <input 
                  type="text" 
                  name="surname" 
                  id="surname"
                  v-model="formData.surname"
                  required
                  :style="{ borderColor: '#947268' }"
                  placeholder="Your last name"
                />
              </div>
            </div>

            <div class="form-group">
              <label :style="{ color: '#494429' }">Email *</label>
              <input 
                type="email" 
                name="email" 
                id="email"
                v-model="formData.email"
                required
                :style="{ borderColor: '#947268' }"
                placeholder="your.email@example.com"
              />
              <span id="email-error" class="error-message" v-if="emailError">{{ emailError }}</span>
            </div>

            <div class="form-group">
              <label :style="{ color: '#494429' }">Message *</label>
              <textarea 
                name="message" 
                id="message"
                v-model="formData.message"
                required
                :style="{ borderColor: '#947268' }"
                placeholder="Type something..."
                rows="5"
              ></textarea>
              <span id="PhoneNumber-error" class="error-message" v-if="phoneError">{{ phoneError }}</span>
            </div>

            <button 
              type="submit" 
              id="submit"
              class="submit-btn"
              :style="{ backgroundColor: '#74070d' }"
              :disabled="isSubmitting"
            >
              <span v-if="!isSubmitting">Send Message </span>
              <span v-else>Sending...</span>
            </button>

            <p v-if="formSubmitted" class="success-message" :style="{ backgroundColor: '#494429', color: '#f3e3b2' }">
              ✅ Thanks! Your message has been sent. I'll get back to you soon!
            </p>
          </form>
    </main>

    <footer class="site-footer" :style="{ backgroundColor: '#310f10' }">
      <div class="container">
        <p :style="{ color: '#f3e3b2' }">© 2026 Uthi Njokweni. All rights reserved.</p>
      </div>
    </footer>
    
</template>

<script setup>
    import { ref } from 'vue'

    const formData =ref({
        name: "",
        surname: "",
        email: "",
        message: "",
    })

    const formSubmitted = ref(false)

    const handleSubmit = async () =>{
        const formBody = new FormData()
        formBody.append('form-name', 'form')
        formBody.append('name', formData.value.name)
        formBody.append('surname', formData.value.surname)
        formBody.append('email', formData.value.email)
        formBody.append('message', formData.value.message)

        try{
            await fetch ('/', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/x-www-form-urlencoded'
                },
                body: new URLSearchParams (formBody).toString()
            })

            formSubmitted.value = true

            formData.value = {
                name: '',
                email: '',
                message: ''
                }
        }
         catch (error) {
            console.error('Form submission error:', error)
            alert('Something went wrong. Please try again.')
        }
    }
</script>

<style>
    .contact-page {
    font-family: 'Segoe UI', sans-serif;
    line-height: 1.6;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
}

    .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 40px 20px;
    flex: 1;

}

.success-message {
  margin-top: 20px;
  padding: 15px 20px;
  border-radius: 8px;
  text-align: center;
  font-weight: 500;
  animation: slideIn 0.3s ease;
}

.form-container {
  padding: 50px 40px;
}

.form-container h2 {
  font-size: 2em;
  margin: 0 0 30px 0;
  font-weight: 600;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.form-group label {
  font-weight: 600;
  font-size: 0.95em;
  letter-spacing: 0.5px;
}

.form-group input,
.form-group textarea {
  padding: 12px 15px;
  border: 2px solid;
  border-radius: 8px;
  font-size: 1em;
  transition: all 0.3s ease;
  background-color: white;
  font-family: inherit;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #74070d !important;
  box-shadow: 0 0 0 3px rgba(116, 7, 13, 0.1);
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: #999;
  opacity: 0.7;
}


</style>