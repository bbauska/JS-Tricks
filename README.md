# JS-Tricks
JavaScript tips, tricks, techniques.  ES6 or greater. Chrome predominantly.

<b>1. Get Value of a browser Cookie</b>
Retrieve the value of a cookie by accessing with document.cookie
```
const cookie = name => `; ${document.cookie}`.split(`; ${name}
=`).pop().split(';').shift();
cookie('_ga');
// Result: "GA1.2.1929736587.1601974046
```
<b>2. Convert RGB to Hex</b>
rgbToHex enables you to convert RGB (Red, Green, Blue) values to their
corresponding hexadecimal representation.
```
const rgbToHex = (r, g, b) =>
"#" + ((1 << 24) + (r << 16) + (g << 8) +
b).toString(16).slice(1);
rgbToHex(0, 51, 255);
// Result: #0033f
// Result: #0033ff
```
<b>3. Copy to Clipboard</b>
Easily copy any text to clipboard using navigator.clipboard.writeText.
```
const copyToClipboard = (text) =>
navigator.clipboard.writeText(text);
copyToClipboard("Hello World");
```
<b>4. Check if Date is Valid</b>
Use the following snippet to check if a given date is valid or not.
```
const isDateValid = (...val) => !Number.isNaN(new
Date(...val).valueOf());
isDateValid("December 17, 1995 03:24:00");
// Result: true
```
<b>5. Find the day of year</b>
Find which is the day by a given date.
```
const dayOfYear = (date) =>
Math.floor((date - new Date(date.getFullYear(), 0, 0)) / 1000 / 60 / 60
/ 24);
dayOfYear(new Date()); // Result: 272
```
<b>6. Capitalise a String</b>
Javascript doesn't have an inbuilt capitalise function, so we can use the
following code for the purpose.
```
const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1)
capitalize("follow for more")
```
// Result: Follow for more
<b>7. Find the number of days between two days</b>
Find the days between 2 given days using the following snippet.
```
const dayDif = (date1, date2) => Math.ceil(Math.abs(date1.getTime()
- date2.getTime()) / 86400000)
dayDif(new Date("2020-10-21"), new Date("2021-10-22"))
// Result: 366
```
<b>8. Clear All Cookies</b>
You can easily clear all cookies stored in a web page by accessing the
cookie using document.cookie and clearing it.
```
const clearCookies = document.cookie.split(';').forEach(cookie =>
document.cookie = cookie.replace(/^ +/, '').replace(/=.*/,
`=;expires=${new Date(0).toUTCString()};path=/`));
```
<b>9. Generate Random Hex</b>
You can generate random hex colors with Math.random and padEnd
properties.
```
const randomHex = () => `#${Math.floor(Math.random() *
0xffffff).toString(16).padEnd(6, "0")}`;
console.log(randomHex());
// Result: #92b008
```
<b>10. Get Query Params from URL</b>
You can easily retrieve query params from a url either by passing
window.location or the raw URL goole.com?search=easy&page=3
```
const getParameters = (URL) => {
URL = JSON.parse('{"' + decodeURI(URL.split("?")[1]).replace(/"/g, '\
\"').replace(/&/g, '","').replace(/=/g, '":"') +'"}');
return JSON.stringify(URL);
};
getParameters(window.location)
// Result: { search : "easy", page : 3 }
```
<b>11. Log Time from Date</b>
We can log time, in the format hour::minutes::seconds from a given
date.
```
const timeFromDate = date => date.toTimeString().slice(0, 8);
console.log(timeFromDate(new Date(2021, 0, 10, 17, 30, 0)));
// Result: "17:30:00"
```
<b>12. Check if a number is even or odd</b>
A simple JavaScript function named "isEven" determines if a number is
even or odd. It takes a "num" as input and returns true if even, false if
odd.
```
const isEven = num => num % 2 === 0;
console.log(isEven(2));
// Result: True
```
<b>13. Find Average of Numbers</b>
Find the average between multiple numbers using reduce method.
```
const average = (...args) => args.reduce((a, b) => a + b) /
args.length;
average(1, 2, 3, 4);
// Result: 2.5
```
<b>14. Scroll to Top</b>
You can use window.scrollTo(0, 0) method to automatic scroll to top.
Set both x and y as 0.
```
const goToTop = () => window.scrollTo(0, 0);
goToTop();
```
<b>15. Reverse a string</b>
You can easily reverse a string using split, reverse and join methods.
```
const reverse = str => str.split('').reverse().join('');
reverse('hello world');
// Result: 'dlrow olleh'
```
<b>16. Check if array is empty</b>
You can check if an array if empty with this snippet.
const isNotEmpty = arr => Array.isArray(arr) && arr.length > 0;
```
isNotEmpty([1, 2, 3]);
// Result: true
```
<b>17. Get Selected Text</b>
Get the text the user has select using inbuilt getSelection property.
```
const getSelectedText = () => window.getSelection().toString();
getSelectedText();
```
<b>18. Shuffle an Array</b>
Shuffling an array is super easy with sort and random methods.
```
const shuffleArray = (arr) => arr.sort(() => 0.5 - Math.random());
console.log(shuffleArray([1, 2, 3, 4]));
// Result: [ 1, 4, 3, 2 ]
```
<b>19. Detect Dark Mode</b>
Check if a user's device is in dark mode with the following code.
```
const isDarkMode = window.matchMedia &&
window.matchMedia('(prefers-color-scheme: dark)').matches
console.log(isDarkMode) // Result: True or False
```
<b>20. Remove Duplicated from Array</b>
You can easily remove duplicates with Set in JavaScript. Its a life saver.
```
const removeDuplicates = (arr) => [...new Set(arr)];
console.log(removeDuplicates([1, 2, 3, 3, 4, 4, 5, 5, 6]));
// Result: [ 1, 2, 3, 4, 5, 6 ]
```
<b>21. Get the Length of a String</b>
getLength efficiently calculates the length of a given string using .length
property.
```
const getLength = (str) => str.length;
getLength("Hello, world!");
// Result: 13
```
<b>22. Calculate the Area of a Circle</b>
Calculate the area of a circle given its radius.
const calculateCircleArea = (radius) => Math.PI * Math.pow(radius,
```
2);
calculateCircleArea(5);
// Result: 78.53981633974483
```
<b>23. Check if a Number is Prime</b>
Determine if a given number is a prime number.
```
const isPrime = (num) => {
if (num <= 1) return false;
for (let i = 2; i <= Math.sqrt(num); i++) {
if (num % i === 0) return false;
}
return true;
};
isPrime(13);
// Result: true
```
<b>24. Count Occurrences of a Character in a String</b>
Count the occurrences of a specific character in a given string.
```
const countOccurrences = (str, char) => str.split(char).length - 1;
countOccurrences("banana", "a");
// Result: 3
```
<b>25. Remove Leading and Trailing</b>
Whitespaces
Remove leading and trailing whitespaces from a given string.
```
const removeWhitespaces = (str) => str.trim();
removeWhitespaces(" Hello, world! ");
// Result: "Hello, world!"
```
<b>26. Generate a Random Number within a Range</b>
Generate a random integer within a specified range.
```
const randomInRange = (min, max) => Math.floor(Math.random() *
(max - min + 1)) + min;
randomInRange(1, 10);
// Result: Random number between 1 and 10 (inclusive)
```
<b>27. Convert Seconds to HH:MM:SS Format</b>
Convert a given number of seconds into the "hours:minutes:seconds"
format.
```
const secondsToHHMMSS = (seconds) => {
const pad = (num) => String(num).padStart(2, '0');
const hours = Math.floor(seconds / 3600);
const minutes = Math.floor((seconds % 3600) / 60);
const secs = seconds % 60;
return `${pad(hours)}:${pad(minutes)}:${pad(secs)}`;
};
secondsToHHMMSS(3660); // Result: "01:01:00"
```
<b>28. Get the Last Element of an Array</b>
Retrieve the last element of a given array.
```
const getLastElement = (arr) => arr[arr.length - 1];
getLastElement([1, 2, 3, 4]);
// Result: 4
```
<b>29. Sort an Array of Numbers in Ascending</b>
Order
Sort a given array of numbers in ascending order.
```
const sortAscending = (arr) => arr.slice().sort((a, b) => a - b);
sortAscending([3, 1, 4, 1, 5, 9, 2, 6, 5, 3]);
// Result: [1, 1, 2, 3, 3, 4, 5, 5, 6, 9]
```
<b>30. Check if a String is Palindrome</b>
Determine if a given string is a palindrome.
```
const isPalindrome = (str) => str === str.split('').reverse().join('');
isPalindrome("level");
// Result: true
```
<b>31. Calculate Factorial of a Number</b>
Calculate the factorial of a given number.
```
const factorial = (num) => {
if (num === 0 || num === 1) return 1;
return num * factorial(num - 1);
};
factorial(5);
// Result: 120
```
<b>32. Sum all Numbers in an Array</b>
Calculate the sum of all numbers in a given array.
```
const sumArray = (arr) => arr.reduce((acc, val) => acc + val, 0);
sumArray([1, 2, 3, 4, 5]);
// Result: 15
```
<b>33. Find the Maximum Value in an Array</b>
Find the maximum value in a given array of numbers.
```
const findMax = (arr) => Math.max(...arr);
findMax([10, 5, 8, 20, 3]);
// Result: 20
```
<b>34. Get the Current Date in DD/MM/YYYY</b>
Format
Get the current date in the "DD/MM/YYYY" format.
```
const getCurrentDate = () => {
const date = new Date();
const day = String(date.getDate()).padStart(2, '0');
const month = String(date.getMonth() + 1).padStart(2, '0');
const year = date.getFullYear();
return `${day}/${month}/${year}`;
};
getCurrentDate(); // Result: "02/08/2023"
```
