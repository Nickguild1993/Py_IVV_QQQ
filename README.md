

# Comparative analysis for Exchange Traded Funds: IVV & QQQ
 
## Overview of the ETF Analysis:

- The purpose of this analysis was to compare two passively managed ETFs in order to see which one has performed better since the beginning of 2015.  Using the Pandas Data Reader library, I imported the starting data from Yahoo Finance using their API.  This allowed me to get real time data without having to copy any CSV files.  From there, I went about fleshing out my analysis by creating new tables with columns for tools like Moving Average, Exponential Moving Average, Year to Year Growth, Normalized Percentage Change, among others.  Those values were then graphed in order to visualize the analysis and make comparisons easier and more noticeable.

## Terminology:

- Exchange Traded Funds (referred to as ETFs from this point on) are an investment vehicle that can be comprised of stocks, bonds, commodities, real estate as well as other types of financial assets.  ETFs are similar to mutual funds, in that both contain a basket of assets, but they operate differently in a few key areas.  One important difference is that ETFehave like stocks (in that they are tradable at any point while the market is open) they offer much more flexibility than a traditional mutual fund, which is only traded once, at the end of trading day.  Because ETFs are traded throughout the day, their value is constantly updated, which allows the investor to be more reactive instead of having to wait on a mutual funds NAV (net asset value- the funds total assets minus liabilities divided by the number of issued shares) to be calculated at the end of the day.  Because of this, and other benefits such as being more tax friendly than mutual funds, ETFs have become increasingly popular among both institutional and retail investors.

- While there are actively managed ETFs, this project focuses on two of the top passively managed ETFs- iShares’ IVV and Invesco’s QQQ.  IVV tracks the S&P 500 index while QQQ tracks the NASDAQ-100 index.  

## Analysis:
### The notebook file for the analysis is in the Repo (there is also a .py file version available)

The first thing to explore is a breakdown of the top 5 holdings of each ETF, a table of which is below.

![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_excel_tables/ETF_holdings_table.png)

- Looking at the holdings breakdown, QQQ has a much higher exposure with their largest holdings compared to IVV.  Those top 5 holdings represent 40.55% of the total assets of QQQ and 20.97% of IVV total assets, respectively.  Additionally, those top 5 companies would all be considered technology companies (even if some are technically part of the consumer discretionary or communications sectors).  *For this analysis, I combined Alphabet Class A (GOOGL) & Class C (GOOG) because the price variation is somewhat negligible, and the voting rights associated with GOOGL (GOOG shares are not attached to any voting rights) don't really factor into this analysis.

![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/top_5_holdings.png) 


When I first called the data from Yahoo Finance for both ETFs using the Pandas Data Reader, it looked like this.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/IVV_DF_starting.png) 

- This DataFrame served as a useful starting point that gave me some ideas about how best to dive deeper into the data.  My first move was to create three new columns for both DataFrames- Daily_Change: which is the daily amount (in dollars) that the ETF gained or lost from the opening of the market to it’s close.  Percentage_Change: which is the same information expressed as a percentage, and finally Normalized_Change: which is an value that represents the closing amount for that day compared to the first day of the analysis (January 2nd, 2015).  

![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/IVV_DF_wCode_Normalized.png) 


- These added columns, especially Normalized Change, allow the viewer to quickly compare the closing value of the ETF from any day and compare it to previous dates.

- Next, I wanted to compare the closes of each ETF side by side, so I created a new DataFrame that would allow for quick comparisons of the ETF closing values.

![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/ETF_DF_Closes.png)


- In order to visualize the closes over time, I created a line plot that tracked each ETFs closing values from the selected starting point (1/2/2015) to the current date.




![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/QQQ_IVV_Closes.png)


- Next, I wanted to look at the simple moving averages (SMA) for both ETFs.  Simple moving averages take a certain time (for this use case, 10 days) and get the mean for that range of dates.  Additionally, I wanted to also add in the exponential moving averages (EMA), which are similar to SMAs but weight the more recent dates heavier so that they are more sensitive to future price changes.  



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/SMA_EMA_code.png)


- Using those values, I created a line plot that would chart the SMA and EMA for each security with the share price of each one overlayed.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/QQQ_IVV_MA_EMA.png)


- From the graph, you can see that the EMA lines for both ETFs are indeed more predictive than the SMAs of future price changes, as expected.  The choice was made to start this graph at the beginning of 2020 for two reasons- firstly, because it was unwieldy and difficult to discern when 6+ years of available data was used, and secondly, because I was curious to see how each security was effected by the market effectively collapsing in Q1 of 2020 and how each subsequently rebounded.  The graph helps visualize how IVV was hit harder than QQQ and grew at a slower rate in the aftermath of the dramatic correction.

- Next, I wanted to compare the value change for the securities over a one year span.  In order to do so, I created two new DataFrames that had the closing price for each particular day along with the closing price for one year after that initial date.  Then to allow for a quicker comparison, a column that had the difference (in USD) between the two was added.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/IVV_DF_year_change.png)


