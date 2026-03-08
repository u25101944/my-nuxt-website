<!--Uthi Leseo Njokweni u25101944-->

<template>
     <header>
        <nav>
            <ul>
                <li><NuxtLink to = "/" class="nav">Home</NuxtLink></li>
                <li class="active"><NuxtLink to = "/projects" class="nav">Projects</NuxtLink></li>
                <li><NuxtLink to = "/contact" class="nav">Contact</NuxtLink></li>
                <li><NuxtLink to = "/APIs"class="nav">API</NuxtLink></li>
            </ul>
        </nav>
    </header>
    <main class="container">
      <h1 class="page-title" :style="{ color: '#74070d' }">My Projects</h1>
      <p class="page-subtitle" :style="{ color: '#494429' }">
        A collection of my work from various modules and personal projects
      </p>

      <div class="projects-grid">
        <!-- Project 1 - Hunger Games Overview -->
        <div class="project-card" :style="{ backgroundColor: '#947268' }">
          <div class="project-image-container">
            <img src="/images/project1.png" alt="Hunger Games Overview project screenshot" class="project-image">
          </div>
          <div class="project-content">
            <h2 class="project-title" :style="{ color: '#f3e3b2' }">Hunger Games Overview</h2>
            <p class="project-description" :style="{ color: '#f3e3b2' }">
              This project was done using CSS, HTML and JavaScript. It gives a basic overview of the first book in The Hunger Games trilogy, showcasing interactive elements and responsive design.
            </p>
            <div class="project-tech">
              <span class="tech-tag" :style="{ backgroundColor: '#74070d', color: '#f3e3b2' }">HTML</span>
              <span class="tech-tag" :style="{ backgroundColor: '#494429', color: '#f3e3b2' }">CSS</span>
              <span class="tech-tag" :style="{ backgroundColor: '#310f10', color: '#f3e3b2' }">JavaScript</span>
            </div>
          </div>
        </div>

        <!-- Project 2 - Vacation Oasis -->
        <div class="project-card" :style="{ backgroundColor: '#494429' }">
          <div class="project-image-container">
            <img src="/images/project2.png" alt="Vacation Oasis project screenshot" class="project-image">
          </div>
          <div class="project-content">
            <h2 class="project-title" :style="{ color: '#f3e3b2' }">Vacation Oasis</h2>
            <p class="project-description" :style="{ color: '#f3e3b2' }">
              A team project where we created a tourist attraction guide for South Africa.
            </p>
            <div class="project-tech"> 
              <span class="tech-tag" :style="{ backgroundColor: '#74070d', color: '#f3e3b2' }">HTML</span>
              <span class="tech-tag" :style="{ backgroundColor: '#947268', color: '#f3e3b2' }">CSS</span>
              <span class="tech-tag" :style="{ backgroundColor: '#310f10', color: '#f3e3b2' }">JavaScript</span>
              <span class="tech-tag" :style="{ backgroundColor: '#74070d', color: '#f3e3b2' }">Team Project</span>
            </div>
          </div>
        </div>

        <!-- Project 3 - Isometric Room -->
        <div class="project-card" :style="{ backgroundColor: '#74070d' }">
          <div class="project-image-container">
            <img src="/images/project3.png" alt="Isometric Room illustration" class="project-image">
          </div>
          <div class="project-content">
            <h2 class="project-title" :style="{ color: '#f3e3b2' }">Isometric Room</h2>
            <p class="project-description" :style="{ color: '#f3e3b2' }">
              An isometric illustration of my kitchen created using Adobe Illustrator.
            </p>
            <div class="project-tech">
              <span class="tech-tag" :style="{ backgroundColor: '#494429', color: '#f3e3b2' }">Adobe Illustrator</span>
              <span class="tech-tag" :style="{ backgroundColor: '#947268', color: '#f3e3b2' }">Isometric Design</span>
            </div>
          </div>
        </div>
      </div>
    </main>

    <footer class="site-footer" :style="{ backgroundColor: '#310f10' }">
      <div class="container">
        <p :style="{ color: '#f3e3b2' }">© 2026 Uthi Njokweni. All rights reserved.</p>
      </div>
    </footer>


  
</template>

<script scoped>
    
</script>

<style>
    .projects-page {
  font-family: 'Segoe UI', sans-serif;
  line-height: 1.6;
  display: flex;
  flex-direction: column;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
  flex: 1;
}


.page-title {
  font-size: 3em;
  text-align: center;
  margin: 20px 0 10px;
  font-weight: 700;
}

.page-subtitle {
  text-align: center;
  font-size: 1.2em;
  margin-bottom: 50px;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 30px;
  margin: 40px 0;
}

.project-card {
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0,0,0,0.15);
  display: flex;
  flex-direction: column;
  height: 100%;
}

.project-image-container {
  width: 100%;
  height: 220px;
  overflow: hidden;
  border-bottom: 3px solid #f3e3b2;
}

.project-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.project-content {
  padding: 25px;
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.project-title {
  font-size: 1.8em;
  margin: 0 0 15px 0;
  font-weight: 600;
  line-height: 1.3;
}

.project-description {
  font-size: 1em;
  margin-bottom: 20px;
  flex-grow: 1;
  opacity: 0.9;
  line-height: 1.6;
}

.project-tech {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: auto;
}

.tech-tag {
  padding: 6px 15px;
  border-radius: 20px;
  font-size: 0.85em;
  font-weight: 500;
  letter-spacing: 0.5px;
}
</style>