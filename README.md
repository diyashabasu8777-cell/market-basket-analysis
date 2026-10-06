# Market Basket Analysis on Retail Transactions

Finding products that UK customers tend to buy together, to suggest cross-sell and bundle ideas.

## Dataset
UCI Online Retail data (about 541,910 rows of transactions from a UK online retailer). Not included here because of its size: download it and place the file next to the notebook, then update the file name in the loading cell.

## What I did
1. Cleaned 541,910 rows to 527,725 (removed cancelled invoices, returns, zero price or quantity, and non-product codes like postage).
2. Focused on UK customers (17,901 invoices) and loaded the data into SQLite.
3. Used SQL (CTEs, joins, a RANK window function, GROUP BY and HAVING) to pick the 200 most popular products and build 13,515 baskets with 2 or more items.
4. Ran Apriori (minimum support 2%) and generated association rules with mlxtend.

## Results
- 455 frequent item sets and 674 rules with lift above 1 (206 with confidence of 0.5 or more).
- Strongest rule: about 78% of baskets with the Wooden Star Christmas Scandinavian decoration also had the Wooden Heart one (lift 20.9).

## Cross-sell suggestions
1. Bundle the Wooden Star and Wooden Heart Christmas decorations.
2. Sell the Charlotte bag designs (Woodland, Strawberry, Suki, Pink Polkadot) as a set or place them together.
3. Offer the Pink, Green and Roses Regency teacups as a mixed set.

## Limitations
- Many strong rules are variants of the same product family, which is less surprising.
- Only the top 200 products and one year of data were used.
- Association does not mean one purchase causes the other.

## How to run
```
pip install pandas numpy matplotlib mlxtend openpyxl
jupyter notebook market_basket_analysis.ipynb
```
