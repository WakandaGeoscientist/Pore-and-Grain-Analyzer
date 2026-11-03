Pore & Grain Analyser

A single-page web app for quantitative analysis of thin-section photomicrographs and close-up photos of grains. Everything runs in the browser, so images never leave your device and no server or installation is needed.

What it does

The app guides you through five steps:

	1.	Image: load a JPG, PNG or WebP. You can limit the analysis to an area, or analyse that area at full resolution.
	2.	Scale: from a scale bar, the image's real width or height, or the pixel size.
	3.	Pores: automatic first guess, K-means colour groups (2–20), tap-to-teach examples, colour range or brightness threshold, and hand fixes.
	4.	Grains: there are two methods:
	•	an automatic watershed split, steered by grain contacts and colour;
	•	erode & dilate (morphological opening with a disk), as in the companion Python notebook.
You can then merge, split or exclude grains by hand.
	5.	Results:
	•	porosity, and pore and grain size, shape and fabric statistics;
	•	Folk & Ward size statistics;
	•	point counting;
	•	plots (size distributions, area histogram, rose diagram, shape, a scatter explorer);
	•	tables, plus export to CSV and an annotated PNG.

The “Use the same method as the Python notebook” button reproduces the notebook's pipeline:

	•	K-means on RGB with k-means++;
	•	merging groups by role;
	•	binary_erosion / binary_dilation with disk(r);
	•	4-connected scipy.ndimage.label.

Running it

Open index.html in any modern browser (Chrome, Edge, Firefox or Safari). It works offline except for the web fonts, which fall back to system fonts.

Publishing with GitHub Pages

	1.	Create a new repository on GitHub (for example thin-section-analyser).
	2.	Upload index.html, README.md and .nojekyll to the root of the repository: choose Add file → Upload files, drag the files in, then Commit changes.
	3.	Go to Settings → Pages.
	4.	Under Build and deployment, set Source to Deploy from a branch, choose the main branch and the / (root) folder, then Save.
	5.	After a minute or two the site is live at https://<your-username>.github.io/<repository-name>/. The address is shown at the top of the Pages settings.

To update the app later, upload a new index.html over the old one and commit; Pages redeploys automatically.

Limits

	•	Browsers can hold roughly 12 megapixels for analysis on a computer and 6 on a phone. Larger images, such as whole rock slabs, are analysed at reduced size. For exact agreement with full-resolution Python results, draw an area and use Analyse the drawn area at full resolution.
	•	TIFF files must be converted to JPG or PNG first.
	•	Section sizes are apparent 2D sizes, and areal porosity misses microporosity below image resolution.
