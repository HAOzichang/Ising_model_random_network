# Ising_model_random_network
We use the Metropolis-Hastings algorithm to simulate the behavior of the Ising model in different random networks near the phase transition point. 

The Metropolis-Hastings algorithm is a Markov chain Monte Carlo (MCMC) method for generating a sequence of samples from a probability distribution, such that as more samples are obtained, the distribution becomes a better approximation of the desired distribution. So it is a powerful sampling method to know the macro property of a distribution that has no analytic form. 

The goal is to sample from the distribution $p(\theta)$. The basic algorithm is
1. Choosing a starting sample $\theta_{0}$.
2. At iteration $i$, draw a proposed sample $\theta' \sim q(\cdot |\theta_{i-1})$.
3. Calculate the acceptance ratio
$$r(\theta'|\theta_{i-1} ) = \frac{p(\theta')q(\theta_{i-1}|\theta')}{p(\theta_{i-1}) q(\theta'|\theta_{i-1})}$$.
4. Set $\theta_{i} = \theta'$ with probability $\min \{1,r\};$ otherwise set $\theta_{i}=\theta_{i-1}$.
5. Repeat steps 2-4. 
For the Ising model, $p(\theta) $ is the probability distribution of the spin configuration which we want to sample from. 
$$p(\theta) = \frac{\exp (-\beta E_{\theta})}{\sum_{\theta} \exp(\beta E_{\theta})} $$
Here $\theta$ is one configuration of spin, and $E_{\theta}$ is the total energy of the system for one spin configuration  which includes all nearest-neighbor interactions. In our code, we chose the proposal  distribution $q(\cdot | \cdot)$ to be the uniform distribution. So the acceptance ratio is 
$$r(\theta'|\theta_{i-1} ) = \frac{p(\theta')}{p(\theta_{i-1}) }=\frac{\exp (\beta E_{\theta'})}{\exp (\beta E_{\theta})}.$$
