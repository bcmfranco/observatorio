<template>
  <div class="landing-page">
    <header class="header">
      <h1>Observatorio cognitivo</h1>
      <p>Explore the world of cognitive science with us.</p>
      <button class="cta-button">Get Started</button>
    </header>
    <section class="features">
      <div class="feature">
        <h2>Research</h2>
        <p>Stay updated with the latest research and developments.</p>
      </div>
      <div class="feature">
        <h2>Resources</h2>
        <p>Access a wide range of cognitive science resources.</p>
      </div>
      <div class="feature">
        <h2>Community</h2>
        <p>Join a community of like-minded individuals.</p>
      </div>
    </section>
    <footer class="footer">
      <p>&copy; 2024 Cognitive Observatory. All rights reserved.</p>
    </footer>
  </div>
</template>

<style>
.landing-page {
  font-family: 'Roboto', sans-serif;
  color: #333;
  text-align: center;
  padding: 0 20px;
}

.header {
  background: linear-gradient(135deg, #6200ea, #03dac6);
  color: white;
  padding: 50px 20px;
  margin-bottom: 40px;
}

.header h1 {
  font-size: 3em;
  margin: 0;
}

.header p {
  font-size: 1.2em;
  margin: 20px 0;
}

.cta-button {
  background-color: #03dac6;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 1em;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.cta-button:hover {
  background-color: #018786;
}

.features {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  margin-bottom: 40px;
}

.feature {
  background-color: #f5f5f5;
  padding: 20px;
  border-radius: 8px;
  margin: 10px;
  width: 30%;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s;
}

.feature:hover {
  transform: translateY(-10px);
}

.feature h2 {
  color: #6200ea;
  margin-bottom: 10px;
}

.footer {
  background-color: #6200ea;
  color: white;
  padding: 20px 0;
}

.footer p {
  margin: 0;
}
</style>
