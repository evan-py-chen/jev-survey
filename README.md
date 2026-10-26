# A Survey on Jev: Prior Research, Adaptation Costs, and Evidence of System One Models

Evan Chen, Jiamu Zhang, Tianze Yang, Kelly Wan, Liangjie Hong, Liang Wu
*Nokia, Sunnyvale, CA, USA*

Accepted to ACM SIGKDD Explorations, 2026 (authors' version)

**News, October 2026:** ACM SIGKDD Explorations accepted this survey. This repository now has the accepted version.

**[PDF](https://evan-py-chen.github.io/jev-survey/jev-survey.pdf)** · **[Paper page](https://evan-py-chen.github.io/jev-survey/)**

## Abstract

Many decisions in LLM systems do not need generated text. They only need a choice among a few fixed options, such as which model should handle a request or whether a response is safe. Typed decision models, also called Jev-style or System One decision models, are designed for exactly this case. They take a state and a question specified at call time, and instead of generating text, they return a probability distribution over a closed answer set. TypeSafe AI offers this interface in Jev, and several open implementations reproduce it. This short survey explains what these models are, where their ideas come from, and what the current evidence can support. These models build on earlier work, which we organize into two areas of earlier research. The first area, routing research, supplies the goal: a decision component that adapts when the system changes, without retraining. The second area supplies the mechanisms: zero-shot classifiers, safety guards, and label-probability readout. How much "no retraining" actually saves, however, depends on what changes. We therefore examine the adaptation cost of three kinds of change: new models, new decisions, and new deployment constraints. Adding a new candidate model is not free, because the routing approaches reviewed here still rely on candidate-specific evidence for each new candidate. A new type of decision, however, can be specified without retraining the shared model. Finally, a new deployment constraint, such as a target error rate, still requires labeled examples. The empirical evidence is also mixed. On the positive side, independent studies report valid outputs and large cost reductions compared with LLM judges, although these savings shrink when the baseline is already cheap. On the negative side, the same studies find that accuracy trails frontier LLMs on hard tasks, that calibration varies across workloads and subgroups, and that added context can change decisions. Given these trade-offs, we recommend testing a typed model against two simpler alternatives before adopting it: a label-probability readout on an open model, and a cheap generative cascade. The comparison should use the same acceptance rule the deployment will use.

**Keywords:** Jev, typed decision models, System One models, LLM routing, zero-shot classification, calibration, selective prediction, guardrails

## Citation

```bibtex
@article{chen2026jevsurvey,
  title   = {{A Survey on Jev}: Prior Research, Adaptation Costs, and Evidence of {System One} Models},
  author  = {Chen, Evan and Zhang, Jiamu and Yang, Tianze and Wan, Kelly and Hong, Liangjie and Wu, Liang},
  journal = {ACM SIGKDD Explorations Newsletter},
  year    = {2026},
  note    = {Accepted, to appear},
  url     = {https://evan-py-chen.github.io/jev-survey/}
}
```

## Building from source

The LaTeX source is in [`src/`](src/). It uses the SIGKDD Explorations template (`sigkddExp.cls`, two columns). With [Tectonic](https://tectonic-typesetting.github.io/):

```bash
cd src && tectonic -X compile main_kdd.tex
```

or with TeX Live: `pdflatex main_kdd && bibtex main_kdd && pdflatex main_kdd && pdflatex main_kdd`. The folder also has `main_kdd.bbl`, so a build without BibTeX also works.