- In order to visualize this change, I created a line graph for each security.  The first line (QQQ_1 or IVV_1) is the price on the day the chart starts (1/02/2018) and the second line (QQQ_2 or IVV_2) is the price on that same day, one year later.  This allows for the viewer to quickly look at how the security performed over 1 year intervals.  Here again, QQQ outshines IVV as it is shown to be more resilient to corrections and experiences growth after a dip faster than IVV.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/IVV_1yr_change.png)

![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/QQQ_1year_change.png)


- To better understand which ETF performed better over those 1 year time periods, a new DataFrame was created using the following code.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/DF_1year_code.png)


- The above code allowed for new columns showing the percentage growth for each security and also identifies which performed better in each one-year period.  The new table can be seen below.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/DF_1yr_comparsion.png)


- In order to zoom in and quickly asertain which ETF had better 1 year performance overall, the previous table was distilled into a simpler one with that simply counted up the number of times each ETF performed better over the 1 year intervals (there is a row for equal performance, but this never actually occurred).



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/DF_1yr_performance_count.png)


- To visualize the comparison, the followign bar chart was created below.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/Bar_Chart_1yr_comp.png)




- Out of the 990 1 year periods, QQQ performed better in 835 of them, good for 84% of the total.  

- Next, I wanted to expand the range to 5 year periods, to see if the QQQs performance held up over a longer timeframe.  A new DataFrame was created using the same method as before, but the code was slightly changed so that the new date column was 5 years after the starting point, instead of just 1 year.  Below is an image of the table.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/DF_5year_table.png)


- Next, I added the same new columns to the DataFrame that I had for the 1 year version that show which ETF performed better over a given 5 year period.  Below is a sample of 10 random dates chosen using  the following: ```sample(n=10)```



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/DF_5yr_performance_count_comp.png)


- After creating a new table to count the amount of times that each ETF performed better than the competitor, I created a new bar chart to visualize how each security did.

![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/Bar_Chart_5yr_comp.png)


- Instead of IVV having a better showing after performing better in only 155 out of 990 possible 1 year periods in the previous graph, QQQ literally dominated; outperforming IVV 349 out of 349 possible times, a perfect 100%.  While it should be noted that the percentage that QQQ beat IVV every time varied, and sometimes it was indeed close, the fact that there wasn’t a single 5 year period in which IVV performed better than QQQ is frankly, shocking.

- Now that sufficient data has been compiled, it’s time to see how the information collected plays out with a real world example.  To understand how each security preformed, I wanted to start with an initial investment of $10,000 in each one, and track various measurements of how it performed from the start date (1/02/2015) right up until now.  Between those two points, I created 1, 3, and 5-year performance benchmarks.  The DataFrame code and resulting table is pictured below.

![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_DataFrames/DF_returns_wCode.png)


- While this is helpful, it isn’t exactly very easy to extract information from. In order to make the data more accessible, the DataFrame was exported as a .CSV file so that it was compatible with Excel.

- The first table that was created was just a direct import of the Pandas DataFrame with conditional formatting to highlight the higher performing value with a green cell, and the lower performing one with a red cell fill.  Below is a partial view of the table (the table contains too many columns to capture it fully).



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_excel_tables/ETF_excel_direct_export.png)


- Next, I wanted to examine the securities rate of normalized change side by side more closely.  A new table was created to showcase the comparative normalized changes of the two ETFs.  



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_excel_tables/ETF_excel_normalized_change.png)


- Normalized change is a great way to understand how a specific security is performing because the rate is normalized from the initial amount, so it’s comparable across time. What is exceedingly clear is that QQQ performs at a much higher level across every single benchmark. As it can be seen below in the line chart, the 5-year QQQ normalized change is greater than the current (6.5 years) normalized change of IVV.  Furthermore, when comparing the current normalized rate of both ETFs, QQQ has experienced 140% more growth than IVV.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/ETF_line_normalized_change.png)


- The line plot allows for an accessible comparison of the two securities over time. The increase in growth disparity over time is unmistakable, as QQQ pulls far ahead of IVV.

- One thing that must always be considered when investing are the fees associated with said investment.  Famously, In 2008, Warren Buffett placed a million-dollar wager with Protégé Partners, a hedge fund, with the winner being determined by whose investment strategy would yield a better return after fees.  The security that Buffett invested in was a simple S&P 500 Index fund- not dissimilar from the two ETFs examined here.  The bet took place over a span of nearly 10 years, with the managers at Protégé finally conceding in 2017.  While it should be noted that Mr. Buffett’s chosen index fund outperformed the hedge fund even before fees, the point that Mr. Buffett was making is that the fees charged for active management inevitably exceed any realized gains from that active management.  No public fund manager has proven to have the ability over a multi-year period to consistently outperform the market. And yet, the fees that some active managers charge would only be justified if they were able to do so.  

