# JS-Tricks
JavaScript tips, tricks, techniques.  ES6 or greater. Chrome predominantly.

2. Get Value of a brower Cookie
Retrieve the value of a cookie by accessing with document.cookie
const cookie = name => `; ${document.cookie}`.split(`; ${name}
=`).pop().split(';').shift();
cookie('_ga');
// Result: "GA1.2.1929736587.1601974046

3. Convert RGB to Hex
rgbToHex enables you to convert RGB (Red, Green, Blue) values to their
corresponding hexadecimal representation.
const rgbToHex = (r, g, b) =>
"#" + ((1 << 24) + (r << 16) + (g << 8) +
b).toString(16).slice(1);
rgbToHex(0, 51, 255);
// Result: #0033f

// Result: #0033ff
4. Copy to Clipboard
Easily copy any text to clipboard using navigator.clipboard.writeText.
const copyToClipboard = (text) =>
navigator.clipboard.writeText(text);
copyToClipboard("Hello World");

5. Check if Date is Valid
Use the following snippet to check if a given date is valid or not.
const isDateValid = (...val) => !Number.isNaN(new
Date(...val).valueOf());
isDateValid("December 17, 1995 03:24:00");
// Result: true

6. Find the day of year
Find which is the day by a given date.
const dayOfYear = (date) =>
Math.floor((date - new Date(date.getFullYear(), 0, 0)) / 1000 / 60 / 60
/ 24);
dayOfYear(new Date()); // Result: 272
7. Capitalise a String
Javascript doesn't have an inbuilt capitalise function, so we can use the
following code for the purpose.
const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1)
capitalize("follow for more")
// Result: Follow for more
8. Find the number of days between two
days
Find the days between 2 given days using the following snippet.
const dayDif = (date1, date2) => Math.ceil(Math.abs(date1.getTime()
- date2.getTime()) / 86400000)
dayDif(new Date("2020-10-21"), new Date("2021-10-22"))
// Result: 366
9. Clear All Cookies
You can easily clear all cookies stored in a web page by accessing the
cookie using document.cookie and clearing it.
const clearCookies = document.cookie.split(';').forEach(cookie =>
document.cookie = cookie.replace(/^ +/, '').replace(/=.*/,
`=;expires=${new Date(0).toUTCString()};path=/`));
10. Generate Random Hex
You can generate random hex colors with Math.random and padEnd
properties.
const randomHex = () => `#${Math.floor(Math.random() *
0xffffff).toString(16).padEnd(6, "0")}`;
console.log(randomHex());
// Result: #92b008

11. Get Query Params from URL
You can easily retrieve query params from a url either by passing
window.location or the raw URL goole.com?search=easy&page=3
const getParameters = (URL) => {
URL = JSON.parse('{"' + decodeURI(URL.split("?")[1]).replace(/"/g, '\
\"').replace(/&/g, '","').replace(/=/g, '":"') +'"}');
return JSON.stringify(URL);
};
getParameters(window.location)
// Result: { search : "easy", page : 3 }

12. Log Time from Date
We can log time, in the format hour::minutes::seconds from a given
date.
const timeFromDate = date => date.toTimeString().slice(0, 8);
console.log(timeFromDate(new Date(2021, 0, 10, 17, 30, 0)));
// Result: "17:30:00"
13. Check if a number is even or odd
A simple JavaScript function named "isEven" determines if a number is
even or odd. It takes a "num" as input and returns true if even, false if
odd.
const isEven = num => num % 2 === 0;
console.log(isEven(2));
// Result: True
14. Find Average of Numbers
Find the average between multiple numbers using reduce method.
const average = (...args) => args.reduce((a, b) => a + b) /
args.length;
average(1, 2, 3, 4);
// Result: 2.5
15. Scroll to Top
You can use window.scrollTo(0, 0) method to automatic scroll to top.
Set both x and y as 0.
const goToTop = () => window.scrollTo(0, 0);
goToTop();
16. Reverse a string
You can easily reverse a string using split, reverse and join methods.
const reverse = str => str.split('').reverse().join('');
reverse('hello world');
// Result: 'dlrow olleh'
17. Check if array is empty
You can check if an array if empty with this snippet.
const isNotEmpty = arr => Array.isArray(arr) && arr.length > 0;
isNotEmpty([1, 2, 3]);
// Result: true
18. Get Selected Text
Get the text the user has select using inbuilt getSelection property.
const getSelectedText = () => window.getSelection().toString();
getSelectedText();
19. Shuffle an Array
Shuffling an array is super easy with sort and random methods.
const shuffleArray = (arr) => arr.sort(() => 0.5 - Math.random());
console.log(shuffleArray([1, 2, 3, 4]));
// Result: [ 1, 4, 3, 2 ]
20. Detect Dark Mode
Check if a user's device is in dark mode with the following code.
const isDarkMode = window.matchMedia &&
window.matchMedia('(prefers-color-scheme: dark)').matches
console.log(isDarkMode) // Result: True or False

