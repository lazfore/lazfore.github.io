---
title: "Jiarui Li"
description: "Personal homepage of Jiarui Li, featuring research in AI security, privacy, and applied cryptography."
draft: false
---

{{< home-hero image="/images/selfie-home.jpg" alt="Portrait of Jiarui Li" >}}
# Jiarui Li（李嘉锐）

F-building, 9th floor  
Xueyuan Avenue No. 1068, Nanshan District  
Shenzhen Institute of Advanced Technology, Chinese Academy of Sciences  
Shenzhen, Guangdong, China

## Contact

Email: lazfore[AT]gmail[DOT]com

{{< /home-hero >}}

{{< home-section id="about" title="About Me" >}}

I am currently a postdoctoral researcher at the Shenzhen Institute of Advanced
Technology, Chinese Academy of Sciences. Before that, I received my Ph.D. from
the Department of Electrical and Computer Engineering at Stevens Institute of
Technology, where I had the honor of working with
[Dr. Shucheng Yu](https://sites.google.com/view/shuchengyu/about-me?authuser=0).
I received my master's degree in Business Intelligence and Technology from
Stevens in May 2019. Before coming to Stevens, I received my bachelor's degree
in Applied Mathematics from South China University of Technology in 2017.

My research focuses on applied cryptography and its applications in AI security
and privacy. I have also worked on lattice-based attribute-based encryption
(ABE) and its applications. More broadly, I am interested in privacy-preserving
computing techniques, including homomorphic encryption and multiparty
computation.

{{< /home-section >}}

{{< home-section id="teaching" title="Teaching Experience" class="home-band--teaching" >}}

- **CS513 Data Mining** — Teaching Assistant, Fall 2018
- **CPE691 Information Security** — Guest Speaker, Spring 2020 and Fall 2024
- **CPE695 Applied Machine Learning** — Instructor, since Fall 2023
- **Retrieval-Augmented Generation** — Co-Lecturer, Summer 2024 mini-course
- **Privacy-Preserving Machine Learning** — Co-Lecturer with York College,
  Summer 2025 mini-course

{{< /home-section >}}

{{< home-section-title id="research" title="Research Projects" >}}

{{< home-project id="secure-inference" title="Secure Inference Outsourcing for IoT Devices" image="/images/CNNoutsourcing.png" placeholder="Secure inference outsourcing architecture" >}}

As deep learning models become increasingly complex, executing inference
locally on resource-constrained devices such as IoT sensors, drones, and
embedded systems has become increasingly impractical. Offloading computation to
nearby edge or cloud servers offers an attractive solution, but it also raises
critical privacy concerns: the data used for inference often contains sensitive
personal or contextual information, and transmitting it to an untrusted server
may expose users to data leakage.

To address this problem, I introduced a practical framework for secure deep
neural network inference outsourcing [1] that protects input confidentiality
while maintaining real-time performance, without relying on heavy cryptographic
tools such as homomorphic encryption or multiparty computation. The key insight
is to separate neural computations into linear and nonlinear parts. Linear
layers, such as convolutional and fully connected layers, dominate the
computational cost and can be securely outsourced, while nonlinear activations
remain local. This design leverages the algebraic linearity of neural networks
to achieve both efficiency and privacy.

To realize this idea, I developed an interactive Privacy-Preserving Scalar
Product (iPPSP) evaluation primitive that enables secure linear computation
outsourcing using lightweight one-time-pad encryption. The protocol ensures
confidentiality under standard cryptographic assumptions, requires minimal
computation on the client side, and remains compatible with existing deep
learning frameworks and GPU acceleration. This work was validated through
extensive experiments using IoT devices such as Raspberry Pi boards and drones.
Because the protocol relies only on linearity, it generalizes naturally to
diverse neural architectures such as CNNs, RNNs, and transformers, making it
broadly applicable to edge, IoT, and distributed learning settings.

{{< /home-project >}}

{{< home-project id="verifiable-federated-learning" title="Verifiable Federated Learning with TEE" image="/images/integrity-workflow.png" placeholder="Verifiable federated learning architecture" >}}

Federated learning (FL) enables multiple participants to collaboratively train
machine learning models without centralizing their raw data, offering a
promising foundation for privacy-preserving analytics across organizations and
devices. However, by keeping training local, FL trades data confidentiality for
a new vulnerability: integrity violations. Malicious or lazy participants can
submit falsified model updates without performing proper training, degrading
model quality and undermining trust. This risk is amplified in cross-silo and
IoT deployments, where devices operate under heterogeneous conditions and may
not be fully trusted. My research addresses this issue by leveraging Trusted
Execution Environments (TEEs) to provide verifiable training integrity and
computational efficiency under a zero-trust assumption.

#### Integrity Verification for Federated Learning

To ensure the integrity of training participants in federated learning, I use
TEEs to design a sampling-based retraining verification protocol [2]. The
solution randomly selects a subset of training rounds to be reproduced inside a
TEE, allowing the server to verify whether participants executed legitimate
training on their committed data.

The framework also incorporates secure offloading techniques from my previous
work. In particular, I introduce a partial training offloading scheme that
allows secure enclaves to offload linear operations to co-located GPUs,
protected by lightweight one-time-pad encryption and pseudorandom permutation.
This design significantly improves scalability by eliminating the need to
perform the entire training process within TEEs. In addition, the framework
does not require every participant to possess a TEE because only the verifier
operates within a trusted environment. This flexibility broadens its
applicability to large-scale and heterogeneous federated learning deployments.

#### Accumulator-Based Integrity Verification for Federated Learning

Building on sampling-based retraining and secure offloading, I further improve
integrity assurance by eliminating the need for retraining [3]. I design a
lightweight accumulator that records cryptographic commitments to intermediate
gradients throughout the local training process. Instead of retraining, the
verifier checks whether these accumulators are consistent with the submitted
local model updates.

This commitment-based mechanism significantly reduces computational overhead
while maintaining verifiable correctness. By combining TEE-assisted attestation
with cryptographic accumulation, the framework achieves efficient,
privacy-preserving verification suitable for resource-constrained and sensitive
domains such as healthcare.

{{< /home-project >}}

{{< home-project id="lattice-ma-abe" title="Practical Lattice-Based Multi-Authority ABE" >}}

In this project, we aim to use an efficient ring-LWE construction to improve
the efficiency of decentralized multi-authority attribute-based encryption
(MA-ABE). We design an RLWE-based MA-ABE protocol and prove its security in the
selective security model. Our analysis shows that the protocol improves
efficiency by a factor of \(N^2\) compared with other lattice-based MA-ABE
schemes offering the same functionality. Preliminary results demonstrate
encryption and decryption times of 28.60 and 15.71 seconds, respectively, when
\(N = 1024\), showing the feasibility of the construction in real-world
applications.

We are currently implementing the protocol and plan to release the code as an
open-source library on GitHub.

{{< /home-project >}}

{{< home-section id="publications" title="Publications" class="home-band--publications" >}}

### International Conference Publications

1. Li, J., & Yu, S. (2024). Efficient multi-authority ABE from learning with
   errors over rings. In *Proceedings of the IEEE Military Communications
   Conference (MILCOM 2024)* (pp. 963–968). IEEE.
   [DOI](https://doi.org/10.1109/MILCOM61039.2024.10773690)
2. Li, J., Chen, N., Yu, S., & Srivatanakul, T. (2024). Efficient and
   privacy-preserving integrity verification for federated learning with TEEs.
   In *Proceedings of the IEEE Military Communications Conference (MILCOM
   2024)* (pp. 999–1004). IEEE.
   [DOI](https://doi.org/10.1109/MILCOM61039.2024.10773815)
3. Li, J., & Yu, S. (2024). Integrity verifiable privacy-preserving federated
   learning for Healthcare-IoT. In *Proceedings of the IEEE International
   Conference on E-health Networking, Application & Services (HealthCom 2024)*
   (pp. 1–6). IEEE.
4. Guo, R., Li, J., & Yu, S. (2024). GridSE: Towards practical secure
   geographic search via prefix symmetric searchable encryption. In
   *Proceedings of the 33rd USENIX Security Symposium (USENIX Security 2024)*.

### Refereed Journal Publications

1. Li, J., Zhang, Z., Yu, S., & Yuan, J. (2022). Improved secure deep neural
   network inference offloading with privacy-preserving scalar product
   evaluation for edge computing. *Applied Sciences, 12*(18), 9010.
   [DOI](https://doi.org/10.3390/app12189010)
2. Zhang, Z., Li, J., Yu, S., & Makaya, C. (2023). SafeLearning: Enable
   backdoor detectability in federated learning with secure aggregation. *IEEE
   Transactions on Information Forensics and Security, 18*, 3289–3304.
   [DOI](https://doi.org/10.1109/TIFS.2023.3280032)

{{< /home-section >}}
