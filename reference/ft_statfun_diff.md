---
title: ft_statfun_diff
---
```plaintext
 FT_STATFUN_DIFF demonstrates how to compute the difference of the mean in two
 conditions. Although it can be used for statistical testing, it will have rather
 limited sensitivity and is not really suited for inferential testing.

 This function serves as an example for a statfun. You can use such a function with
 the statistical framework in FieldTrip using FT_TIMELOCKSTATISTICS,
 FT_FREQSTATISTICS or FT_SOURCESTATISTICS to perform a statistical test, without
 having to worry about the representation of the data.

 Use this function by calling the high-level statistic functions as
   [stat] = ft_freqstatistics(cfg, freq1, freq2, ...)
 with the following configuration option:
   cfg.statistic = 'ft_statfun_diff_itc'

 The experimental design is specified as:
   cfg.ivar  = independent variable, row number of the design that contains the labels of the conditions to be compared (default=1)

 The labels for the independent variable should be specified as the number 1 and 2.

 See also FT_TIMELOCKSTATISTICS, FT_FREQSTATISTICS or FT_SOURCESTATISTICS, and see FT_STATFUN_MEAN for a similar example
```
