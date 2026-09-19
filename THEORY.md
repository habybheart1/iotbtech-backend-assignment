# QUESTION 1

Write the **exact** output of both lines. Then explain in one sentence why the two outputs differ — what do indices `0`, `1`, and `2+` of `process.argv` represent?

## ANSWER 1

**Output of both lines**

```js Output
[
  "C:\\Program Files\\nodejs\\node.exe",
  "C:\\Users\\hp\\Desktop\\check\\app.js",
  "--port",
  "8080",
  "--host",
  "localhost",
];
```

```js output
["--port", "8080", "--host", "localhost"];
```

The output differs because `console.log(process.argv)` is array of everything typed after node. The exact paths at indices `[0] and [1] vary by machine, `argv[0]`is the Node executable,`argv[1]`is the script path, and indices 2+ contain the command-line arguments.
while`console.log(process.argv.slice(2));` remove item at index o and 1, it prints the command-line arguments.

---

# QUESTION 2

Why do you almost always write `process.argv.slice(2)` and never `process.argv` directly in a real CLI tool? What happens the day someone runs your script from a different folder or with a wrapper like `bun run app.js`?

## ANSWER 2

It prevent mistaken the executable path and script path from being mistaken as the user input. Running the script from a different folder does not change the first two entries. with wrapper like `bun run app.js` it gives the same result.

---

# QUESTION 3

Write the three outputs. Then explain **why** the first two numbers are different from each other, and why the third line gives a different number from the first. Use the words "bytes" and "characters" correctly.

## ANSWER 3

```js
console.log(Buffer.from("مرحبا").length);
```

**output: 10** is bytes, not characters. buffer for each letter length is 2. EXAMPLE

```js
const buf = Buffer.from("م");
console.log(buf);
```
_output is <Buffer d9 85>_ which .length is equivalent to 2

```js
console.log(Buffer.from("hello").length);
```
**output: 5** is bytes, not characters.

```js
console.log("مرحبا".length);
```
**output: 5**


