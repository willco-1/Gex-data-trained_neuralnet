# Gex-data-trained-neuralnet


 # Gamma Exposure 
 
 Explained simply, there is a way to track how much delta hedging (by selling calls or puts) a market maker has engaged in. This is done by market makers in order to shield themselves from some of the directional risk of their positions.

The predictive power of GEX data lies in the neccesity of option's dealers to re-hedge their positions. To realize profit an option selling market maker muust limit his exposure to deltas.
In order to use this data to make powerful prediective assumptions about the market, it requires that we make a few assumptions: 


#1. All traded options are facilitated by delta-hedgers.
 In other words, all options contracts are bought or sold by a market participant whose goal is to profitably manage a book of options.
 
 #2. Call options are sold by investors; bought by market-makers
 It is difficult to determine the “direction” of a trade in an ultra-liquid market, . A vast majority will trade at the midpoint of the bid and ask.
It is apparent from an analysis of skew, open interest at strike, and
(circularly) the eQects of GEX, however, that the practice of call overwriting
(and stock collaring) drives the market for calls.

#3. Put options are bought by investors; sold by market-makers. As with calls,
puts are primarily used by investors who are already exposed to the
underlying market, and who are looking to modify the return pro5le of their
portfolio by using options. The “protective put” commands a premium for this reason, thus influencing the vertical skew of index options

#4. Market-makers hedge precisely to the option delta. If market-makers hedged
their deltas every time an option's delta changed, they would be trading
incessantly. In reality, market-makers utilize “hedging bands” to balance the
twin challenges of hedging costs and delta risk. Since it is not feasible to
gauge the breadth of every market-maker's hedging band, we simply use the
delta of the option.


# Computing Gamma

Gamma is the first dervivative of delta of an option. This is expressed as the rate of change of delta in a 1 point move in the underlying 
Thus, if the gamma of a single 50-delta call option is 10, we can assume that
a market-maker will re-hedge that option to either 40 or 60 delta in the
event of any ±1 point move in the underlying. In either case, the marketmaker will need to trade 10 shares. E.g., if the underlying moves up 1 point
and the new delta is 60, the market-maker will short-sell 10 shares. If the
underlying moves down 1 point and the new delta is 40, the market-maker
will buy back 10 shares.
In the case of a put option it is mostly the same as a calll option except if the underlying moves up 1 point the market-maker will buy 10 shares and if the market moves down 1 point the market-maker will short-sell 10 shares. 

The GEX of a stock is the summation of GEX at every available strike-price in every available contract on the options-chain for that security

ok so... that is all well and good... but what does that mean to us.. 

Based on the above, a positive GEX figure will imply that option market makers will hedge their positions in a way that will stifle volatility (buying into lows, selling into highs). A negative GEX figure implies the opposite, (buying into highs, selling into lows). 

A GEX figure approaching zero means that the market will be relatively protected from the invisible hand from the re-hedging activities of market-makers.

My thesis is that although it has been proven that using machine learning to predict the price action of securities is trivial and a sometimes blatantly in accurate metric, it could be a good training excercise to incorporate GEX data as a training point in a simple machine learning model to predict price action.

In order to determine the predicting power of GEX, it would be best to test the accuracy of a machine learning model to predict price with GEX data, and another one to use simple price-derived variance metric, a third using a price-derivied volatility metric.

It is my belief that after tuning and evalutating the performance of the models, that the models that were trained on GEX data will outperform the models trained on price-derived variance and volatility , respectively. 

More research will be required to define the exact featureset, but for sake of the experiment they should be held constant except for the variables that will be changed to test. 

The Featureset should be as follows [Adj close, Volume, open, high, low, daily close GEX value]
this featureset should be replicated and GEX value replaced by volatality OR variance. 
The model should also be trained absent of GEX, volatility, or variance in order to determine if that is even affecting the model's performance at all.


# Other ideas: 








