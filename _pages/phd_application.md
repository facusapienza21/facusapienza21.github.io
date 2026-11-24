---
layout: page
permalink: /phd-application/
title: PhD Application Form
description: Mass balance modelling of Andean glaciers via physics-informed machine learning · SIDERAL · IGE Grenoble
nav: false
---

{% assign form_pdf = '/assets/pdf/phd_application_form.pdf' | relative_url %}

<p class="pdf-viewer-intro">
  Download the form, fill it in with any PDF reader and save it as <code>&lt;Last Name&gt;_form.pdf</code>.
  <strong>Deadline: Tuesday, December 22, 2026, 23:59 CET.</strong>
</p>

<div class="pdf-viewer-actions">
  <a href="{{ form_pdf }}" download="phd_application_form.pdf" class="btn z-depth-0" role="button">
    <i class="material-icons">file_download</i> Download form (PDF)
  </a>
  <a href="{{ form_pdf }}" target="_blank" class="btn z-depth-0" role="button">
    <i class="material-icons">open_in_new</i> Open in new tab
  </a>
</div>

<object class="pdf-viewer" data="{{ form_pdf }}#navpanes=0&view=FitH" type="application/pdf">
  <p class="pdf-viewer-fallback">
    Your browser cannot display the PDF here.
    <a href="{{ form_pdf }}" download="phd_application_form.pdf">Download the application form</a> instead.
  </p>
</object>

<p class="mt-3"><a href="{{ '/people/' | relative_url }}">&larr; Back to open positions</a></p>
