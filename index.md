---
title: "Home"
---

<style>
.carousel { 
  position: relative; 
  overflow: hidden; 
}

.carousel-track {
  display: flex;
  gap: 1rem;
  flex-wrap: nowrap;
  overflow-x: auto;
  scroll-behavior: smooth;
  padding-bottom: .25rem;
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.carousel-track::-webkit-scrollbar { 
  display: none; 
}

.carousel .card { 
  flex: 0 0 300px; 
}

.profile-pic {
  width: 220px;
  height: 220px;
  border-radius: 50%;
  object-fit: cover;
  object-position: center 25%;
  transform: scale(0.9);
}
</style>


<section id="about" class="section">
<div class="about-container">

<img src="{{ '/assets/images/rachid.png' | relative_url }}"
     alt="Rachid Hamadou"
     class="profile-pic">

<div class="about-text">

<h1>Hello World! I'm Rachid Abou Djamal Hamadou</h1>

<p>Data Science & AI Enthusiast | Cloud Technologies | Student</p>

<p>
Curious about data, artificial intelligence and modern technologies,
I enjoy building projects that explore how data can be processed,
analyzed and transformed into useful insights.
</p>

<p>
<strong>Core skills:</strong>
Python · SQL · Data Analysis · Cloud Computing · Machine Learning
</p>

<p class="social-links">

<a href="https://www.linkedin.com/in/rachid-abou-djamal-hamadou"
   target="_blank"
   aria-label="LinkedIn">
<i class="fa-brands fa-linkedin"></i>
</a>

<a href="https://github.com/tole-corne"
   target="_blank"
   aria-label="GitHub">
<i class="fa-brands fa-github"></i>
</a>

</p>

</div>
</div>
</section>


<section id="projects" class="section">

<div class="section-header">
<h2>🚀 Projects</h2>

<a class="view-all"
   href="https://github.com/tole-corne"
   target="_blank"
   rel="noopener">
All repos →
</a>

</div>

{% assign projects_count = site.data.projects | size %}

{% if projects_count > 4 %}

<div class="carousel">

<button class="scroll-btn left"
        data-target="#projects-track"
        aria-label="Scroll projects left">‹</button>

<div id="projects-track"
     class="carousel-track"
     role="region"
     aria-label="Projects list">

{% for item in site.data.projects %}

<article class="card">

<a class="thumb"
   href="{{ item.link }}"
   target="_blank"
   rel="noopener">

<img src="{{ item.image | default: '/assets/images/placeholder_project.jpg' | relative_url }}"
     alt="{{ item.title | escape }}"
     loading="lazy">

</a>

<div class="card-body">

<h3 class="card-title">
<a href="{{ item.link }}" target="_blank">
{{ item.title }}
</a>
</h3>

<p class="card-text">
{{ item.description }}
</p>

{% if item.stack %}
<p class="card-tags">{{ item.stack }}</p>
{% endif %}

<div class="card-actions">

{% if item.screenshot %}
<a href="#"
   class="btn ghost"
   data-lightbox-src="{{ item.screenshot | relative_url }}">
Preview
</a>
{% endif %}

<a class="btn"
   href="{{ item.link }}"
   target="_blank">
Open
</a>

</div>
</div>
</article>

{% endfor %}
</div>

<button class="scroll-btn right"
        data-target="#projects-track"
        aria-label="Scroll projects right">›</button>

</div>

{% endif %}

</section>


<script>
(function () {

function init(btn) {

var targetSel = btn.getAttribute('data-target');
var track = document.querySelector(targetSel);
if (!track) return;

var step = Math.max(300, Math.floor(track.clientWidth * 0.9));

btn.addEventListener('click', function () {

track.scrollBy({
left: btn.classList.contains('left') ? -step : step,
behavior: 'smooth'
});

});

function update() {

var max = track.scrollWidth - track.clientWidth - 1;
var x = track.scrollLeft;

var leftBtn = track.parentElement.querySelector('.scroll-btn.left');
var rightBtn = track.parentElement.querySelector('.scroll-btn.right');

if (leftBtn) leftBtn.disabled = x <= 0;
if (rightBtn) rightBtn.disabled = x >= max;

}

track.addEventListener('scroll', update, { passive: true });
window.addEventListener('resize', update);

update();

}

document.querySelectorAll('.scroll-btn').forEach(init);

})();
</script>
