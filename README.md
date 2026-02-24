# Learning Probability Density Functions using Data Only

## Objective
The objective of this assignment is to learn the probability density function of a transformed random variable using only data samples, without assuming any analytical form of the distribution.

The transformed variable is learned using a Generative Adversarial Network (GAN).

---

## Dataset
The dataset used contains air quality measurements from Indian cities.

link of Dataset : https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data

Only the **NO₂ concentration** column is used for this assignment.

---

## Data Transformation
Let x denote the NO₂ concentration.

Each value of x is transformed using the function:

z = x + a_r sin(b_r x)

where the parameters depend on the university roll number.

---

## Transformation Parameters
Roll Number: 102303545

a_r = 0.5 × (r mod 7)  =  0.5 
b_r = 0.3 × ((r mod 5) + 1) = 0.3

---

## GAN Architecture
The GAN consists of two neural networks:

**Generator**
- Input: random noise sampled from a normal distribution
- Output: generated samples of z
- Structure: fully connected layers

**Discriminator**
- Input: a single value of z
- Output: probability of being real or fake
- Structure: fully connected layers with sigmoid output

The generator learns to produce samples similar to the transformed data, while the discriminator learns to distinguish between real and generated samples.

---

## Training Procedure
1. The discriminator is trained using real transformed samples and fake samples from the generator.
2. The generator is trained to fool the discriminator by producing realistic samples.
3. This process is repeated for multiple epochs until stable learning is observed.

---

## PDF learned using GAN 
The probability density function learned using the GAN shows a right-skewed distribution of the transformed variable 𝑧.

The density is highest at lower values of 𝑧  and gradually decreases as 𝑧 increases.

A prominent peak near the lower range indicates that most generated samples are concentrated in this region. A smaller secondary rise suggests the presence of additional structure in the data, which the generator is able to capture. The long tail towards higher values of z
z reflects the variability introduced by the nonlinear transformation.

Overall, the smooth shape of the curve indicates that the GAN has successfully learned a realistic and continuous approximation of the underlying probability density.

<img width="736" height="570" alt="image" src="https://github.com/user-attachments/assets/ad961e94-66b8-4d73-9de7-544f3305ba6c" />


---
# PDF Estimated Using Histogram

The histogram plot provides a discrete approximation of the probability density by grouping the generated samples into bins. It clearly shows that a large number of samples are concentrated at lower values of z, with the frequency decreasing as 
z increases. This plot helps visualize the spread and concentration of the generated data and supports the trend observed in the KDE plot.

<img width="727" height="569" alt="image" src="https://github.com/user-attachments/assets/7ec5f2ab-6c68-4349-bb74-639aa75c1200" />



---
# PDF Estimated Using KDE

The KDE plot shows a smooth and continuous approximation of the probability density function learned from the GAN-generated samples. The density is highest at lower values of 𝑧 and gradually decreases as z increases, indicating a right-skewed distribution. The smooth curve highlights the main peak and the long tail, showing that the generator has captured the overall shape and variability of the transformed data distribution.

<img width="732" height="569" alt="image" src="https://github.com/user-attachments/assets/24760de9-8226-41a5-aacf-e7dca5c2f27c" />


---

## Observations

### Mode Coverage
The generator captures the main modes of the transformed data distribution.

### Training Stability
Training becomes stable after initial iterations with small fluctuations.

### Quality of Generated Distribution
The generated samples follow a smooth and realistic distribution similar to the transformed data.

---

## Conclusion
This assignment demonstrates that GANs can learn an unknown probability distribution using data samples only, without assuming any parametric form.
