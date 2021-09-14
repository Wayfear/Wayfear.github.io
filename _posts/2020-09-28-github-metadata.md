---
layout: distill
title:  Automatically install pytorch-geometric
date: 2020-09-28 21:01:00
description:
authors:
  - name: Xuan Kan
    affiliations:
      name: Emory University
---

```bash
#!/bin/bash
TORCH=$(python -c "import torch; print(torch.__version__)")
CUDA=$(python -c "import torch; version=torch.version.cuda.replace('.','');print(f'cu{version}')")
pip install --no-index torch-scatter -f https://pytorch-geometric.com/whl/torch-${TORCH}+${CUDA}.html
pip install --no-index torch-sparse -f https://pytorch-geometric.com/whl/torch-${TORCH}+${CUDA}.html
pip install --no-index torch-cluster -f https://pytorch-geometric.com/whl/torch-${TORCH}+${CUDA}.html
pip install --no-index torch-spline-conv -f https://pytorch-geometric.com/whl/torch-${TORCH}+${CUDA}.html
pip install torch-geometric
```