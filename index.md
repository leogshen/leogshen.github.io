---
title: SepSentinel Timeline
---

<style>
:root { color-scheme: light; }
* { box-sizing: border-box; }
body { margin: 0; background: #f6f8fb; color: #172033; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif; }
.timeline-shell { width: min(100% - 32px, 680px); margin: 0 auto; padding: 56px 0 80px; }
.site-header { margin-bottom: 38px; text-align: center; }
.site-header h1 { margin: 0 0 10px; font-size: clamp(2.2rem, 7vw, 4rem); letter-spacing: -0.055em; }
.site-header p { margin: 0 auto; max-width: 540px; color: #687287; font-size: 1.05rem; line-height: 1.6; }
.timeline { position: relative; display: grid; gap: 30px; }
.timeline::before { content: ""; position: absolute; left: -17px; top: 18px; bottom: 18px; width: 2px; background: #dce3ed; }
.post-card { position: relative; overflow: hidden; background: #fff; border: 1px solid #e3e8ef; border-radius: 18px; box-shadow: 0 12px 34px rgba(27, 39, 66, .08); }
.post-card::before { content: ""; position: absolute; left: -23px; top: 22px; width: 10px; height: 10px; border: 3px solid #f6f8fb; border-radius: 50%; background: #2563eb; }
.post-card img { display: block; width: 100%; max-height: 660px; object-fit: cover; background: #eef2f7; }
.post-body { padding: 22px 24px 24px; }
.post-date { color: #2563eb; font-size: .78rem; font-weight: 750; letter-spacing: .09em; text-transform: uppercase; }
.post-title { margin: 8px 0 10px; font-size: 1.45rem; letter-spacing: -.025em; }
.post-title a { color: inherit; text-decoration: none; }
.post-title a:hover { color: #2563eb; }
.post-excerpt { color: #566176; line-height: 1.65; }
.post-excerpt p { margin: 0; }
.read-more { display: inline-block; margin-top: 16px; color: #2563eb; font-weight: 700; text-decoration: none; }
.empty-state { padding: 44px 28px; text-align: center; background: #fff; border: 1px dashed #c8d1de; border-radius: 18px; color: #687287; }
.site-footer { margin-top: 44px; text-align: center; color: #8a94a6; font-size: .9rem; }
@media (max-width: 720px) { .timeline::before, .post-card::before { display: none; } .timeline-shell { padding-top: 36px; } }
</style>

<div class="timeline-shell">
  <header class="site-header">
    <h1>SepSentinel</h1>
    <p>Timeline, progress log, and achievements from our work toward earlier, smarter sepsis monitoring.</p>
  </header>

  <main class="timeline" aria-label="SepSentinel project timeline">
    {% if site.posts.size > 0 %}
      {% for post in site.posts %}
        <article class="post-card">
          {% if post.image %}
            <a href="{{ post.url | relative_url }}">
              <img src="{{ post.image | relative_url }}" alt="{{ post.image_alt | default: post.title | escape }}">
            </a>
          {% endif %}
          <div class="post-body">
            <time class="post-date" datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%B %-d, %Y" }}</time>
            <h2 class="post-title"><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
            <div class="post-excerpt">{{ post.excerpt }}</div>
            <a class="read-more" href="{{ post.url | relative_url }}">View update →</a>
          </div>
        </article>
      {% endfor %}
    {% else %}
      <div class="empty-state">
        <h2>The timeline starts here.</h2>
        <p>Our first visual project update is coming soon.</p>
      </div>
    {% endif %}
  </main>

  <footer class="site-footer">SepSentinel · Building toward earlier warning for sepsis</footer>
</div>
