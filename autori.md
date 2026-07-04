---
layout: default
title: Autrici
permalink: /autori/
---

<h1 class="page-title">Le Autrici</h1>

<div class="authors-grid">
{% for author in site.authors %}
    <div class="author-card">
        <h2>{{ author.name }}</h2>
        <p class="author-role">{{ author.pillar | capitalize }}</p>
        <p>{{ author.bio }}</p>

        {% assign author_posts = site.posts | where: "author", author.slug %}
        <p class="author-stats">{{ author_posts.size }} articoli pubblicati</p>

        <h3>Ultimi articoli:</h3>
        <ul>
        {% for post in author_posts limit: 5 %}
            <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a></li>
        {% endfor %}
        </ul>
    </div>
{% endfor %}
</div>

<style>
.page-title {
    font-family: 'Marcellus', serif;
    color: var(--teal-primario);
    text-align: center;
    margin-bottom: 2rem;
}

.authors-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
    gap: 2rem;
}

.author-card {
    background: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.author-card h2 {
    font-family: 'Marcellus', serif;
    color: var(--teal-primario);
    margin-bottom: 0.5rem;
}

.author-role {
    color: var(--salvia-accent);
    font-style: italic;
    margin-bottom: 1rem;
}

.author-stats {
    background: var(--sabbia);
    padding: 0.5rem 1rem;
    border-radius: 4px;
    display: inline-block;
    margin: 1rem 0;
    font-weight: 600;
    color: var(--teal-primario);
}

.author-card h3 {
    color: var(--inchiostro);
    font-size: 1rem;
    margin: 1.5rem 0 0.5rem;
}

.author-card ul {
    list-style: none;
}

.author-card li {
    padding: 0.3rem 0;
}

.author-card a {
    color: var(--inchiostro);
    text-decoration: none;
}

.author-card a:hover {
    color: var(--teal-primario);
}
</style>
