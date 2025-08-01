
1️⃣ Fundamentals (40%) – HTML, CSS, JS Basics
HTML Basics
Difference between <div> and <span>
<div> → Block-level, takes full width, starts on new line.
<span> → Inline, does not break line.
Use case: Layout containers vs inline text styling.
What are semantic tags in HTML and why are they important?
Examples: <header>, <footer>, <article>, <section>.
Improves readability, SEO, and accessibility.
Difference between relative and absolute paths in HTML
Relative → Based on current file location.
Absolute → Full URL or from root.
What are data attributes and when to use them?
Attributes like data-id="123".
Store extra information without extra classes or IDs.

CSS Basics
Explain the CSS box model
Content → Padding → Border → Margin.
Defines spacing and element sizing.
Difference between inline, block, and inline-block elements
block → Full width, new line (<div>).
inline → Width = content (<span>).
inline-block → Inline but allows width/height.
Difference between position: relative, absolute, fixed, and sticky
relative → Position relative to normal flow.
absolute → Relative to first positioned ancestor.
fixed → Relative to viewport.
sticky → Relative, then sticks on scroll.
Explain CSS specificity and its calculation
Inline styles (1000) > IDs (100) > Classes/Attributes (10) > Elements (1).

JavaScript Basics
Difference between == and ===
== → Loose equality (type conversion).
=== → Strict equality (no conversion).
Explain hoisting for var, let, and const
var → Hoisted as undefined.
let/const → Hoisted but in Temporal Dead Zone.
What is event bubbling and event delegation?
Bubbling → Event goes child → parent.
Delegation → Parent handles child events efficiently.
Difference between function declaration and function expression
Declaration → Hoisted, callable before definition.
Expression → Not hoisted.
Explain this in normal vs arrow functions
Normal → this depends on caller.
Arrow → this is lexical (from parent scope).

Browser Storage & API Basics
Difference between cookies, localStorage, and sessionStorage
Cookies → 4KB, sent to server, expire manually.
localStorage → Persistent, browser-only.
sessionStorage → Clears on tab close.
Difference between GET and POST requests
GET → URL params, cached, idempotent.
POST → Request body, create/update.
How would you handle API errors in frontend?
js
Copy
try {
  const res = await fetch('/api/data');
  if(!res.ok) throw new Error('Failed');
} catch(err) {
  alert(err.message);
}



Sample Fundamentals Coding
Reverse a string
js
Copy
function reverseString(str) {
  return str.split('').reverse().join('');
}

Truncate string to 10 chars and add ...
js
Copy
function truncate(str) {
  return str.length > 10 ? str.slice(0, 10) + '...' : str;
}

Count vowels in a string
js
Copy
function countVowels(str) {
  return (str.match(/[aeiou]/gi) || []).length;
}

Change all <p> text to uppercase
js
Copy
document.querySelectorAll('p').forEach(p => p.textContent = p.textContent.toUpperCase());


2️⃣ Problem-Solving (30%) – Coding & Logic
Easy
Palindrome check
js
Copy
function isPalindrome(str) {
  str = str.toLowerCase();
  return str === str.split('').reverse().join('');
}

Remove duplicates from array
js
Copy
function uniqueArray(arr) {
  return arr.filter((v, i) => arr.indexOf(v) === i);
}


Medium
First non-repeating character
js
Copy
function firstUniqueChar(str) {
  for(let ch of str) {
    if(str.indexOf(ch) === str.lastIndexOf(ch)) return ch;
  }
  return null;
}

Rotate array by k positions
js
Copy
function rotateArray(arr, k) {
  k %= arr.length;
  return arr.slice(-k).concat(arr.slice(0, -k));
}

Flatten nested array
js
Copy
function flatten(arr) {
  return arr.flat(Infinity);
}


Advanced
Group array of objects by key
js
Copy
function groupBy(arr, key) {
  return arr.reduce((acc, obj) => {
    (acc[obj[key]] = acc[obj[key]] || []).push(obj.name);
    return acc;
  }, {});
}

Merge overlapping intervals
js
Copy
function mergeIntervals(intervals) {
  intervals.sort((a,b) => a[0]-b[0]);
  const result = [intervals[0]];
  for(let i=1;i<intervals.length;i++){
    let last = result[result.length-1];
    if(intervals[i][0]<=last[1]) last[1] = Math.max(last[1], intervals[i][1]);
    else result.push(intervals[i]);
  }
  return result;
}

Deep clone an object
js
Copy
function deepClone(obj) {
  if(obj === null || typeof obj !== 'object') return obj;
  if(Array.isArray(obj)) return obj.map(deepClone);
  const clone = {};
  for(let key in obj) clone[key] = deepClone(obj[key]);
  return clone;
}


3️⃣ Applied Knowledge (30%) – Advanced JS, Debugging, Browser Concepts
Advanced JS
Explain closures with example
js
Copy
function counter() {
  let count = 0;
  return () => ++count;
}
const c = counter();
c(); // 1
c(); // 2

Explain prototypal inheritance
Objects inherit properties via prototype chain using Object.create() or class syntax.
Promise.all vs Promise.allSettled vs Promise.race
Promise.all → Fails fast on first rejection.
Promise.allSettled → Waits for all to settle (success or fail).
Promise.race → Resolves/rejects with the first settled promise.

Debugging & Browser
How to debug memory leaks in SPA
Chrome DevTools → Memory tab → Record Heap Snapshots → Check for detached DOM nodes.
How to debug slow rendering page
Performance tab → Record → Look for long tasks, layout shifts, and reflows.
Difference between repaint and reflow
Repaint → Visual change without layout change.
Reflow → Layout recalculation (heavier).

Performance
How CDN improves performance
Serves content from closest server, reduces latency.
What is lazy loading
Loading components/images only when needed to reduce initial load time.
What are service workers
Scripts running in background for caching/offline support.
Cache busting
Use versioned/hashes filenames like app.123.js to ensure users get new versions.

Security
How to prevent XSS
Escape user input, use Content Security Policy (CSP).
How to prevent CSRF
Use same-site cookies or anti-CSRF tokens.
How to handle CORS errors
Set proper Access-Control-Allow-Origin headers or use proxy servers.

