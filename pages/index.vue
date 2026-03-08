<!--Uthi Leseo Njokweni u25101944-->

<template>
    <header>
        <nav>
            <ul>
                <li class = active><NuxtLink to = "/" class="nav">Home</NuxtLink></li>
                <li><NuxtLink to = "/projects" class="nav">Projects</NuxtLink></li>
                <li><NuxtLink to = "/contact" class="nav">Contact</NuxtLink></li>
                <li><NuxtLink to = "/APIs"class="nav">API</NuxtLink></li>
            </ul>
        </nav>
    </header>

      <main>
        <section class="me">
             <h1 class="name">Hello, my name is Uthi Leseo Njokweni</h1>
             <p class="bio">I am a student at the University of Pretoria, doing my second year in Multimedia. I chose to study Multimedia because of the opportunity it offers to study and learn a wide variety of media outlets. In my first year I learnt how to create a basic HTML website, styling it with CSS as well as basic Javascript. Along with web development I also learnt how to use Adobe animate, illustator and photoshop. I do not know where I would like to branch off to in the future. </p>
             <div class="profile">
                <img src ="/public/images/Profile.jpeg" alt="image of me">
             </div>
        </section>

        <section class="skills">
            <h2>Skills</h2>
            <ul>
                <li>web Development</li>
                <li>Animation</li>
                <li>Programming in C++</li>
            </ul>
        </section>
     </main>

     <footer class="site-footer" :style="{ backgroundColor: '#310f10' }">
      <div class="container">
        <p :style="{ color: '#f3e3b2' }">© 2026 Uthi Njokweni. All rights reserved.</p>
      </div>
    </footer>

</template>

<script setup>
</script>

<style>
    .me{
        font-family: 'Segoe UI', sans-serif;
        line-height: 1.6;
        background-color: #947268;
    }

   .me p{
    color:#f3e3b2
   } 

   .me h1{
    color:#f3e3b2
   }

   .me img{
    width: 100%;
    height: 100%;
    object-fit: cover;
   }

   .skills{
    background-color:#f3e3b2;
    font-family: 'Segoe UI', sans-serif;
    line-height: 1.6;
   }

   .skills h2{
    color: #74070d
   }

   header{
    background-color: #310f10;
    padding: 20px 0;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
    background-color: #310f10;
   }

   nav{
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: center;
    gap: 30px;
    padding: 0 20px;
   }
   .nav{
    color: #f3e3b2;
    text-decoration: none;
    font-weight: 500;
    padding: 8px 16px;
    border-radius: 4px;
    font-size: 1.1em;
   }
   .active{
    background-color: #74070d;
    color: #f3e3b2;
   }



</style>