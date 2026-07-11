# Learn2Discern (L2D)

# Paper
LLMs are increasingly used with external knowledge sources like the internet. Do they weigh information appropriately-updating more for reliable sources (source discernment) and more when claims bring priors closer to the truth (truth discernment)? We formalize this as information discernment and introduce Learn2Discern (L2D), an experimental framework and benchmark grounded in three normative axioms with interpretable metrics. To establish external validity, a pre-registered, quota-matched user study (n=299) confirms that real LLM users endorse all three axioms and report that violations reduce their trust and usage intent. Across 13 models and nearly 670K trials, we find consistent failures across both dimensions: models perform near chance on source and truth discernment, rely on source popularity twice as much as source reliability, and update roughly equally whether a claim improves or worsens their position relative to the ground truth. Models integrate external knowledge most effectively on datasets where their priors are already the most accurate. Newer and larger models improve truth discernment but not source discernment, a blind spot that model complexity does not address. We identify simple inference-time interventions that improve both forms of discernment. We release our dataset and survey as a testbed for a core alignment property that scales in importance as LLMs replace traditional search.

[![Paper](https://img.shields.io/badge/📄_Paper-ResearchGate-00CCBB?style=for-the-badge)](https://www.researchgate.net/publication/408658513_Information_Discernment_in_Large_Language_Models)
[![DOI](https://img.shields.io/badge/DOI-10.13140/RG.2.2.22199.28328/1-blue?style=for-the-badge)](https://doi.org/10.13140/RG.2.2.22199.28328/1)

# Cite

```
@misc{ashkinaze2026informationdiscernment,
  title        = {Information Discernment in Large Language Models},
  author       = {Ashkinaze, Joshua and Kurek, Laura and Faisal, Alina and Miao, Tongyuan and Joseph, Mariam and Budak, Ceren and Gilbert, Eric},
  year         = {2026},
  month        = {July},
  doi          = {10.13140/RG.2.2.22199.28328/1},
  url          = {https://www.researchgate.net/publication/408658513_Information_Discernment_in_Large_Language_Models}
}
```

---

## Downloads

### Dataset

| Split | Description | Download |
|---|---|---|
| `exp1_prompts.json` | Augmented test set used in the paper. **Use this to benchmark new models.** | [Download](https://www.dropbox.com/scl/fi/njgyzki9rndyoz3lr0q3l/exp1_prompts.json?rlkey=bmmdas0oxgqypiwr7uit69b7c&st=b2w2y0et&dl=0) |
| `test.json` | Test tuples used in the paper. | [Download](https://www.dropbox.com/scl/fi/wzmo928g28jwgy1ib8dae/test.json?rlkey=v472bevhx2hwgrf4g2ks0bwmx&st=alil2h97&dl=0) |
| `train.json` | Train tuples (not used in the paper; available for fine-tuning). | [Download](https://www.dropbox.com/scl/fi/fwbsrnlt4y5ssvhxabtvb/train.json?rlkey=1r1k0o0zblatqyut6midsoc3c&st=3zpzb54t&dl=0) |

### User Study

De-identified responses from our pre-registered, quota-matched user study (*n* = 299).

| File | Download |
|---|---|
| `info_discern_user_study.csv` | [Download](https://www.dropbox.com/scl/fi/53f837t3wl9aniqm4zg9i/info_discern_user_study.csv?rlkey=olwbzdq3wq26dbtk75g00qkpx&st=ns5v5m97&dl=0) |

---

## Documentation

- [Dataset codebook](https://github.com/josh-ashkinaze/l2d-public/blob/main/exp1_prompts_codebook.md)
- [User study codebook](https://github.com/josh-ashkinaze/l2d-public/blob/main/user_study_codebook.md)
