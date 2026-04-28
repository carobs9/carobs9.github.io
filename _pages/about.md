---
permalink: /
title: "Carolina Brañas"
layout: home
author_profile: false
redirect_from:
  - /about/
  - /about.html
---

{% include base_path %}

<section id="about">
<h2>About</h2>

<p>I am a data scientist keen on learning how to build websites. During some months of unemployment, I decided to start this website for fun and to polish it as much as possible.</p>

<p>Besides making this website look pretty, my interests include machine learning, network analysis, natural language processing, and geospatial data.</p>

<h3>Currently</h3>
<p>Collaborating as a research assistant in the <a href="https://www.carlsbergfondet.dk/en/what-we-have-funded/cf25-1677/">Cataloguing Crop Traits and Breeders Across the OECD 1980-2025</a> project (financed by the Carlsberg Foundation).</p>

<h3>Core Skills</h3>
<ul>
  <li>Machine Learning</li>
  <li>NLP (Transformers, Topic Modeling, RAG)</li>
  <li>Python (pandas, numpy, scikit-learn, PyTorch, TensorFlow)</li>
  <li>Geospatial (Geopandas, Rasterio, QGIS)</li>
  <li>Data Visualization (Matplotlib, Seaborn, Tableau, Power BI)</li>
  <li>Docker, Git, AWS, UCloud, CI/CD, ETL, SQL</li>
</ul>
</section>

<section id="projects">
<h2>Projects</h2>

{% for post in site.portfolio %}
  <div class="home-entry">
    <h3><a href="{{ base_path }}{{ post.url }}">{{ post.title }}</a></h3>
    {% if post.excerpt %}
      <p>{{ post.excerpt | markdownify | remove: '<p>' | remove: '</p>' }}</p>
    {% endif %}
  </div>
{% endfor %}
</section>

<section id="publications">
<h2>Research collaborations</h2>

<p class="section-intro">Papers I've contributed to as a research assistant. I am not listed as an author — credit goes to the authors below.</p>

{% for post in site.publications reversed %}
  <div class="home-entry">
    {% if post.my_role %}<span class="role-badge">{{ post.my_role }}</span>{% endif %}
    <h3>{% if post.paperurl %}<a href="{{ post.paperurl }}">{{ post.title }}</a>{% else %}{{ post.title }}{% endif %}</h3>
    {% if post.authors %}
      <p class="home-entry-authors">By {{ post.authors | join: ', ' }}</p>
    {% endif %}
    <p class="home-entry-meta">
      {% if post.venue %}<em>{{ post.venue }}</em>{% endif %}
      {% if post.date %} · {{ post.date | date: "%Y" }}{% endif %}
    </p>
    {% if post.excerpt %}
      <p>{{ post.excerpt | markdownify | remove: '<p>' | remove: '</p>' }}</p>
    {% endif %}
    {% if post.news_url %}
      <p>📰 Press: <a href="{{ post.news_url }}">{{ post.news_title | default: 'News article' }}</a></p>
    {% endif %}
  </div>
{% endfor %}
</section>

<section id="cv">
<h2>CV</h2>

<p>You can access a PDF version of my CV <a href="/files/Carolina_Branas_Resume_no_pic.pdf">here</a>.</p>

<h3>Summary</h3>
<p>Data Scientist with hands-on experience building machine learning and NLP models (including RAG and topic modeling) and scalable containerized data workflows. Interests span network analysis, geospatial data, and applied machine learning for actionable insights.</p>

<h3>Experience</h3>

