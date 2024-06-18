<template>
  <div class="home-container">
    <div class="home-content">
      <h1 class="home-title">THIS IS MY HOME</h1>
      <p class="home-description">UAS PBK - ANDIKA SHALIHIN</p>
      <router-link to="/about" class="btn" @click="handleAboutClick">⇨ Tentang Indonesia ⇦</router-link>
    </div>
    <div class="side-feature">
      <h2 class="feature-title">Fitur Menarik</h2>
      <p class="feature-description">Temukan lebih banyak informasi menarik tentang Indonesia.</p>
      <img src="https://th.bing.com/th/id/OIP.LidvGcI0zJsuUNVCBhyu-gHaIG?rs=1&pid=ImgDetMain" alt="Garuda Pancasila" class="feature-image">
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    handleAboutClick() {
      this.$router.push('/about');
    }
  }
}
</script>

<style>
.home-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(to right, #0f0c29, #302b63, #24243e); /* Gradient background */
  padding: 20px;
}

.home-content {
  text-align: center;
  background-color: rgba(255, 255, 255, 0.9); /* Semi-transparent background */
  padding: 40px;
  border-radius: 20px; /* Rounded border */
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3); /* Shadow effect */
  margin-right: 40px;
  backdrop-filter: blur(10px); /* Blur effect */
  color: #333; /* Text color */
  transition: transform 0.3s ease;
}

.home-content:hover {
  transform: translateY(-5px);
}

.home-title {
  font-size: 48px;
  font-weight: bold;
  margin-bottom: 20px;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3); /* Text shadow */
}

.home-description {
  font-size: 20px;
  color: #666;
  margin-bottom: 30px;
}

.btn {
  padding: 15px 30px;
  background-color: #007bff;
  color: white;
  text-decoration: none;
  border-radius: 25px;
  font-size: 18px;
  transition: background-color 0.3s ease;
  display: inline-block;
}

.btn:hover {
  background-color: #0056b3;
}

.side-feature {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background-color: rgba(255, 255, 255, 0.9); /* Semi-transparent background */
  border-radius: 20px;
  padding: 30px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3); /* Shadow effect */
  backdrop-filter: blur(10px); /* Blur effect */
  width: 250px;
  text-align: center;
  color: #333; /* Text color */
}

.feature-title {
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 15px;
}

.feature-description {
  font-size: 16px;
  color: #666;
  margin-bottom: 20px;
}

.feature-image {
  width: 150px;
  height: auto;
  margin-top: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Shadow effect */
}

@media (max-width: 768px) {
  .home-container {
    flex-direction: column;
  }

  .home-content {
    margin-right: 0;
    margin-bottom: 20px;
  }

  .side-feature {
    margin-top: 20px;
    margin-left: 0;
  }
}
</style>
