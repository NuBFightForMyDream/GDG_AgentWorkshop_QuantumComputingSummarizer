# Quantum Study Team

A team of AI agents (built with Gemini, run in Antigravity) that turns quantum computing lecture slides and assignments into:

- a written study manual with step-by-step workflows
- an interactive web visualizer you can deploy as a website

## What's inside

```
my-team/
├── .agents/
│   ├── agents/                    # the four worker agents
│   │   ├── quantum-slide-extractor.md
│   │   ├── quantum-content-writer.md
│   │   ├── quantum-visualizer.md
│   │   └── quantum-reviewer.md
│   └── skills/                    # reusable instructions for each agent
│       ├── quantum-slide-processor/   # entry skill that coordinates the team
│       ├── quantum-extraction/
│       ├── quantum-writing/
│       ├── quantum-visualization/
│       └── quantum-review/
├── sources/                       # input: lecture PDFs + assignments
├── scratch/                       # intermediate files (extracted text)
└── outputs/
    ├── quantum_summary_and_workflows.md   # written manual
    └── quantum_visualizer.html            # interactive page (single file)
```

## How the team works

| Step | Agent | Job |
| --- | --- | --- |
| 1 | `quantum-slide-extractor` | Pulls text, equations, diagrams and terms from the slides |
| 2 | `quantum-content-writer` | Writes summaries and step-by-step workflows |
| 3 | `quantum-visualizer` | Turns concepts into Mermaid diagrams and visual specs |
| 4 | `quantum-reviewer` | Checks everything against the original slides |

The `quantum-slide-processor` skill is the entry point. It runs the four steps in order.

## Run the team

1. Install [Antigravity](https://www.antigravity.google/download) and open this `my-team` folder as a project.
2. Put your lecture PDFs in `sources/Lecture/` and assignments in `sources/Assignments/`.
3. Choose the `quantum-slide-processor` skill and ask it to process the slides.
4. Find the results in `outputs/`.

Use **Gemini 3.6 Flash** in Antigravity.

## Preview the website locally

`outputs/quantum_visualizer.html` is one self-contained file. It only loads Tailwind from a CDN, so it needs an internet connection.

```bash
cd outputs
python3 -m http.server 8000
```

Open <http://localhost:8000/quantum_visualizer.html>.

## Deploy the website

Deploy only the HTML file. Do **not** publish `sources/` or `scratch/`, because they contain course PDFs and text extracted from them.

First make a clean folder with the page named `index.html`:

```bash
mkdir -p site
cp outputs/quantum_visualizer.html site/index.html
```

Then pick one option.

### Option A: GitHub Pages (free, easiest with this repo)

1. Push the repo to GitHub.
2. Put `index.html` in a `docs/` folder at the repo root (`cp site/index.html ../docs/index.html`), then commit and push.
3. On GitHub go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to *Deploy from a branch*, branch `main`, folder `/docs`.
5. After about a minute the site is live at `https://<your-username>.github.io/<repo-name>/`.

### Option B: Netlify Drop (no account setup, fastest)

1. Go to <https://app.netlify.com/drop>.
2. Drag the `site/` folder onto the page.
3. You get a public URL immediately. Sign up to keep it permanently or set a custom name.

### Option C: Vercel

```bash
npm i -g vercel
cd site
vercel --prod
```

Accept the defaults. It is a static site with no build step.

### Option D: Firebase Hosting (fits the Google theme)

```bash
npm i -g firebase-tools
firebase login
cd site
firebase init hosting     # public directory: . ; single-page app: No
firebase deploy
```

Your site is served at `https://<project-id>.web.app`.

## Update the site

1. Re-run the team, or edit `outputs/quantum_visualizer.html`.
2. Copy it to `site/index.html` again (or `docs/index.html` for GitHub Pages).
3. Redeploy: push to GitHub, re-drop on Netlify, or rerun `vercel --prod` / `firebase deploy`.

## Troubleshooting

| Problem | Fix |
| --- | --- |
| Page is unstyled | The Tailwind CDN script did not load. Check your connection. For a permanent fix, ask the team to bundle the CSS into the file. |
| 404 after deploying | The file must be named `index.html` and sit at the root of the published folder. |
| GitHub Pages still shows the README | Wait a minute or two, then check that the folder is set to `/docs` in Settings → Pages. |
| Diagrams don't render | Open the browser console (F12) and look for blocked scripts. |

## Copyright

The lecture slides and assignments belong to their authors. Keep them out of any public repo or deployed site unless you have permission.
