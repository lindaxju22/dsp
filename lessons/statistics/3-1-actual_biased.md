[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> *Something like the class size paradox appears if you survey children and ask how many children are in their family. Families with many children are more likely to appear in your sample, and families with no children have no chance to be in the sample.*
>>
>> *Now compute the biased distribution we would see if we surveyed the children and asked them how many children under 18 (including themselves) are in their household.*
>>
>> *Plot the actual and biased distributions, and compute their means. As a starting place, you can use chap03ex.ipynb.*
>>
>> A: The actual and biased distribution plots are shown when the code below is run. The mean of the actual distribution is 1.024 and the mean of the biased distribution is 2.40.
>>
>> ```python
>> import thinkplot
>> 
>> resp = nsfg.ReadFemResp()
>> 
>> # answer: actual distribution
>> pmf = thinkstats2.Pmf(resp.numkdhh, label='numkdhh')
>> 
>> thinkplot.Pmf(pmf)
>> thinkplot.Config(xlabel='Number of children', ylabel='PMF')
>> 
>> def BiasPmf(pmf, label):
>>     new_pmf = pmf.Copy(label=label)
>> 
>>     for x, p in pmf.Items():
>>         new_pmf.Mult(x, x)
>>         
>>     new_pmf.Normalize()
>>     return new_pmf
>> 
>> # answer: biased distribution
>> biased = BiasPmf(pmf, label='biased')
>> 
>> # answer: plot of actual and biased distributions
>> thinkplot.PrePlot(2)
>> thinkplot.Pmfs([pmf, biased])
>> thinkplot.Config(xlabel='Number of children', ylabel='PMF')
>> 
>> # answer: actual and biased means
>> pmf.Mean()
>> biased.Mean()
>> ```
>>
>> 
