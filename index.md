---
title: "Home"
---

<style>
.profile-pic {
  width: 220px;
  height: 220px;
  border-radius: 50%;
  object-fit: cover;
  object-position: center;
}

.about-container {
  display: flex;
  align-items: center;
  gap: 30px;
  flex-wrap: wrap;
  padding: 40px 20px;
}

.about-text {
  max-width: 650px;
}

.about-text h1 {
  margin-bottom: 16px;
}

.about-text p {
  margin-bottom: 16px;
}

.projects-section {
  padding: 20px;
}

.projects-section h2 {
  margin-bottom: 20px;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 20px;
}

.project-card {
  border: 1px solid rgba(255,255,255,0.12);
  border-radius: 14px;
  padding: 20px;
  background: rgba(255,255,255,0.02);
}

.project-card h3 {
  margin-top: 0;
  margin-bottom: 10px;
}

.project-card p {
  margin-bottom: 12px;
}

.project-meta {
  font-size: 0.95rem;
  opacity: 0.85;
  margin-bottom: 12px;
}

.project-links a {
  margin-right: 12px;
}
</style>

<section id="about">
  <div class="about-container">
    <img src="/assets/images/rachid.png"
         alt="Rachid Abou Djamal Hamadou"
         class="profile-pic">

    <div class="about-text">
      <h1>Hello World! I'm Rachid Abou Djamal Hamadou</h1>

      <p>Data Science & AI Student | Cloud & Data Technologies</p>

      <p>
        Curious about data, artificial intelligence and modern technologies,
        I enjoy building projects that explore how data can be processed,
        analyzed and transformed into useful insights.
      </p>

      <p>
        <strong>Core skills:</strong>
        Python · SQL · Data Analysis · Cloud Computing · Machine Learning
      </p>

      <p>
        <a href="https://www.linkedin.com/in/rachid-abou-djamal-hamadou" target="_blank" rel="noopener">LinkedIn</a> |
        <a href="https://github.com/tole-corne" target="_blank" rel="noopener">GitHub</a>
      </p>
    </div>
  </div>
</section>

<section id="projects" class="projects-section">
  <h2>Projects</h2>
  <p>Selected repositories from my GitHub profile.</p>

  <div class="projects-grid">
    {% assign repos = site.github.public_repositories | sort: "name" %}
    {% for repo in repos %}
      {% unless repo.fork or repo.name == site.github.repository_name %}
      <article class="project-card">
        <h3>{{ repo.name }}</h3>

        <p>
          {% if repo.description %}
            {{ repo.description }}
          {% else %}
            GitHub repository from my portfolio.
          {% endif %}
        </p>

        <p class="project-meta">
          {% if repo.language %}Main language: {{ repo.language }}{% endif %}
        </p>

        <p class="project-links">
          <a href="{{ repo.html_url }}" target="_blank" rel="noopener">Open Repo</a>
          {% if repo.homepage and repo.homepage != "" %}
            <a href="{{ repo.homepage }}" target="_blank" rel="noopener">Live Demo</a>
          {% endif %}
        </p>
      </article>
      {% endunless %}
    {% endfor %}
  </div>
</section>
