# Tin

PyTorch wrapper for Taichi data-oriented class

**PRs are welcomed, please see TODOs.**

## Usage

```python
from tin import Tin
import torch

data_oriented = TiClass()  # some Taichi data-oriented class 
device = torch.device("cpu")
tin_layer = Tin(data_oriented, device=device)
    .register_kernel(data_oriented.forward_kernel)
    .register_input_field(data_oriented.input_field, True)
    .register_output_field(data_oriented.output_field, True)
    .register_weight_field(data_oriented.multiplier, True, name="field name")
    .finish() # finish() is required to finish construction
tin_layer.set_kernel_args(1.0)
output = tin_layer(input_tensor)
```

For input and output:

* We can register multiple `input_field`, `output_field`, `weight_field`.
* At least one `input_field` and one `output_field` should be registered.
* The order of input tensors must match the registration order of `input_field`s.
* The output order will align with the registration order of `output_field`s.

## TODOs

### Documentation

* Code documentation
* Documentation for users

### Engineering

* Set up CI pipeline

### Features
* PyTorch-related:
    * PyTorch checkpoint and save model
    * Proxy `torch.nn.parameter.Parameter` for weight fields for optimizers

### Misc

* A nice logo
