# Unit 4 Challenge: Console Finances

![badmath](https://img.shields.io/github/issues/YueHuaHua/Console-Finances) ![batmath](https://img.shields.io/github/issues-pr-closed/YueHuaHua/Console-Finances) ![badmath](https://img.shields.io/github/license/YueHuaHua/Console-Finances)

</br>

## Table of Contents
* [Description](#description)
* [Features](#features)
* [Installation & Deployment](#installation-and-deployment)
* [Usage](#usage)
* [License](#license)

</br>

## Overview
 
This challenge presents a real-world situation in which the newfound JavaScript skills will come in handy. The code has been built to analyze the given set of a financial records data of a company. The dataset composed of arrays with two fiels, Date and Profit/Losses that has been stated first in `index.js` file.

</br>

## Features
This application is used to calculate the number of months, total profits/loss, the average change in term of profits/loss, and the biggest and least increase/decrease of profit for financial analysis purpose.
</br>

### The Number of Months
The number of months included in the dataset can be achieved by calculating the length of the array. To prevent duplicates of date, several steps has been taken to handle the exception.
</br>
First, the dataset is divided into two different arrays: Months and Money.

  ```javascript
//get the date only
var months = finances.map(function(tuple){
    return tuple[0];
});

//removing any duplicates for exceptional
function onlyUnique(value, index, self) {
    return self.indexOf(value) === index;
}

var monthsUnique = months.filter(onlyUnique)

//get the money only
var money = finances.map(function(tuple){
    return tuple[1];
});
  ```
</br>

Then, the total number of months can be obtained by calculating the length of the Months array.
  ```javascript
var totalMonths = monthsUnique.length;
  ```
</br>

Output:

  ```text
  Total Months: 25
  ```
</br>

### Total Profit / Loss
The net total amount of Profit/Losses by adding all data in Money array for over the entire period.
  ```javascript
//total profit/losses
var sumProfit = money.reduce((a,b) => a+b, 0);
  ```
</br>

Output:

  ```text
  Total: $38382578
  ```
</br>
  
### The Average Change
The average of the changes in profit/losses over the entire period can be obtained by tracking the total change in profits from month to month. A new array is created (Changes array) to save the change values.
  ```javascript
var changes = [];
for (let i=0; i<money.length-1; i++){
    changes[i] = money[i+1] - money[i];
}
  ```
</br>

Then, the sum of changes can be calculated by adding each component of Changes array.
  ```javascript
// get the sum of changes
var netChanges = changes.reduce((a,b) => a+b, 0);
  ```
</br>

Hence, the average of the changes is
  ```javascript
var averageChanges = (netChanges / changes.length).toFixed(2); //2 decimal places
  ```
</br>

Output:

  ```text
  Net Changes: $-196785
  Average Changes: $-2315.12
  ```
</br>

### The Greatest Increase in Profits
As the understanding of the greatest increase in profits has been divided into two, there are two calculations that have been done in this code.
</br>

The first one is simply the greatest profit for over the period which can be obtained by finding the maximum value in Money array.
  ```javascript
//get the biggest profits
var maxProfit = money.reduce((a, b) => Math.max(a, b), -Infinity);
var maxProfitIndex = money.indexOf(maxProfit);
var maxProfitMonth = months[maxProfitIndex];
  ```
</br>

Output:

  ```text
Biggest Profit: Feb-2012 ($1170593)
  ```
</br>

While the second one is the greatest change in profit which can be obtained by finding the maximum value in Change array.
  ```javascript
//get the greatest increase in profits (date and amount) over the entire period
var maxChanges = changes.reduce((a, b) => Math.max(a, b), -Infinity);
var maxChangesIndex = changes.indexOf(maxChanges);
var maxChangesMonth = months[maxChangesIndex+1];
  ```
</br>

Output:

  ```text
Greatest Increase in Profits: Feb-2012 ($1926159)
  ```
</br>

### The Greatest Decrease in Profits
Similar to previous one, as the understanding of the greatest decrease in profits also has been divided into two, there are two calculations that have been done in this code.
</br>

The first one is simply the greatest loss or the least profit for over the period which can be obtained by finding the minimum value in Money array.
  ```javascript
//get the least profits
var minProfit = money.reduce((a, b) => Math.min(a, b), );
var minProfitIndex = money.indexOf(minProfit);
var minProfitMonth = months[minProfitIndex];
  ```
</br>

Output:

  ```text
Smallest Profit: Sep-2013 ($-1196225)
  ```
</br>

While the second one is the greatest change in loss which can be obtained by finding the minimum value in Change array.
  ```javascript
//get the greatest decrease in losses (date and amount) over the entire period
var minChanges = changes.reduce((a, b) => Math.min(a, b), );
var minChangesIndex = changes.indexOf(minChanges);
var minChangesMonth = months[minChangesIndex+1];
  ```
</br>

Output:

  ```text
Greatest Decrease in Profits: Sep-2013 ($-2196167)
  ```
</br>

### Code Output
The obtained result that shows in web console is as the following:
  ```text
Financial Analysis
-----------------------
Total Months: 86
Total: $38382578
Average Changes: $-2315.12
Greatest Increase in Profits: Feb-2012 ($1926159)
Greatest Decrease in Profits: Sep-2013 ($-2196167)
  ```
</br>

## Installation and Deployment

Installation not required, since this is a "plug and play" type of application. The user can simply run it locally by clicking on the `index.html` file and opening in either their default or preferred browser.

Application can also be accessed [here](https://yuehuahua.github.io/Console-Finances/).

</br>

## Usage 

* Simply right click on the page and and choose `inspect`
* Then, select the `Console` tab inside the `inspect` to see the code output

</br>

## License

Licensed under the [MIT license](https://github.com/git/git-scm.com/blob/main/MIT-LICENSE.txt). See LICENSE for the full details.

