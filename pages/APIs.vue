<!--Uthi Leseo Njokweni u25101944-->

<template>
    <header>
        <nav>
            <ul>
                <li><NuxtLink to = "/" class="nav">Home</NuxtLink></li>
                <li><NuxtLink to = "/projects" class="nav">Projects</NuxtLink></li>
                <li><NuxtLink to = "/contact" class="nav">contact</NuxtLink></li>
                <li class="active"><NuxtLink to = "/APIs" class="nav">API</NuxtLink></li>
            </ul>
        </nav>
    </header>
     <div class = "dogFacts">
          <h2>Random Dog Facts</h2>

           <div v-if="dogLoading" class="loading-state">
            <p>Fetching a cute dog fact...</p>
            <div class="spinner"></div>
          </div>
        
          <div v-else-if="dogError" class="error-state">
            <p> {{ dogError }}</p>
            <button @click="fetchDogFact" class="retry-btn">Try Again</button>
          </div>
        
           <div v-else-if="dogFact" class="success-state">
            <div class="fact-card">
            <p class="dog-fact-text">"{{ dogFact }}"</p>
            </div>
           </div>
            <button @click="fetchDogFact" class="button" :disabled="dogLoading">
            {{ dogLoading ? 'Fetching...' : 'Get Another Fact' }}
            </button>
          </div>

        <div class="weather">
        <h2>Current Weather</h2>
        
      
        <div v-if="weatherLoading" class="weather-loading">
          Loading weather data...
        </div>
        
        
        <div v-else-if="weatherError" class="weather-error">
           {{ weatherError }}
        </div>
        
        
        <div v-else-if="weatherData" class="weather-display">
          <div class="weather-main">
            <img 
              :src="weatherData.icon" 
              :alt="weatherData.condition"
              class="weather-icon"
            >
            <div class="weather-temp">{{ weatherData.temp }}°C</div>
          </div>
          
          <div class="weather-details">
            <p class="weather-condition">{{ weatherData.condition }}</p>
            <div class="weather-stats">
              <div class="stat">
                <span>Feels like</span>
                <strong>{{ weatherData.feelsLike }}°C</strong>
              </div>
              <div class="stat">
                <span>Humidity</span>
                <strong>{{ weatherData.humidity }}%</strong>
              </div>
              <div class="stat">
                <span>Wind</span>
                <strong>{{ weatherData.wind }} km/h</strong>
              </div>
              <div class="stat">
                <span>{{ weatherData.location }}</span>
              </div>
            </div>
          </div>
        </div>
        
    
        <div v-else class="weather-error">
          No weather data available
        </div>
      </div>
</template>
 
<script setup>
     import { ref, onMounted } from 'vue'

    const dogFact = ref('')
    const dogLoading = ref(true)
    const dogError = ref('')

    const fetchDogFact = async () => {
        dogLoading.value = true
        dogError.value = ''
     
      try {
    
    const response = await fetch('http://dog-api.kinduff.com/api/facts')
    
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`)
    }
    
    const data = await response.json()
    
    
    if (data.success && data.facts && data.facts.length > 0) {
      dogFact.value = data.facts[0]
    } else {
      throw new Error('No fact received from API')
    }
    
  } catch (error) {
    console.error('Error fetching dog fact:', error)
    dogError.value = 'Could not fetch a dog fact. The API might be temporarily unavailable.'
  } finally {
    dogLoading.value = false
  }
}

const weatherData = ref(null)
const weatherLoading = ref(true)
const weatherError = ref('')

const API_KEY = 'e59c8ef429e44e59bd1232757260603'
const LOCATION = 'Pretoria'

const fetchWeather = async () => {
  weatherLoading.value = true
  weatherError.value = ''

   try {
    // WeatherAPI endpoint - free and reliable [citation:2]
    const response = await fetch(
      `https://api.weatherapi.com/v1/current.json?key=${API_KEY}&q=${LOCATION}&aqi=no`
    )
    
    if (!response.ok) {
      throw new Error(`Weather API error: ${response.status}`)
    }
    
    const data = await response.json()

    weatherData.value = {
      temp: Math.round(data.current.temp_c),
      feelsLike: Math.round(data.current.feelslike_c),
      condition: data.current.condition.text,
      icon: data.current.condition.icon, // WeatherAPI gives full icon URL
      humidity: data.current.humidity,
      wind: data.current.wind_kph,
      location: `${data.location.name}, ${data.location.country}`
    }
    
  } catch (error) {
    console.error('Error fetching weather:', error)
    weatherError.value = 'Could not load weather data. Please try again later.'
  } finally {
    weatherLoading.value = false
  }
}

onMounted(() => {
  fetchWeather()
})

</script>

<style></style>