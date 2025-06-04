# Loss function

**[`nn.L1Loss`](https://pytorch.org/docs/stable/generated/torch.nn.L1Loss.html#torch.nn.L1Loss)**

Creates a criterion that measures the mean absolute error (MAE) between each element in the input *x* and target *y*.
$$
\textbf{MAE}= \frac{\sum_{i=1}^n (\hat{y}-y_i)}{n}
$$
**[`nn.MSELoss`](https://pytorch.org/docs/stable/generated/torch.nn.MSELoss.html#torch.nn.MSELoss)**

Creates a criterion that measures the mean squared error (squared L2 norm) between each element in the input *x*and target *y*.
$$
\textbf{MES}=\frac{\sum_i^n (\hat{y}-y_i)^2}{n}
$$
**[`nn.CrossEntropyLoss`](https://pytorch.org/docs/stable/generated/torch.nn.CrossEntropyLoss.html#torch.nn.CrossEntropyLoss)**

This criterion computes the cross entropy loss between input logits and target.
$$
H(p,q)=-\sum_{x\in\mathcal{X}}p(x)\log{q(x)}
$$