- While both of the ETFs examined here are passively managed, meaning that their fees are inherently lower than active managed securities, it is still important to take those fees (or expense ratio) into consideration.  For QQQ, the expense ratio is .20%.  Meaning that for every $10,000 invested in the fund, the yearly fee is $20.00.  IVV on the other hand, has a much lower expense ratio, .03%.  So, for every $10,000 invested in IVV, the yearly fee would be $3.00. For a point of reference, the mean expense ratio for ETF is .45%, which is much higher than both IVV and QQQ. While those fractional percentages may not sound expensive in the above example, over a span of years, the difference in those expense ratios can have a surprisingly large effect on one’s realized returns.

- In order to see how those fees played out, the table below was constructed to examine how the different fee rates effected the returns of both ETFs.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_excel_tables/ETF_after_fees_table.png)


- Again, using conditional formatting, the higher value cell is green and the lower red, and the pattern that has been consistent since the start of the analysis holds, QQQ outperforms IVV- even with its comparatively higher expense ratio.  The line graph aptly visualizes the after fees ROI over time for each fund, and it couldn’t be clearer that QQQ is the better performing fund.



![ALT_TEXT](https://github.com/Nickguild1993/Py_IVV_QQQ/blob/main/ETF_images/Growth_after_fees_ETF.png)



## Conclusions: 

- Throughout every type of analysis above, the more profitable investment vehicle for the time span of 01/02/2015 to 07/01/2021 was Invesco’s QQQ.  Even when considering that it has a higher expense ratio (which again, is still far below the average rate) than IVV, the returns simply aren’t on the same level over any segment of time in the analysis period.  While that’s excellent information, the next question is of course, “why does one security greatly outperform the other, when they’re both index funds, which have a mandate to track the equities on their respective index?”  The answer can be found in a few related points.  

- The first is that while they’re both index funds, they do not track the same index.  QQQ tracks the NASDAQ-100, which is an index of the 100 largest non-financial companies that are listed on the NASDAQ.  IVV, on the other hand, tracks the S&P 500, which is comprised of the 500 largest public companies listed on the exchanges.  

- The key difference is that the NASDAQ-100 has a much higher exposure to technology focused companies than the S&P 500. So, QQQ, which tracks the NASDAQ, has nearly double the percentage of it’s total holdings in Apple, Microsoft, Amazon, Alphabet and Facebook (40.55% vs. 20.97%) compared to IVV. Those 5 companies, and others like Nvidia, which QQQ also has a large stake in, represent some of the best performing stocks over the past five years, with that level of growth only becoming more pronounced in the last 18 months.  

- Zooming out, and just looking at the indices themselves, since 2008, the NASDAQ has outperformed the S&P 500 11 out of 13 years.  In that same period, the NASDAQ has had an annualized return of 16.2% compared to the S&P 500’s 9.8%. Clearly, the holdings composition of the two indices is driving the difference in returns.

- Another thing to consider is that hypothetically, having such a large proportion of a fund’s holdings tied up in one or two sectors, like the case is for QQQ, should expose it to more volatility. The reason is that sometimes, market corrections do not cause the same downturn in every sector. For example, if you have a market pull back caused by a prolonged global supply chain issue, that will effect very likely be more detrimental to consumer goods companies than healthcare companies. Because even though such an issue would have a negative effect on the entire world economy (not just the markets) damage to the global supply chain would be more damaging to companies that rely upon shipping to bring their physical goods that companies like Nestle, or Proctor & Gamble compared to Blue Cross Blue Shield or Humana which do not.

- What’s interesting is that QQQ’s readily apparent potential for higher volatility did not manifest itself during the timeframe of this analysis.  In fact, based on the simple rolling average graphs created in the analysis, it seemed to be more resilient to dips in value when compared to IVV.  This observation is backed up by comparing the volatility of the NASDAQ-100, which had an annual rolling volatility of 23% compared to S&P 500, which at 21%, experienced only slightly less annual volatility from 2008-2020.  These findings are surprising, since the first word any financial advisor utters to a client about how to mitigate risk while ensuring growth is “diversification”.  Which of course, is more than just a buzzword- it’s quite logical that diversifying one’s investments, or investing in a security like IVV, comprised of myriad top companies across every sector, would be a safer bet over investing in a fund like QQQ with its higher exposure to tech companies. 

- Perhaps one of the most important takeaways is trying to balance these two concepts- 1. Past results are the best indicator of future outcomes. 2. Just because something has happened before, does not mean it is guaranteed to happen again, or vise versa (an analog to the Gambler’s Fallacy).  Merging those two concepts and applying them to the analysis leads to understanding that just because QQQ, with its heavily weighted tech holdings, has performed better in the past, does not guarantee that it will continue to outperform IVV ad infinitum. However, if one believes that IVV will perform better in the future because perhaps its lower level of growth has caused it to be undervalued and QQQ will inherently become overvalued and bloated, you’d be betting against years of definitive results.  This highwire balancing act of competing ideas is what makes the analysis so fascinating, should one bet on a fund that has produced much higher returns but also is exposed to sector specific corrections, or should one possibly accept lower annual returns with the benefit of hypothetically far less risk?  Based on the results of the various analysis performed in this project, it is clear that the answer today is going with QQQ, and that answer does not look like it’s heading for a correction in the near future.



