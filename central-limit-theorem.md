The ==central limit theorem== (CLT) states that a large properly drawn sample will resemble population from which it is drawn. The [[probability]] that any sample will deviate massively form the underlying population is low.

Rule of thumb: for CLT to hold, the sample size must be at least 30.

CLT allows us to make inferences:
- Make inferences about a sample from a population
	- E.g. when only a sample of students is tested, the average test score will note deviate much from the average test score of the whole school.
- Make inferences about a population from a sample
	- E.g. the person testing only the sample of students can be reasonable certain that he gets a grasp of the performance of all students.
- The sample means will be distributed roughly as a normal distribution around the population mean, no matter what the distribution of the underlying population looks like.
	- The larger the number of samples, the more closely it will approximate a normal distribution. The larger the sample sizes, the tighter the distribution will be.

==Standard error== measures the dispersion of the sample means.
==Standard deviation==: dispersion in population (`σ`)
==Standard error==: dispersion in sample means (`SE = σ / √n`)

Because sample means are distributed normally:
- 68% of all sample means lie within 1 SE of population mean.
- 95% - 2SE
- 99.7% - 3 SE

Example: `population mean = 162`, `σ = 36`, `sample mean = 194`, `sample size = 62`
- SE of sample: `5 / √62 = 36 / 7.9 = 4.6`
- Difference sample mean and population mean is 32.
- That is way more than 3 SE's (99.7%)
- It is extremely unlikely that the sample is drawn from the population.

Most sample means will lie reasonably close to the population mean, the SE is what defines "reasonably close".

CLT tells us that the [[probability]] that a sample mean will lie within a certain distance of the population mean. It is relatively unlikely that a sample mean will lie more than two standard errors away from the population mean, etc.

[[statistics]]