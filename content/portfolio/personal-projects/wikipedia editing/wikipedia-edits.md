---
title: "Wikipedia edits"
draft: false
slug: "wikipedia-edits"
params:
  hideMeta: true
  hiddenInHomeList: true
---

I help maintain Wikipedia by contributing edits that improve the quality and clarity of information, especially by finding and cleaning polling data related to Canadian elections.

<p><strong>Current live edit count:</strong> <span id="wiki-edit-count">Loading…</span></p>

<script>
  const username = 'CGP05';
  const countEl = document.getElementById('wiki-edit-count');

  fetch(`https://xtools.wmcloud.org/api/user/editcount/${encodeURIComponent(username)}?format=json`)
    .then(function (response) {
      if (!response.ok) {
        throw new Error('Network response was not ok');
      }
      return response.json();
    })
    .then(function (data) {
      const count = data && data.editcount ? data.editcount : 'unknown';
      countEl.textContent = count;
    })
    .catch(function () {
      countEl.textContent = 'unavailable';
    });
</script>
