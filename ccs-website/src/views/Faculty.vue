<template>
  <section id="faculty" class="faculty-section">
    <!-- Header Section -->
    <div class="header">
      <h2>Faculty & Staff</h2>
      <p>The mentors behind the college's success</p>
      <div class="divider"></div>
    </div>

    <!-- College Leadership Section -->
    <div class="leadership-group">
      <div class="card card-leadership">
        <div class="avatar-wrapper">
          <img src="@/assets/quijano.png" alt="Ma. Christina A. Quijano" class="avatar" />
        </div>
        <div class="card-info">
          <h3>MA. CHRISTINA A. QUIJANO, MSCS</h3>
          <span class="badge dean-badge">DEAN</span>
        </div>
      </div>

      <div class="card card-leadership">
        <div class="avatar-wrapper">
          <img src="@/assets/castano.jpg" alt="Chrislyn C. Castaño" class="avatar" />
        </div>
        <div class="card-info">
          <h3>CHRISLYN C. CASTAÑO</h3>
          <span class="badge sec-badge">COLLEGE SECRETARY</span>
        </div>
      </div>
    </div>

    <!-- Department Sections (Expandable Accordion) -->
    <div 
      v-for="(dept, index) in departments" 
      :key="dept.name" 
      class="department-block"
      :class="{ 'is-expanded': dept.expanded }"
    >
      <div class="dept-header" @click="toggleDepartment(index)">
        <div class="dept-title-group">
          <h3 class="dept-title">{{ dept.name }}</h3>
          <span class="member-count">({{ dept.members.length }} members)</span>
        </div>
        
        <button class="expand-btn" :aria-label="dept.expanded ? 'Collapse section' : 'Expand section'">
          <span class="btn-text">{{ dept.expanded ? 'Collapse' : 'Expand' }}</span>
          <svg 
            class="chevron-icon" 
            :class="{ 'rotate': dept.expanded }" 
            xmlns="http://www.w3.org/2000/svg" 
            viewBox="0 0 24 24" 
            fill="none" 
            stroke="currentColor" 
            stroke-width="2" 
            stroke-linecap="round" 
            stroke-linejoin="round"
          >
            <polyline points="6 9 12 15 18 9"></polyline>
          </svg>
        </button>
      </div>

      <!-- Expandable Grid Content -->
      <transition name="accordion">
        <div v-show="dept.expanded" class="faculty-grid">
          <div v-for="member in dept.members" :key="member.name" class="card faculty-card">
            <div class="avatar-wrapper">
              <img :src="member.image" :alt="member.name" class="avatar" />
            </div>
            <div class="card-info">
              <h4>{{ member.name }}</h4>
              <p class="role">{{ member.role }}</p>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const getAssetUrl = (name) => {
  return new URL(`../assets/${name}`, import.meta.url).href
}

const departments = ref([
  {
    name: 'Information Technology Department',
    expanded: true,
    members: [
      { name: 'ROSE LEAH JOY A. OJACASTRO, MSCS', role: 'DEPARTMENT HEAD, IT', image: getAssetUrl('ojacastro.png') },
      { name: 'LEO PAULO B. BELDIA, MSCS', role: 'FACULTY', image: getAssetUrl('beldia.png') },
      { name: 'RODOLFO C. EREGIA, JR., MSCS', role: 'FACULTY', image: getAssetUrl('eregia.png') },
      { name: 'REA P. BALONTONG, MBA', role: 'FACULTY', image: getAssetUrl('balontong.png') },
      { name: 'GLEASON B. BAYLON, MSCS', role: 'FACULTY', image: getAssetUrl('baylon.png') }
    ]
  },
  {
    name: 'Computer Science & BSDMIA Department',
    expanded: true,
    members: [
      { name: 'MARJEE ROSE B. PARREÑO, MSCS', role: 'DEPARTMENT HEAD, BSCS AND BSDMIA', image: getAssetUrl('parreno.jpg') },
      { name: 'MA. SHIELA C. SAPUL, Ph.D.CS', role: 'FACULTY', image: getAssetUrl('sapul.jpg') },
      { name: 'ANTONIO M. MONTAÑO, JR., MSCS', role: 'FACULTY', image: getAssetUrl('montano.jpg') }
    ]
  },
  {
    name: 'Library & Information Science Program',
    expanded: true,
    members: [
      { name: 'RHEA JOY T. FERNANDEZ, MLIS', role: 'PROGRAM COORDINATOR', image: getAssetUrl('fernandez.png') }
    ]
  },
  {
    name: 'Laboratories & Technical Staff',
    expanded: true,
    members: [
      { name: 'PEDRO PETER RHYS B. CAMBRONERO, JR., MSCS', role: 'LABORATORY COORDINATOR', image: getAssetUrl('cambronero.png') },
      { name: 'JUNYEE H. PACHECO', role: 'COMPUTER TECHNICIAN', image: getAssetUrl('pacheco.png') },
      { name: 'A.M.P. LATTER P. TAASAN', role: 'COMPUTER TECHNICIAN', image: getAssetUrl('taasan.jpg') }
    ]
  }
])

