---
layout: page
title: Triathlon
permalink: /triathlon/
---

## My Triathlon Database

<div id="triathlon-table">Loading...</div>

<script>
fetch('/data/all_combined.tsv')
  .then(res => res.text())
  .then(tsv => {
    const rows = tsv.trim().split('\n').map(r => r.split('\t'));
    const headers = rows[0];
    const data = rows.slice(1);

    let html = '<table><thead><tr>';
    headers.forEach(h => html += `<th>${h}</th>`);
    html += '</tr></thead><tbody>';
    data.forEach(row => {
      html += '<tr>';
      row.forEach(cell => html += `<td>${cell}</td>`);
      html += '</tr>';
    });
    html += '</tbody></table>';

    document.getElementById('triathlon-table').innerHTML = html;
  });
</script>
