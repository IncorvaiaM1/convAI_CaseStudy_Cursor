# Cursor case study

Engineering case study for ECE 6256 / CS 6604 Conversational AI, Georgia Tech, Fall 2026. Team: Greyson McReynolds, Michael Incorvaia, Heeba Merchant and Canting Zhu.

We examine Cursor through understanding, state, policy, generation and their interfaces, using public engineering sources and a small coding experiment. The fair presentation uses a printed poster; the former slide deck is archived.

## Start here

| Material | Location | Status |
| --- | --- | --- |
| Reviewed paper | [paper/reviewed/main.tex](paper/reviewed/main.tex) | Current edited source; compilation checked |
| Bibliography and ACL styles | [paper/reviewed/](paper/reviewed/) | Included for compilation |
| Poster PDF | [poster/Cursor_CaseStudy_Poster.pdf](poster/Cursor_CaseStudy_Poster.pdf) | Latest supplied PDF; wording corrections still pending |
| Experiment and evidence | [caseStudyRun/](caseStudyRun/) | Grok patch, annotated transcript, tests and harness |
| Submitted brief | [docs/brief/](docs/brief/) | Earlier planning document |
| Assignment handout | [docs/reference/](docs/reference/) | Course requirements |
| Older drafts | [archive/](archive/) | Retired deck, poster sources, paper and planning drafts |

## Paper

Open `paper/reviewed/main.tex` in a LaTeX editor, or import the entire `paper/reviewed/` directory into Overleaf. The directory includes `custom.bib`, `acl.sty` and `acl_natbib.bst`. With a local TeX installation, run from that directory:

```sh
latexmk -pdf main.tex
```

Compilation was checked with the Codex editor. Confirm the final PDF has no more than four content pages; references are excluded from the assignment's page limit. Generated paper PDFs and LaTeX build files are ignored by Git.

## Poster

Use the PDF in `poster/` as the current visual reference. See [poster/README.md](poster/README.md) for remaining corrections and editable draft locations. The archived deck is not part of the planned presentation.

## Evidence and limitations

The repository includes the Grok run's [saved patch](caseStudyRun/manual_runs/run1_grok-4.6-high-fast.patch), [annotated transcript](caseStudyRun/manual_runs/run1_grok_transcript.md) and [manual log](caseStudyRun/runs_log.csv). Applying the patch to an isolated copy reproduced 10 visible and 9 held-out test passes during review. Grok made 24 total tool calls, or 19 excluding four to-do updates and one tool lookup.

The paper also reports an Auto CLI run. Its raw transcript, timing records and patch are not currently included here, so those results cannot be reproduced from this checkout alone. The two runs used different interfaces and counting conventions, with one observation each; they do not establish a model ranking. Hidden-test success is not longitudinal code retention or Keep Rate.

The blank rows in the manual CSV record the original four-model plan, not completed runs.

## Experiment setup

Python 3.10+ and Git are required; new model runs also require the Cursor CLI authenticated to an account with access to the selected model.

```sh
python -m pip install -r caseStudyRun/requirements.txt
cd caseStudyRun
python harness.py --help
python harness.py models
```

See [RUN_PROTOCOL.md](caseStudyRun/RUN_PROTOCOL.md) for the prompt and run procedure. Model runs can incur usage charges. Preserve `cursor-task/` as the starting fixture and keep `cursor-eval/` outside the agent's workspace. The harness creates separate run repositories.

## Repository hygiene

Commit curated evidence and intentional deliverables. Local credentials, agent configuration, temporary files, generated paper builds, raw event streams and per-run repository copies are ignored. Review transcripts and Office metadata before publishing. No license is granted by this repository; the bundled ACL styles retain their upstream notices.
