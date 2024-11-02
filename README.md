# JS-Tricks
JavaScript tips, tricks, techniques.  ES6 or greater. Chrome predominantly.
<b>
2. Get Value of a browser Cookie</b>
Retrieve the value of a cookie by accessing with document.cookie
```
const cookie = name => `; ${document.cookie}`.split(`; ${name}
=`).pop().split(';').shift();
cookie('_ga');
// Result: "GA1.2.1929736587.1601974046
```
3. Convert RGB to Hex
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
4. Copy to Clipboard
Easily copy any text to clipboard using navigator.clipboard.writeText.
```
const copyToClipboard = (text) =>
navigator.clipboard.writeText(text);
copyToClipboard("Hello World");
```
5. Check if Date is Valid
Use the following snippet to check if a given date is valid or not.
```
const isDateValid = (...val) => !Number.isNaN(new
Date(...val).valueOf());
isDateValid("December 17, 1995 03:24:00");
// Result: true
```
7. Find the day of year
Find which is the day by a given date.
```
const dayOfYear = (date) =>
Math.floor((date - new Date(date.getFullYear(), 0, 0)) / 1000 / 60 / 60
/ 24);
dayOfYear(new Date()); // Result: 272
```
8. Capitalise a String
Javascript doesn't have an inbuilt capitalise function, so we can use the
following code for the purpose.
```
const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1)
capitalize("follow for more")
```
// Result: Follow for more
9. Find the number of days between two
days
Find the days between 2 given days using the following snippet.
```
const dayDif = (date1, date2) => Math.ceil(Math.abs(date1.getTime()
- date2.getTime()) / 86400000)
dayDif(new Date("2020-10-21"), new Date("2021-10-22"))
// Result: 366
```
9. Clear All Cookies
You can easily clear all cookies stored in a web page by accessing the
cookie using document.cookie and clearing it.
```
const clearCookies = document.cookie.split(';').forEach(cookie =>
document.cookie = cookie.replace(/^ +/, '').replace(/=.*/,
`=;expires=${new Date(0).toUTCString()};path=/`));
```
10. Generate Random Hex
You can generate random hex colors with Math.random and padEnd
properties.
```
const randomHex = () => `#${Math.floor(Math.random() *
0xffffff).toString(16).padEnd(6, "0")}`;
console.log(randomHex());
// Result: #92b008
```
11. Get Query Params from URL
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
12. Log Time from Date
We can log time, in the format hour::minutes::seconds from a given
date.
```
const timeFromDate = date => date.toTimeString().slice(0, 8);
console.log(timeFromDate(new Date(2021, 0, 10, 17, 30, 0)));
// Result: "17:30:00"
```
13. Check if a number is even or odd
A simple JavaScript function named "isEven" determines if a number is
even or odd. It takes a "num" as input and returns true if even, false if
odd.
```
const isEven = num => num % 2 === 0;
console.log(isEven(2));
// Result: True
```
14. Find Average of Numbers
Find the average between multiple numbers using reduce method.
```
const average = (...args) => args.reduce((a, b) => a + b) /
args.length;
average(1, 2, 3, 4);
// Result: 2.5
```
15. Scroll to Top
You can use window.scrollTo(0, 0) method to automatic scroll to top.
Set both x and y as 0.
```
const goToTop = () => window.scrollTo(0, 0);
goToTop();
```
16. Reverse a string
You can easily reverse a string using split, reverse and join methods.
```
const reverse = str => str.split('').reverse().join('');
reverse('hello world');
// Result: 'dlrow olleh'
```
17. Check if array is empty
You can check if an array if empty with this snippet.
const isNotEmpty = arr => Array.isArray(arr) && arr.length > 0;
```
isNotEmpty([1, 2, 3]);
// Result: true
```
18. Get Selected Text
Get the text the user has select using inbuilt getSelection property.
```
const getSelectedText = () => window.getSelection().toString();
getSelectedText();
```
19. Shuffle an Array
Shuffling an array is super easy with sort and random methods.
```
const shuffleArray = (arr) => arr.sort(() => 0.5 - Math.random());
console.log(shuffleArray([1, 2, 3, 4]));
// Result: [ 1, 4, 3, 2 ]
```
20. Detect Dark Mode
Check if a user's device is in dark mode with the following code.
```
const isDarkMode = window.matchMedia &&
window.matchMedia('(prefers-color-scheme: dark)').matches
console.log(isDarkMode) // Result: True or False
```
21. Remove Duplicated from Array
You can easily remove duplicates with Set in JavaScript. Its a life saver.
```
const removeDuplicates = (arr) => [...new Set(arr)];
console.log(removeDuplicates([1, 2, 3, 3, 4, 4, 5, 5, 6]));
// Result: [ 1, 2, 3, 4, 5, 6 ]
```
22. Get the Length of a String
getLength efficiently calculates the length of a given string using .length
property.
```
const getLength = (str) => str.length;
getLength("Hello, world!");
// Result: 13
```
23. Calculate the Area of a Circle
Calculate the area of a circle given its radius.
const calculateCircleArea = (radius) => Math.PI * Math.pow(radius,
```
2);
calculateCircleArea(5);
// Result: 78.53981633974483
```
24. Check if a Number is Prime
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
25. Count Occurrences of a Character in a
String
Count the occurrences of a specific character in a given string.
```
const countOccurrences = (str, char) => str.split(char).length - 1;
countOccurrences("banana", "a");
// Result: 3
```
26. Remove Leading and Trailing
Whitespaces
Remove leading and trailing whitespaces from a given string.
```
const removeWhitespaces = (str) => str.trim();
removeWhitespaces(" Hello, world! ");
// Result: "Hello, world!"
```
27. Generate a Random Number within a
Range
Generate a random integer within a specified range.
```
const randomInRange = (min, max) => Math.floor(Math.random() *
(max - min + 1)) + min;
randomInRange(1, 10);
// Result: Random number between 1 and 10 (inclusive)
```
28. Convert Seconds to HH:MM:SS Format
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
29. Get the Last Element of an Array
Retrieve the last element of a given array.
```
const getLastElement = (arr) => arr[arr.length - 1];
getLastElement([1, 2, 3, 4]);
// Result: 4
```
30. Sort an Array of Numbers in Ascending
Order
Sort a given array of numbers in ascending order.
```
const sortAscending = (arr) => arr.slice().sort((a, b) => a - b);
sortAscending([3, 1, 4, 1, 5, 9, 2, 6, 5, 3]);
// Result: [1, 1, 2, 3, 3, 4, 5, 5, 6, 9]
```
31. Check if a String is Palindrome
Determine if a given string is a palindrome.
```
const isPalindrome = (str) => str === str.split('').reverse().join('');
isPalindrome("level");
// Result: true
```
32. Calculate Factorial of a Number
Calculate the factorial of a given number.
```
const factorial = (num) => {
if (num === 0 || num === 1) return 1;
return num * factorial(num - 1);
};
factorial(5);
// Result: 120
```
33. Sum all Numbers in an Array
Calculate the sum of all numbers in a given array.
```
const sumArray = (arr) => arr.reduce((acc, val) => acc + val, 0);
sumArray([1, 2, 3, 4, 5]);
// Result: 15
```
34. Find the Maximum Value in an Array
Find the maximum value in a given array of numbers.
```
const findMax = (arr) => Math.max(...arr);
findMax([10, 5, 8, 20, 3]);
// Result: 20
```
35. Get the Current Date in DD/MM/YYYY
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
