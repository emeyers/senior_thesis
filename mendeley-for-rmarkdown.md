# Using Mendeley for R Markdown Citations

**Mendeley** is a reference management tool where you can add all your articles and sources (PDFs, web pages, books). It automatically generates citation information which you can export as a BibTeX file for use in R Markdown.

## Step 1: Export BibTeX from Mendeley

1. Open Mendeley Desktop
2. Select your references
3. **File → Export** or click  **Export** at the bottom of the window
4. Choose format: **BibTeX (*.bib)**
5. Save as `example.bib` in your R Markdown project folder

## Step 2: Understanding your BibTeX File
Your exported `example.bib` file will look like this: 

```bibtex 
@article{smith2020, 
title={Food Safety Inspections and Public Health Outcomes}, 
author={Smith, John and Doe, Jane}, 
journal={Journal of Public Health}, 
year={2020}, 
volume={45}, 
pages={123-145} 
} 
@book{jones2019, 
title={Machine Learning for Policy}, 
author={Jones, Alice}, 
publisher={MIT Press}, 
year={2019} } @article{chen2021, 
title={Geographic Patterns in Restaurant Compliance}, 
author={Chen, Wei and Garcia, Maria}, 
journal={Urban Studies}, year={2021}, 
volume={58}, 
number={3}, 
pages={567-589} 
} 
``` 
**The citation key** is the first thing after the `@article{` or `@book{`: 
-  `smith2020` ← This is the key you'll use 
-   `jones2019` ← This is the key you'll use 

## Step 3: Add to R Markdown YAML Header
```yaml
---
title: "Your Title"
author: "Your Name"
bibliography: example.bib
---
```

## Step 4: Cite in Text

Use citation keys from your BibTeX file:
```markdown
Restaurant inspections reduce illness [@smith2020].

Multiple studies support this [@smith2020; @jones2019].

As Smith et al. [-@smith2020] demonstrated...
```

**Citation formats:**
- `[@smith2020]` 
	- (Smith et al. 2020)
	- (Smith 2020)
	- (Smith and Wilson 2020)
	- (Smith, Wilson, and Rourke 2020)
- `@smith2020`  
	- Smith et al. (2020)
	- Smith (2020)
	- Smith and Wilson (2020)
	- Smith, Wilson, and Rourke (2020)
- `[-@smith2020]`
	- (2020) [suppresses author]

## Step 5: Add References Section

At the end of your document, add:
```markdown
# References
```

**All sources cited from your BibTeX file will automatically populate here when you knit. If there is a source in the file that you did not cite in the R-Markdown document, it won't appear here.**

## Optional: Change Citation Style

Download a CSL file (e.g., APA, Chicago) from https://www.zotero.org/styles

Add to YAML:
```yaml
bibliography: references.bib
csl: apa.csl
```

---

**That's it! Good luck!**
