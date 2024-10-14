# Financial Forecasting from Textual and Tabular Time Series

Please cite our paper if you use the code or data in your work:

## Introduction

This repository will contain the data and code used in the EMNLP 2024 paper. We will be adding them as soon as we can. 

## Data 

We source Reported Earnings per Share (EPS) and Analyst Consensus Estimates of EPS from FactSet Fundamentals (https://go.factset.com/marketplace/catalog/product/factset-fundamentals) and Consensus Estimates (https://go.factset.com/marketplace/catalog/product/factset-estimates-consensus), respectively, to compute the Earnings Surprise target variable. We collect English conference calls from FactSet Document Distributor (https://go.factset.com/marketplace/catalog/product/factset-document-distributor-xml-transcripts).

We source raw company filings (10Ks) from the Notre Dame Software Repository for Accounting and Finance (https://sraf.nd.edu/sec-edgar-data/). We apply extensive preprocessing to extract Section 7A: Management Discussion and Analysis (MDA). We use a variety of regular expressions to extract the MDA section and filter the resulting section text for quality in a refined iterative process.

We collect the monthly macroeconomic indices from the ST. Louis FED (https://fred.stlouisfed.org/).

We thank FactSet and AJOVista for their permission to release this data to the academic community. 

We merge all data across modalities to align with the quarterly fiscal period end dates for each company. Therefore, for each Earnings Surprise forecast quarter date (e.g. Q2 2020), we select data that was available within 5 business days of the end of the previous quarter fiscal end date, including all financial variables, quarterly financial reports, earnings conference calls, and macroeconomic data. Although some of this data is available at a higher frequency than once a quarter, such as stock price-based financial variables or monthly economic indicators, we only select the values of such data that were available as of 5 business days after the last fiscal period end date. Thus, our predictions are always made 3 months in advance of the earnings report date. We leave it to future work to explore the value in updating the predictions at a higher frequency.

We select 15 commonly used market price and accounting-based financial variables available at the time of the report date from the definitions and cluster classifications in Swade et al., (2023; https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4605976). This set includes dividend yield (Value), earnings-to-price (Value), sales-to-price (Value), book value-to-price (Value), sales growth (Growth), earnings growth (Growth), gross profit to assets (Profitability), net income to equity (Profitability), net income to assets (Profitability), medium-term price momentum (Momentum), short-term price reversal (Reversal), price volatility (Low Risk), market leverage (Debt Issuance), share turnover (Low Risk), and market capitalization (Size). This set of variables is not exhaustive but has been shown to span the set of principle components of firm characteristics. 

## Code
