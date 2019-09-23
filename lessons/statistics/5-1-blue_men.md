[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

>> *In the BRFSS (see Section* [*5.4*](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#lognormal)), *the distribution of heights is roughly normal with parameters µ = 178 cm and σ = 7.7 cm for men, and µ = 163 cm and σ = 7.3 cm for women.In order to join Blue Man Group, you have to be male between 5’10” and 6’1” (see http://bluemancasting.com). What percentage of the U.S. male population is in this range? Hint: use scipy.stats.norm.cdf.*
>>
>> A: Roughly 34% of the US male population is between 5’10” and 6’1”
>>
>> ```python
>> import scipy.stats
>> 
>> mu = 178
>> sigma = 7.7
>> dist = scipy.stats.norm(loc=mu, scale=sigma)
>> type(dist)
>> 
>> dist.mean(), dist.std()
>> 
>> dist.cdf(mu-sigma)
>> 
>> low = dist.cdf(177.8)    # 5'10"
>> high = dist.cdf(185.4)   # 6'1"
>> low, high, high-low
>> ```
>>
>> 
