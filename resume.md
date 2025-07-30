---
layout: single
title: "Моё Резюме"
permalink: /resume/
---

<div style="position: relative; padding-bottom: 140%; height: 0; overflow: hidden;">
  <iframe 
    src="{{ '/assets/files/resume.pdf' | relative_url }}" 
    style="position: absolute; top:0; left: 0; width: 100%; height: 100%;" 
    frameborder="0">
  </iframe>
</div>

<canvas id="pdf-canvas"></canvas>
<script>
  const url = "{{ '/assets/files/resume.pdf' | relative_url }}";
  const canvas = document.getElementById('pdf-canvas');
  const ctx = canvas.getContext('2d');
  pdfjsLib.getDocument(url).promise.then(pdf => {
    pdf.getPage(1).then(page => {
      const viewport = page.getViewport({ scale: 1.5 });
      canvas.height = viewport.height;
      canvas.width = viewport.width;
      page.render({ canvasContext: ctx, viewport: viewport });
    });
  });
</script>

[Скачать резюме (PDF)]({{ "/assets/files/resume.pdf" | relative_url }})

<!-- Добавьте всё, что нужно: навыки, сертификаты, проекты -->
