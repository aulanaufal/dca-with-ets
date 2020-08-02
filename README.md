# Decline Curve Analysis with Error-Trend-Seasonal (ETS) Method

As we all know, Decline Cruve analysis is a reservoir engineering empirical technique that extrapolates trends in the production data from oil and gas wells. The purpose of DCA usually is to generate forecast of future production rates and determine the ultimate recoverable reserves (EUR). 

![alt text](https://github.com/aulanaufal/DCAwithETS/blob/master/DCA_Pic.png?raw=true)

Traditionally, decline curve analysis is done on a rate vs time plot (or sometimes rate versus cumulative production) using trending equations published by J.J. Arps (1945). The forecasting will end based on:
* Scheduled end time achieved
* Economic rate limit of the well
* Scheduled reserves achieved
* Water cut/ WOR limit of the well

## Practical Decline Curve Analysis Key Points 
(quoted from www.fekete.com)
All production can be characterized as having an initial transient flow period followed by a boundary-dominated flow period. During the transient period, the reservoir pressure at the flow boundary remains constant at the initial reservoir pressure and the flow boundary moves outward from the well through the reservoir. This portion of a well’s flow is characterized by very high decline rates. When the flow boundary reaches an actual reservoir boundary, or meets with a flow boundary of another well, the reservoir pressure begins to decline and the well enters the boundary-dominated flow period. It is in this period that traditional decline methods (i.e. Arps) can be used.

The transient flow period can last for time periods from several minutes to several years, depending upon permeability and the areal extent of the reservoir. For most conventional production, the transient flow period ends after a few days. Tighter reservoirs that have permeability in the 0.5 to 1.0 mD range can have transient periods that last several months. Reservoirs that have even lower permeabilities that require extensive fracture networks can have transient periods that could last for several years.

Once a well has achieved boundary-dominated flow, another important consideration is the sandface flowing pressure. For the period of production included in the decline analysis, the **sandface flowing pressure must be relatively constant before a reliable set of decline parameters can be extracted**. Factors that affect sandface flowing pressure are **rate controlled wells, changing wellhead backpressure, changing wellbore configurations, and liquid loading.**

## Error-Trend-Seasonal (ETS) Method
In this repository, we will try to forecast a Decline Curve with ETS method as another alternative to the Arps method. ETS method is a method to forecast time-series data which decomposes the time-series data to components:
* Trend
* Seasonal (The repeated periodically additional values)
* Residual (Noise of the time-series data)

Each of the component can be:
* None 
* Additive (Increasing/decreasing linearly)
* Multiplicative (Increasing/decreasing with a factor/exponentially)

![alt text](https://github.com/aulanaufal/DCAwithETS/blob/master/Decomposition.jpg?raw=true)

Big shout-out for **Wira Dharma (J.Cop)** to share this material on his youtube channel (https://www.youtube.com/playlist?list=PLGn1wRmlR3Ms7wr2zgtcC4LaE_NHQAEjx) and his github (https://github.com/WiraDKP)

# Inside the Notebook
We will find a sandbox to predict DCA using ETS method. We are mainly using **Wira Dharma's jcopml.time_series package** which is build on top of **statsmodels package**. At first, we will import required packages and data, then we will select the well to be forecasted and impute missing values (time series should be continuous) using pandas time interpolation function. Then we will determine the ETS method we are going to use, and forecast the time-series data. Lastly, we will use Auto ETS method from jcopml.time_series package to do a Grid Search optimization to determine the suitable components for our ETS method.

![alt text](https://github.com/aulanaufal/DCAwithETS/blob/master/DCA_Forecast.jpg?raw=true)

# Sources
* Traditional Decline Analysis Theory (http://www.fekete.com/SAN/WebHelp/FeketeHarmony/Harmony_WebHelp/Content/HTML_Files/Reference_Material/Analysis_Method_Theory/Traditional_Decline_Theory.htm)
* WiraDKP / time_series (https://github.com/WiraDKP/time_series)
* Time Series Forecasting | Indonesia (https://www.youtube.com/playlist?list=PLGn1wRmlR3Ms7wr2zgtcC4LaE_NHQAEjx)

# Citation

Should you use this repository, please make this citation:

> Naufal, A.A., DCA with ETS, (2020), GitHub Repository, https://github.com/aulanaufal/DCAwithETS

Bibtex: Coming Soon

# License 

```
MIT License

Copyright (c) 2020 Aulia Ahmad Naufal

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```






