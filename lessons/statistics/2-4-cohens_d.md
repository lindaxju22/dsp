[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

>> Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?
>>
>> A: First babies slightly are lighter than others (7.20 vs 7.33). Cohen's d is -0.089 compared to 0.029 as difference in pregnancy length.
>>
>> ```python
>> import nsfg
>> 
>> preg = nsfg.ReadFemPreg()
>> 
>> live = preg[preg.outcome == 1]
>> 
>> firsts = live[live.birthord == 1]
>> others = live[live.birthord != 1]
>> 
>> firsts.totalwgt_lb.mean(), others.totalwgt_lb.mean()
>> 
>> def CohenEffectSize(group1, group2):
>>     diff = group1.mean() - group2.mean()
>> 
>>     var1 = group1.var()
>>     var2 = group2.var()
>>     n1, n2 = len(group1), len(group2)
>> 
>>     pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
>>     d = diff / np.sqrt(pooled_var)
>>     return d
>> 
>> CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
>> 
>> CohenEffectSize(firsts.prglngth, others.prglngth)
>> ```
