# Cascade FinTech Assessment

![alt text](https://github.com/brolz/CascadeAssessment/blob/main/src/assets/screenshot.png?raw=true)

## Problem
```
Display the given data in vuex store and display it to the user.
```

## Solution
```
I started by grabbing the data with a getter and passing it to my TransactionsList component.
 In my component I used a 'v-for' directive to render the list of items based 
 on the data given.

To calculate the balances I created two computed properties, One to gather 
all the transaction amounts that were 'billed' and get the remaing balance, 
and the other to get the total balance after every transaction is completed. 
I then used them in my Latest and Pending Transactions sections respectively.

For the dates I used vanilla Js Date object and passed the transaction 
date followed by making it a string and slicing it to only show Day, Month, 
Date, Year, and Time.
```
