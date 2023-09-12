## Post Quantum Secure Blockchained Federated Learning for MEC

This repository is the Python implementation of the paper: 

> [Post Quantum Secure Blockchain-based Federated Learning for Mobile Edge Computing.](https://arxiv.org/abs/2302.13258) Submitted to IEEE Transactions on Mobile Computing, 2023

and evolved from the following paper:

> [FAIR-BFL: Flexible and Incentive Redesign for Blockchain-based Federated Learning](https://doi.org/10.1145/3545008.3545040). Accepted by ICPP '22.

Abstract: 

Mobile Edge Computing (MEC) has been a promising paradigm for communicating and edge processing of data on the move. We aim to employ Federated Learning (FL) and prominent features of blockchain into MEC architecture such as connected autonomous vehicles to enable complete decentralization, immutability, and rewarding mechanisms simultaneously. FL is advantageous for mobile devices with constrained connectivity since it requires model updates to be delivered to a central point instead of substantial amounts of data communication. For instance, FL in autonomous, connected vehicles can increase data diversity and allow model customization, and predictions are possible even when the vehicles are not connected (by exploiting their local models) for short times. However, existing synchronous FL and Blockchain incur extremely high communication costs due to mobility-induced impairments and do not apply directly to MEC networks. We propose a fully asynchronous Blockchained Federated Learning (BFL) framework referred to as BFL-MEC, in which the mobile clients and their models evolve independently yet guarantee stability in the global learning process. More importantly, we employ post-quantum secure features over BFL-MEC to verify the client's identity and defend against malicious attacks. All of our design assumptions and results are evaluated with extensive simulations.

## Requirements

This code is implemented in Python 3.8, using [pytorch](https://pytorch.org/), [pycryptodome](https://www.pycryptodome.org/) and [pqcrypto](https://github.com/kpdemetriou/pqcrypto).

## System Setup

The default setting is 2 edge nodes, 100 clients, and the client will perform local update and send the gradients to a edge node when it's local data size exceeds 100 ($N$), while the edge nodes will compute global update when they have 15 ($\phi$) unaggregated local gradients. You can modify these in **FAIR-BFL+.ipynb**.

## Usage

You can directly run the **FAIR-BFL+.ipynb**.

## Algorithm

We adopt asynchronous design, which means the clients and edge nodes conduct independent strategy. The whole process of client update strategy is shown below:

![image-20230912183408020](https://s2.loli.net/2023/09/12/dH5tcyXDvVf9me2.png)

And the strategy for edge nodes to calculate global updates is as follows:

![image-20230912183558258](https://s2.loli.net/2023/09/12/tPZFzdG1aTS3Ocr.png)

## Results

- Based on the provided figures, it is evident that our proposed method BFL-MEC, can achieve lower latency while guaranteeing post-quantum safety, and is more competitive for latency-sensitive computing scenarios such as mobile edge computing.

![image-20230912190113215](https://s2.loli.net/2023/09/12/rajJAXYN85cuUkO.png)

- Furthermore, investigated trade-off between $N$ and $\phi$. The results imply that the best combination of $(N,\phi)$ can be found.

![image-20230912190246681](https://s2.loli.net/2023/09/12/qi5lchfWNbxnmUj.png)

![image-20230912190553662](https://s2.loli.net/2023/09/12/6sEj9LIrD3ia4G8.png)

- Also, with the help of novel discard strategy and contribution identification mechanism, the proposed method can be further accelerated and resist various malicious attacks.

![image-20230912191048954](https://s2.loli.net/2023/09/12/QYd7GCUjZ3OV4TM.png)

![image-20230912190801359](https://s2.loli.net/2023/09/12/otFX8nJDUMbKkzG.png)

## Acknowledgment

- The underlying federated learning algorithms used are from FedAVG and partially use implementations from [this repository](https://github.com/WHDY/FedAvg).
- Datasets are MNIST contributed by Yann LeCun, downloaded from [offical wesite](http://yann.lecun.com/exdb/mnist/).

## Citations

If you use this code for a scientific publication, please include a reference to this paper:

- Xu, R., Pokhrel, S. R., Lan, Q., & Li, G. (2023). Post Quantum Secure Blockchain-based Federated Learning for Mobile Edge Computing. *arXiv preprint arXiv:2302.13258*.

Also, this paper if you want a comprehensive display of our research on this line:

- Rongxin Xu, Shiva Raj Pokhrel, Qiujun Lan, and Gang Li. 2023. FAIR-BFL: Flexible and Incentive Redesign for Blockchain-based Federated Learning. In Proceedings of the 51st International Conference on Parallel Processing (ICPP '22). Association for Computing Machinery, New York, NY, USA, Article 80, 1–11. https://doi.org/10.1145/3545008.3545040

`BibTex` information:

```bibtex
@inproceedings{10.1145/3545008.3545040,
author = {Xu, Rongxin and Pokhrel, Shiva Raj and Lan, Qiujun and Li, Gang},
title = {FAIR-BFL: Flexible and Incentive Redesign for Blockchain-Based Federated Learning},
year = {2023},
isbn = {9781450397339},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3545008.3545040},
doi = {10.1145/3545008.3545040},
booktitle = {Proceedings of the 51st International Conference on Parallel Processing},
articleno = {80},
numpages = {11},
keywords = {Security and Privacy, Blockchain, Federated Learning, Incentive},
location = {Bordeaux, France},
series = {ICPP '22}
}
```