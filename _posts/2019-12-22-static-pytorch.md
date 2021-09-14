---
layout: distill
title: The Trap of Static Variables in Pytorch
description: 
date: 2019-05-22
authors:
  - name: Xuan Kan
    affiliations:
      name: Emory University

---




```python
import torch
from torch import nn

class A(nn.Module):

    def __init__(self):
        super().__init__()
        self.p = nn.ParameterList()
        self.p.append(nn.Parameter(torch.zeros(5)))

a = A()

for name, para in a.named_parameters():
    print(name)
# oupput p.0

# wrong method
class AA(nn.Module):
    p = nn.ParameterList()

    def __init__(self):
        super().__init__()
        self.p.append(nn.Parameter(torch.zeros(5)))

a = AA()

for name, para in a.named_parameters():
    print(name)
# output nothing

# right method
class AA(nn.Module):
    p = nn.ParameterList()

    def __init__(self):
        super().__init__()
        t = nn.Parameter(torch.zeros(5))
        self.p.append(t)
        self.register_parameter('parameter_name', t)

a = AA()

for name, para in a.named_parameters():
    print(name)

# output parameter_name
```
