<template>
  <section class="contact-section">
    <div class="contact-container">
      <h2 class="title">Get In Touch<span>.</span></h2>
      <p class="subtitle">Have a question or want to work together? Drop me a message.</p>

      <form 
        action="https://formspree.io/f/mqenwjpa" 
        method="POST"
        class="contact-form"
      >
        <div class="input-group">
          <label for="name">Name</label>
          <input type="text" id="name" name="name" placeholder="John Doe" required />
        </div>

        <div class="input-group">
          <label for="email">Email</label>
          <input type="email" id="email" name="email" placeholder="john@example.com" required />
        </div>

        <div class="input-group">
          <label for="message">Message</label>
          <textarea id="message" name="message" rows="5" placeholder="How can I help you?" required></textarea>
        </div>

        <button type="submit" class="submit-btn">
          Send Message
          <span class="paper-plane">↗</span>
        </button>
      </form>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  padding: 5rem 10%;
  display: flex;
  justify-content: center;
}

.contact-container {
  max-width: 600px;
  width: 100%;
}

.title {
  font-family: 'JetBrains Mono', monospace;
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
}

.title span { color: #10b981; }

.subtitle {
  color: #94a3b8;
  margin-bottom: 3rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.input-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.8rem;
  color: #10b981;
  text-transform: uppercase;
  letter-spacing: 1px;
}

input, textarea {
  background: rgba(30, 41, 59, 0.3);
  border: 1px solid rgba(255, 255, 255, 0.1);
  border-radius: 8px;
  padding: 0.8rem 1rem;
  color: white;
  font-family: 'Inter', sans-serif;
  transition: all 0.3s ease;
}

input:focus, textarea:focus {
  outline: none;
  border-color: #10b981;
  background: rgba(30, 41, 59, 0.5);
  box-shadow: 0 0 10px rgba(16, 185, 129, 0.1);
}

.submit-btn {
  margin-top: 1rem;
  background: #ffffff;
  color: #000000;
  border: none;
  padding: 1rem;
  border-radius: 8px;
  font-weight: 700;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  transition: all 0.3s ease;
}

.submit-btn:hover {
  transform: translateY(-3px);
  background: #10b981;
  color: white;
}

.paper-plane {
  font-size: 1.1rem;
}
</style>