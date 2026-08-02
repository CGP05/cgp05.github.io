---
title: "ECO202 research paper"
draft: false
slug: "eco202-paper"
params:
  hideMeta: true
  hiddenInHomeList: true
---

This paper is my ECO202 research assignment on government spending and GDP growth in Canada over the past approximately 40 years, with statistical analysis done in Python (specifically with the packages pandas, numpy, matplotlib, statsmodels)

<h3>PDF of the paper</h3>
<div id="pdf-controls" style="display:flex;flex-wrap:wrap;gap:10px;align-items:center;margin-bottom:12px;">
  <button id="pdf-prev" type="button" style="padding:8px 12px;">Previous</button>
  <button id="pdf-next" type="button" style="padding:8px 12px;">Next</button>
  <span id="pdf-page-info" style="font-weight:600;">Page 1 / 1</span>
  <label style="display:flex;align-items:center;gap:6px;">Zoom:
    <select id="pdf-scale" style="padding:6px 8px;">
      <option value="0.75">75%</option>
      <option value="1.0">100%</option>
      <option value="1.25" selected>125%</option>
      <option value="1.5">150%</option>
      <option value="2.0">200%</option>
    </select>
  </label>
  <a href="/pdfs/eco202%20research%20paper%20to%20post%20on%20github.pdf" target="_blank" rel="noopener noreferrer" style="padding:8px 12px;border:1px solid #ddd;border-radius:6px;background:#fff;color:#0366d6;text-decoration:none;">Open full PDF</a>
</div>
<div id="pdf-viewer" style="border: 1px solid #ddd; padding: 12px; background: #fafafa; max-width: 900px;">
  <canvas id="pdf-canvas" style="width:100%;height:auto;display:block;margin:auto;background:#fff;border:1px solid #ddd;"></canvas>
</div>

<h3>Analysis notebook</h3>
<p>You can view the notebook below, or <a href="https://github.com/CGP05/ECO202-government-spending-and-economic-growth-paper/blob/main/canada_deficit_growth_colab_notebook%20by%20shazia.ipynb" target="_blank" rel="noopener noreferrer">open it on GitHub</a>.</p>
<iframe src="https://nbviewer.org/github/CGP05/ECO202-government-spending-and-economic-growth-paper/blob/main/canada_deficit_growth_colab_notebook%20by%20shazia.ipynb" width="100%" height="900px" style="border: 1px solid #ddd; background: white;"></iframe>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<script>
  const pdfUrl = '/pdfs/eco202%20research%20paper%20to%20post%20on%20github.pdf';
  const viewer = document.getElementById('pdf-viewer');
  const canvas = document.getElementById('pdf-canvas');
  const pageInfo = document.getElementById('pdf-page-info');
  const prevButton = document.getElementById('pdf-prev');
  const nextButton = document.getElementById('pdf-next');
  const scaleSelect = document.getElementById('pdf-scale');

  if (window.pdfjsLib) {
    pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';

    let pdfDoc = null;
    let currentPage = 1;
    let currentScale = parseFloat(scaleSelect.value);

    function updateButtons() {
      prevButton.disabled = currentPage <= 1;
      nextButton.disabled = currentPage >= (pdfDoc ? pdfDoc.numPages : 1);
    }

    function renderPage(pageNumber) {
      pdfDoc.getPage(pageNumber).then(function(page) {
        const viewport = page.getViewport({ scale: currentScale });
        const context = canvas.getContext('2d');
        canvas.width = viewport.width;
        canvas.height = viewport.height;
        page.render({ canvasContext: context, viewport: viewport }).promise.catch(function(error) {
          console.error('Failed to render PDF page', error);
        });
        pageInfo.textContent = `Page ${pageNumber} / ${pdfDoc.numPages}`;
        updateButtons();
      }).catch(function(error) {
        console.error('Failed to load PDF page', error);
      });
    }

    pdfjsLib.getDocument(pdfUrl).promise.then(function(pdf) {
      pdfDoc = pdf;
      renderPage(currentPage);
    }).catch(function(error) {
      viewer.innerHTML = '<p>Unable to load the PDF preview right now.</p>';
      console.error('Failed to load PDF', error);
    });

    prevButton.addEventListener('click', function() {
      if (currentPage > 1) {
        currentPage -= 1;
        renderPage(currentPage);
      }
    });

    nextButton.addEventListener('click', function() {
      if (pdfDoc && currentPage < pdfDoc.numPages) {
        currentPage += 1;
        renderPage(currentPage);
      }
    });

    scaleSelect.addEventListener('change', function() {
      currentScale = parseFloat(scaleSelect.value);
      renderPage(currentPage);
    });
  } else {
    viewer.innerHTML = '<p>PDF viewer is unavailable in this browser.</p>';
  }
</script>