<div class="timeline">

  <div class="timeline-item">
    <div class="timeline-date">Feb 2026 – Present</div>
    <h4>Research Assistant, Data Science</h4>
    <div class="timeline-org">University of Copenhagen</div>
    <ul>
      <li>Collaborating as a research assistant in the <a href="https://www.carlsbergfondet.dk/en/what-we-have-funded/cf25-1677/">Cataloguing Crop Traits and Breeders Across the OECD 1980-2025</a> project (financed by the Carlsberg Foundation).</li>
      <li>Building a unified database with all new cereal varieties released in the OECD since 1980, their traits and breeding history, and information about the companies involved in developing them.</li>
      <li>The database will be the first large, unified database of its kind, and will be instrumental for exploring how to improve the crop innovation system to increase the global food supply without expanding cropland into pristine environments.</li>
    </ul>
  </div>

  <div class="timeline-item">
    <div class="timeline-date">May 2024 – Dec 2025</div>
    <h4>Research Assistant, Data Science</h4>
    <div class="timeline-org">University of Copenhagen — with Prof. Jeanet Sinding Bentzen</div>
    <ul>
      <li>Contributed to the Shocking Religion project, which examines how faith-based initiatives in the US shaped religiosity and conservative-religious social views. Press coverage: <a href="https://www.economics.ku.dk/news/news/faith-based-initiatives-increase-religiosity-and-conservatism-in-the-united-states/">UCPH Department of Economics</a>.</li>
      <li>Built topic models to uncover thematic trends in text data.</li>
      <li>Built RAG-based LLM pipelines for document insights.</li>
      <li>Designed and containerized scalable ingestion &amp; preprocessing workflows (UCloud).</li>
      <li>Coordinated with multidisciplinary research team.</li>
    </ul>
  </div>

  <div class="timeline-item">
    <div class="timeline-date">Oct 2023 – May 2024</div>
    <h4>Data Scientist</h4>
    <div class="timeline-org">Above Sports, Denmark</div>
    <ul>
      <li>Automated data workflows to improve efficiency.</li>
      <li>Developed computer vision brand logo detection models.</li>
      <li>Dockerized solutions for reproducible ML workflows.</li>
      <li>Collaborated with product to refine output quality.</li>
    </ul>
  </div>

  <div class="timeline-item">
    <div class="timeline-date">Sep 2021 – May 2022</div>
    <h4>Marketing Strategist</h4>
    <div class="timeline-org">Crescendo Collective, United States</div>
    <ul>
      <li>Analyzed campaign performance (Google Analytics, Ads).</li>
      <li>Automated internal reporting with Python scripts.</li>
      <li>Competitor analysis and audience benchmarks; stakeholder reporting.</li>
    </ul>
  </div>

</div>

<h3>Education</h3>

<div class="timeline">

  <div class="timeline-item">
    <div class="timeline-date">2022 – 2024</div>
    <h4>M.Sc. Social Data Science</h4>
    <div class="timeline-org">University of Copenhagen</div>
    <ul>
      <li>Thesis: <a href="/projects/masters-thesis/">Mobility and income segregation in Madrid, Spain</a>.</li>
      <li>Selected courses: Advanced Machine Learning (ITU), Geospatial Data Science (ITU), Advanced Network Science (ITU), Natural Language Processing (DIKU, University of Copenhagen).</li>
    </ul>
  </div>

  <div class="timeline-item">
    <div class="timeline-date">2018 – 2022</div>
    <h4>B.Sc. Marketing and Computer Science Minor</h4>
    <div class="timeline-org">Cardinal Stritch University</div>
    <ul>
      <li>Magna Cum Laude.</li>
      <li>Dean's List (2018–2022).</li>
      <li>Best Graduating GPA (Marketing, 2022).</li>
    </ul>
  </div>

</div>

<h3>Skills</h3>
<ul>
  <li><strong>Programming &amp; Data:</strong> Python (pandas, numpy, matplotlib, tensorflow, pytorch, scikit-learn), SQL, Bash</li>
  <li><strong>ML &amp; NLP:</strong> Transformers, RAG, Topic Modeling (UMAP, HDBSCAN, BERTopic), Computer Vision, Predictive Modeling, Feature Engineering</li>
  <li><strong>Visualization &amp; Analysis:</strong> Matplotlib, Seaborn, Tableau, Power BI, Statistical Analysis, Data Wrangling</li>
  <li><strong>Geospatial:</strong> Geopandas, Rasterio, QGIS, Spatial Analysis</li>
  <li><strong>Cloud &amp; DevOps:</strong> Docker, Git, Linux, AWS, UCloud, CI/CD, VSCode</li>
  <li><strong>Other:</strong> LaTeX, Overleaf, Statistics</li>
</ul>

<h3>Languages</h3>
<ul>
  <li>Spanish (Native)</li>
  <li>Galician (Native)</li>
  <li>English (Professional)</li>
  <li>Danish (Beginner)</li>
</ul>

<h3>Awards</h3>
<ul>
  <li><strong>Dean's List (2018–2022):</strong> GPA above 3.5 each semester.</li>
  <li><strong>Best Graduating GPA Marketing B.Sc. (2022).</strong></li>
  <li><strong>Academic and Athletic Grant (2018–2022):</strong> Full scholarship for academic excellence and soccer performance.</li>
</ul>
</section>
