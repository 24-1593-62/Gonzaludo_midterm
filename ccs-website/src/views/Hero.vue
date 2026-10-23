<template>
  <section id="hero" class="hero">
    <div class="background">
      <img src="@/assets/cpu.jpeg" alt="CPU Campus" />
    </div>
    <img src="@/assets/ccs.png" alt="CCS Logo" class="ccs" />
    <h1>HOME OF THE DAUNTLESS AND THE BRAVE </h1>
    <h1>CCS THE BEST!! </h1>
    
    <RouterLink to="/#programs" class="explore-academics">
      Explore Academics
    </RouterLink>
  </section>
</template>

<script setup>

</script>

<style scoped>


.hero {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 80vh;
  text-align: center;
  padding: 2rem;
  color: #ffffff;
}

.background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
  overflow: hidden;
}

.background img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: brightness(0.4);
}

.ccs {
  width: 120px;
  height: auto;
  margin-bottom: 1rem;
}

h1 {
  font-size: 2.25rem;
  font-weight: 800;
  letter-spacing: 0.05em;
  margin-bottom: 1.5rem;
}

.explore-academics {
  display: inline-block;
  padding: 0.75rem 1.75rem;
  background-color: #f59e0b;
  color: #0f172a;
  font-weight: 700;
  border-radius: 0.5rem;
  text-decoration: none;
  transition: background-color 0.2s ease, transform 0.2s ease;
}

.explore-academics:hover {
  background-color: #d97706;
  transform: translateY(-2px);
}
</style>