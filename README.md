# Brad's Toolbox

Free tools that run entirely in the browser, hosted on GitHub Pages at
**https://bradploeger.github.io**.

## Tools

| Tool | Path | What it does |
| --- | --- | --- |
| Plotline Grapher | [`/tools/grapher/`](https://bradploeger.github.io/tools/grapher/) | Graphing calculator: functions, implicit equations (e.g. elliptic curves `y^2 = x^3 + ax + b`), modular equations (`... (mod p)`), parameter sliders, roots, intersections, table of values |
| NEXRAD Volume Viewer | [`/tools/nexrad/`](https://bradploeger.github.io/tools/nexrad/) | 3D viewer for NEXRAD Level II radar volumes: decodes the file in the browser and shows it as points, a ray-marched volume, or reflectivity shells (REF, VEL, SW, ZDR, PHI, RHO). Loads latest or archived scans from NOAA's public AWS bucket, a local file, or the bundled Moore, OK 2013 sample in `tools/nexrad/samples/` |

## Layout

```
index.html            Home page listing every tool
404.html              Shown for unknown URLs
assets/site.css       Shared styles for the home and 404 pages
assets/favicon.svg    Site icon
tools/<name>/index.html   One folder per tool, each a self-contained page
.nojekyll             Serve files as-is (skip Jekyll processing)
```

Every tool is a single static HTML file. There is no build step and no server code.
External libraries load from public CDNs (the grapher uses math.js 11.8.0 from cdnjs).
The NEXRAD viewer has its scripts (Three.js, the Level II decoder) inlined in its page.

## Adding a tool

1. Create `tools/<name>/index.html`. Link back home with `<a href="/">← Brad's Toolbox</a>`
   and add `<link rel="icon" href="/assets/favicon.svg">` in the head.
2. In `index.html`, copy the existing `<li>` inside `<ul class="tools">`, point its `href`
   at `/tools/<name>/`, and update the title, description, tags and preview SVG.
3. Add a row to the table above, then commit and push. GitHub Pages republishes within a minute or two.

## Running locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Links use root-relative paths (`/tools/...`), so open the site through a local server
rather than double-clicking the files.
