<template>
  <nav class="navbar">
    <div class="brand">
      <img src="@/assets/ccs.png" class="ccs" alt="CCS Logo" />
      <div class="brand-text">
        <h3>College of Computer Studies</h3>
      </div>
    </div>

    <div class="nav-right">
      <ul>
        <li><router-link :to="{ path: '/', hash: '#hero' }">Home</router-link></li>
        <li><router-link :to="{ path: '/', hash: '#program' }">Program</router-link></li>
        <li><router-link :to="{ path: '/', hash: '#faculty' }">Faculty</router-link></li>
        <li><router-link :to="{ path: '/', hash: '#partnerships' }">Partnerships</router-link></li>
      </ul>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: sticky;
  top: 0;
  z-index: 1000;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 50px;
  background: #fff;
  flex-wrap: wrap;
  gap: 1rem;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.brand {
  display: flex;
  align-items: center;
  gap: 0.7rem;
}

.ccs {
  height: 45px;
  width: auto;
}

.brand-text h3 {
  font-family: 'Times New Roman', Times, serif;
  font-size: 1.5rem;
  font-weight: 700;
  color: #2b1b53;
  margin: 0;
}

.nav-right {
  display: flex;
  align-items: center;
  gap: 1.5rem;
}

nav ul {
  display: flex;
  list-style: none;
  gap: 2rem;
  margin: 0;
  padding: 0;
}

nav a {
  text-decoration: none;
  color: #1e293b;
  font-weight: 600;
  transition: color 0.2s;
}

nav a:hover,
nav a.router-link-exact-active {
  color: #d97706; /* Gold accent hover */
}
</style>