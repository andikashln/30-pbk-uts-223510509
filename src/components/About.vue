<template>
  <div class="about-container">
    <div class="about-content">
      <h1 class="about-title">Tentang Indonesia</h1>
      <p class="about-description">Bendera Merah Putih adalah bendera nasional Indonesia. Bendera ini terdiri dari dua warna, yaitu merah di bagian atas dan putih di bagian bawah. Merah melambangkan keberanian dan putih melambangkan kesucian. Desain bendera ini pertama kali diadopsi pada 17 Agustus 1945, saat Indonesia memproklamasikan kemerdekaannya dari Belanda.</p>
      
      <div class="feature-boxes">
        <div class="feature-box">
          <h2 class="box-title">Simbol Kemerdekaan</h2>
          <p class="box-description">Bendera Merah Putih melambangkan semangat kemerdekaan bangsa Indonesia.</p>
        </div>
        <div class="feature-box">
          <h2 class="box-title">Persatuan Bangsa</h2>
          <p class="box-description">Bendera ini merupakan simbol persatuan dan kesatuan Indonesia yang beragam suku, budaya, dan agama.</p>
        </div>
        <div class="feature-box">
          <h2 class="box-title">Regulasi Penggunaan</h2>
          <p class="box-description">Penggunaan bendera diatur oleh Undang-Undang Dasar Negara Republik Indonesia Tahun 1945.</p>
        </div>
      </div>
      
      <p class="about-description">Bendera Merah Putih memiliki arti dan makna yang dalam bagi masyarakat Indonesia. Selain sebagai simbol kemerdekaan dan kedaulatan negara, bendera ini juga melambangkan semangat persatuan dan kesatuan bangsa Indonesia yang terdiri dari beragam suku, budaya, dan agama. Penggunaan bendera Merah Putih diatur oleh Undang-Undang Dasar Negara Republik Indonesia Tahun 1945 dan peraturan lebih lanjut yang mengatur mengenai bendera, termasuk tata cara pengibarannya. Bendera ini juga sering dikibarkan dalam berbagai acara resmi, peringatan, dan upacara di seluruh Indonesia.</p>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style>
.about-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('https://1.bp.blogspot.com/-lB6INpi2QFQ/XWvCcjLFphI/AAAAAAAAE5I/-6tGdskNTAMZdIZf1UxBRrAQLxphJMw2wCLcBGAs/s1600/bendera-merah-putih.jpg');
  background-size: cover;
  background-position: center;
  position: relative; /* Added for the animation */
  overflow: hidden; /* Added for the animation */
}

.about-content {
  text-align: center;
  opacity: 0; /* Added for the animation */
  transform: translateY(20px); /* Added for the animation */
  transition: opacity 0.5s, transform 0.5s; /* Added for the animation */
  padding: 30px; /* Added for spacing */
  max-width: 800px; /* Added for better readability */
  margin: 0 auto; /* Center align */
}

.about-container:hover .about-content {
  opacity: 1; /* Added for the animation */
  transform: translateY(0); /* Added for the animation */
}

.about-title {
  font-size: 36px;
  font-weight: bold;
  color: #fcfcfc;
  margin-bottom: 20px;
}

.about-description {
  font-size: 18px;
  color: #fdfcfc;
  margin-bottom: 30px;
  text-align: justify; /* Justify text for better readability */
}

.feature-boxes {
  display: flex;
  justify-content: center;
  margin-top: 30px;
}

.feature-box {
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 10px;
  padding: 20px;
  margin: 0 10px;
  width: 250px;
  text-align: center;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}

.box-title {
  font-size: 20px;
  font-weight: bold;
  color: #333;
  margin-bottom: 10px;
}

.box-description {
  font-size: 16px;
  color: #666;
}
</style>
