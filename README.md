# Collaborative-filtering-for-transactions-data

## Steps followed:
 * Transforming data
 * Training and tuning of model parameters
 * Evaluation of model performance and selecting the optimal model
 
 # Problem Statement

I am building collaborative filtering models for recommending product items for a situation such as: Imagine a fast food chain releases a new mobile app allowing its customers to place orders before they even have to walk into the store. There are several opportunities for the app to show recommendations: When a customer first tap on the "order" page, we may recommend the first item to be added to the basket (e.g. a burger). After that, items good for pairing with the existing basket could be recommended. For example, if there is a burger already in the order basket, the app may want to recommend fries and/or drinks, rather than recommending another burger.


## Input data
There is a transaction history data in `trx_data.csv`. Each row represents a past order. It has two columns - customerId and products (separated by ","). The products column contains 1 to 10 product ID(s) of those being purchased, separated by "|".

Here is an example of the transaction records. We find customer 0 purchased 1 item in the first log entery, and customer 1 purchased 10 items in the second log entery (some are duplicated).

`customerId,products
0,20

1,2|2|23|68|68|111|29|86|107|152
2,111|107|29|11|11|11|33|23
1,164|227
3,2|2
6,144|144|55|267
7,136|204|261
3,79|8|8|48
9,102|2|2|297
10,84|77|286|259
11,25|127|127
0,18|183|288|171|289
11,79|8|8|38
1,2|2|20|20|20
7,251|143
`

***Things to be aware of about the data.***
* The `trx_data.csv` is a log of user purcases, so:
    * Users might be found on multiple lines in the csv with different basket items attached.
    * The products "basket" is not listed in any particular order.
        * For example the following data points can be considered as equivelent
            * `6,144|144|55|267` 
            * `6,267|144|55|144`
    * **However** the order of the basket logs is temporal, so in the above example log:
        * `1,2|2|23|68|68|111|29|86|107|152` was a basket of earlier purchases by user `1` than
        * `1,164|227`
