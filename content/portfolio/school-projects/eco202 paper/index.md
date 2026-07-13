---
title: "ECO202 Research Paper"
draft: false
slug: "eco202-paper"
params:
  hideMeta: true
---

This paper is my ECO202 research assignment on government spending and 

<div id="pdf-viewer" style="border: 1px solid #ddd; padding: 12px; background: #fafafa;"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<script>
  const pdfUrl = '/eco202%20research%20paper%20to%20post%20on%20github.pdf';
  const viewer = document.getElementById('pdf-viewer');

  if (window.pdfjsLib) {
    pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';

    pdfjsLib.getDocument(pdfUrl).promise.then(function(pdf) {
      const pagePromises = [];
      for (let pageNumber = 1; pageNumber <= pdf.numPages; pageNumber++) {
        pagePromises.push(pdf.getPage(pageNumber));
      }
      return Promise.all(pagePromises);
    }).then(function(pages) {
      const fragment = document.createDocumentFragment();
      pages.forEach(function(page) {
        const scale = 2.0;
        const viewport = page.getViewport({ scale: scale });
        const canvas = document.createElement('canvas');
        const context = canvas.getContext('2d');
        canvas.width = viewport.width;
        canvas.height = viewport.height;
        canvas.style.width = '100%';
        canvas.style.height = 'auto';
        canvas.style.border = '1px solid #ddd';
        canvas.style.marginBottom = '12px';
        canvas.style.background = '#fff';
        canvas.style.imageRendering = 'auto';
        context.imageSmoothingEnabled = true;
        context.imageSmoothingQuality = 'high';
        fragment.appendChild(canvas);

        page.render({ canvasContext: context, viewport: viewport }).promise.catch(function(error) {
          console.error('Failed to render PDF page', error);
        });
      });

      viewer.innerHTML = '';
      viewer.appendChild(fragment);
    }).catch(function(error) {
      viewer.innerHTML = '<p>Unable to load the PDF preview right now.</p>';
      console.error('Failed to load PDF', error);
    });
  } else {
    viewer.innerHTML = '<p>PDF viewer is unavailable in this browser.</p>';
  }
</script>
>