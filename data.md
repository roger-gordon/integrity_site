---
title: status
layout: landing
description: 'what is in the graph'
image: assets/images/pic05.jpg
nav-menu: true
nav-order: 5
show_tile: false
---

<div id="main">
<section id="one">
	<div class="inner">

		<h2>{{ site.data.stats.data_points }} in {{ site.data.stats.relationships }}</h2>
		<p>Integrity is built on the complete OpenAlex scholarly catalogue — every work, every author, every institution, every publisher, every source, every funder, every award, every topic, and the billions of connections between them. With clear provenance and update information.</p>

		<hr />

    <p>When you want to refresh an Author and their Works, simply tell Integrity. It updates in the background and keeps you informed, so you can keep researching without waiting. The most up to date information indexed now...</p>
    
		<hr />

		<h2>Major Data Points</h2>
		<div>
			<table id="integrity-stats-table" style="width:100%; border-collapse:collapse;">
				<colgroup>
					<col style="width:35%;">
					<col style="width:45%;">
					<col style="width:20%;">
				</colgroup>
				<tbody>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Works</strong></td><td id="stat-Work-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Work">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Authors</strong></td><td id="stat-Author-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Author">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Institutions</strong></td><td id="stat-Institution-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Institution">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Sources</strong></td><td id="stat-Source-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Source">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Publishers</strong></td><td id="stat-Publisher-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Publisher">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Funders</strong></td><td id="stat-Funder-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Funder">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Awards</strong></td><td id="stat-Award-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Award">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Topics</strong></td><td id="stat-Topic-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Topic">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Topic Keywords</strong></td><td id="stat-Topic_Keyword-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Topic_Keyword">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Source Societies</strong></td><td id="stat-Source_Society-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Source_Society">&mdash;</td></tr>
					<tr><td style="padding:6px 24px 6px 0;"><strong>Sustainable Development Goals</strong></td><td id="stat-Sustainable_Development_Goal-desc" style="color:#999; font-size:0.9em; padding:6px 16px 6px 0;"></td><td style="text-align:right; font-weight:bold; padding:6px 0;" id="stat-Sustainable_Development_Goal">&mdash;</td></tr>
				</tbody>
			</table>
		</div>

		<p id="integrity-loader-note" style="display:none; margin-top:0.5em; font-size:0.9em;">
			<span id="integrity-loader-dot" style="color:#888;">&#9679;</span> <span id="integrity-loader-text">Checking&hellip;</span>
		</p>
		<p id="integrity-updated-at" style="margin-top:0.5em; font-size:0.85em; color:#aaa;"></p>

		<hr />

		<h2>Relationships</h2>
		<p>Billions of connections linking linking every researcher, work, institution, funder, publisher, source and topic to every other &mdash; citations, affiliations, funding trails, classifications, co-authorships, and more.</p>

		<hr />

    <p>Data sourced from <a href="https://openalex.org" target="_blank">OpenAlex</a></p>
    
    <ul class="actions" style="margin-top: 2em;">
        <li><a href="/play.html" class="button next">explore</a></li>
        <li><a href="/contact" class="button">get in touch</a></li>
    </ul>

	</div>
</section>
</div>

<script>
(function () {
  var STATUS_URL = "https://integritystatus.blob.core.windows.net/public/status.json";

  function fmt(n) {
    // Format integer with locale thousands separators
    return typeof n === "number" ? n.toLocaleString() : "—";
  }

  function setEl(id, text) {
    var el = document.getElementById(id);
    if (el) el.textContent = text;
  }

  fetch(STATUS_URL, { cache: "no-cache" })
    .then(function (r) {
      if (!r.ok) throw new Error("HTTP " + r.status);
      return r.json();
    })
    .then(function (data) {
      var entities = data.entities || [];
      var loaderRunning = !!data.loader_running;

      // Populate each stat cell and description
      entities.forEach(function (e) {
        var countEl = document.getElementById("stat-" + e.label);
        if (countEl) countEl.textContent = fmt(e.count);
        var descEl = document.getElementById("stat-" + e.label + "-desc");
        if (descEl && e.description) descEl.textContent = e.description;
      });

      // Loader indicator — always show, green if running, grey if complete
      var note = document.getElementById("integrity-loader-note");
      var dot  = document.getElementById("integrity-loader-dot");
      var txt  = document.getElementById("integrity-loader-text");
      if (note) note.style.display = "block";
      if (loaderRunning) {
        if (dot) dot.style.color = "#2ecc71";
        if (txt) txt.textContent = "Loader running \u2014 counts update as indexing continues";
      } else {
        if (dot) dot.style.color = "#888";
        if (txt) txt.textContent = "Indexing complete.";
      }

      // Updated at
      if (data.updated_at) {
        var d = new Date(data.updated_at);
        var s = d.toLocaleDateString(undefined, { year: "numeric", month: "long", day: "numeric" })
              + " at "
              + d.toLocaleTimeString(undefined, { hour: "2-digit", minute: "2-digit", timeZoneName: "short" });
        setEl("integrity-updated-at", "Counts as of " + s);
      }
    })
    .catch(function (err) {
      // Fail silently — static dashes remain, no broken UI
      console.warn("Integrity status fetch failed:", err);
    });
})();
</script>