const toggleDepartment = (index) => {
  departments.value[index].expanded = !departments.value[index].expanded
}
</script>

<style scoped>
.faculty-section {
  max-width: 1200px;
  margin: 0 auto;
  padding: 4rem 1.5rem;
  font-family: 'Segoe UI', system-ui, -apple-system, BlinkMacSystemFont, Roboto, sans-serif;
  color: #1e293b;
  background-color: #ffffff;
}

/* Header Section */
.header {
  text-align: left;
  margin-bottom: 2.5rem;
}

.header h2 {
  font-size: 1.8rem;
  font-weight: 700;
  color: #0f172a;
  margin-bottom: 0.35rem;
}

.header p {
  color: #64748b;
  font-size: 0.95rem;
}

.divider {
  width: 100%;
  height: 2px;
  background-color: #e2e8f0;
  margin-top: 1rem;
}

/* Leadership Section */
.leadership-group {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1.5rem;
  margin-bottom: 3.5rem;
}

.card-leadership {
  width: 100%;
  max-width: 340px;
}

/* Department Section & Expandable Header */
.department-block {
  margin-bottom: 2.5rem;
  background: #ffffff;
  border-radius: 12px;
}

.dept-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem 0;
  border-bottom: 2px solid #eab308;
  cursor: pointer;
  user-select: none;
  margin-bottom: 1.5rem;
  transition: color 0.2s ease;
}

.dept-header:hover .dept-title {
  color: #d97706;
}

.dept-title-group {
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.dept-title {
  font-size: 1.25rem;
  font-weight: 700;
  color: #0f172a;
  transition: color 0.2s ease;
}

.member-count {
  font-size: 0.85rem;
  color: #64748b;
  font-weight: 500;
}

.expand-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background: transparent;
  border: none;
  color: #64748b;
  font-weight: 600;
  font-size: 0.85rem;
  cursor: pointer;
}

.chevron-icon {
  width: 18px;
  height: 18px;
  transition: transform 0.3s ease;
}

.chevron-icon.rotate {
  transform: rotate(180deg);
}

/* Cards Design (Matches the gold outlined style in image) */
.faculty-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 1.5rem;
}

.card {
  background-color: #ffffff;
  border: 1.5px solid #eab308; /* Light Gold/Yellow Border */
  border-radius: 12px;
  padding: 1.5rem 1.25rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.08);
}

.avatar-wrapper {
  margin-bottom: 1rem;
}

.avatar {
  width: 110px;
  height: 110px;
  border-radius: 50%;
  object-fit: cover;
  border: 1px solid #cbd5e1;
  background-color: #f1f5f9;
}

/* Card Info & Badges */
.card-info {
  width: 100%;
}

.card-info h3, .card-info h4 {
  font-size: 0.95rem;
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 0.35rem 0;
  line-height: 1.35;
}

.role {
  font-size: 0.8rem;
  font-weight: 600;
  color: #d97706; /* Darker Gold Text */
  margin: 0;
}

.badge {
  display: inline-block;
  padding: 0.3rem 0.85rem;
  font-size: 0.7rem;
  font-weight: 700;
  border-radius: 9999px;
  margin-top: 0.5rem;
}

.dean-badge {
  background-color: #fef3c7;
  color: #b45309;
}

.sec-badge {
  background-color: #f1f5f9;
  color: #475569;
  border: 1px solid #cbd5e1;
}

/* Smooth Accordion Animation */
.accordion-enter-active,
.accordion-leave-active {
  transition: all 0.3s ease-in-out;
  max-height: 1200px;
  opacity: 1;
  overflow: hidden;
}

.accordion-enter-from,
.accordion-leave-to {
  max-height: 0;
  opacity: 0;
  padding-top: 0;
  padding-bottom: 0;
  overflow: hidden;
}

@media (max-width: 640px) {
  .faculty-grid {
    grid-template-columns: 1fr;
  }
  .btn-text {
    display: none;
  }
}
</style>