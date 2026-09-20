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

---

# QUESTION 4

Explain, step by step, why this approach will crash the machine — and state precisely where the file _goes_ in memory. Then explain how `createReadStream` avoids the problem even though it reads the _same_ file.

## ANSWER 4

`readFileSync()` tries to materialize the entire file in RAM, while `createReadStream()` keeps only a small portion of the file in memory at a time.

```JS
const data = readFileSync("huge.log", "utf8");
```

It gives me the entire contents right now.

```JS
const stream = createReadStream("huge.log");
```
Give me the contents progressively as I need them.

`createFileSync()` It creates a readable stream that processes the file incrementally

---

# QUESTION 5
In your own words, what is the practical difference between `readable.pipe(writable)` and `pipeline(readable, writable)`? Invent one failure scenario where `pipe()` leaves a problem behind and `pipeline()` does not.

## ANSWER 
Pipe: Connect the readable and writable streams.
Pipeline: Run these streams together as one operation and deal with failure/cleanup as a unit

The practical difference is that pipeline can handle error and they wouldnot be break in the code if network fails or any other error and clean up.Pipe take data from readable and send it to writable but erroe handling is not automatically done.

---

# QUESTION 6
Write the two expected outputs. Check by running it. If yours was wrong, write down the correct values **and** what you misunderstood.

## ANSWER 
```javascript
const buf = Buffer.from("Node.js");
console.log(buf.toString("hex"));
console.log(buf.toString("base64"));
```
**OUTPUT: 4e6f64652e6a73 and Tm9kZS5qcw==**
The first line is the UTF-8 bytes represented in hexadecimal; the second is the same bytes encoded as Base64. The provided values are correct.

---

# QUESTION 7
Streams keep memory flat." What does "flat" mean here? Contrast the memory profile of the *bucket* approach vs the *pipe* approach for a growing file (10,000 rows → 10,000,000 rows). Which one becomes flat, and which one grows linearly?

## ANSWER
Flat means its not linear rather it keeps the memory constant
Bucket approach: memory grows linearly with the amount of data retained.
Pipe/stream approach: memory is approximately flat because data is processed incrementally.

---

# QUESTION 8
Give **three** concrete things Bun does out of the box that plain Node does not. For each, say whether you'd reach for Bun or Node on a real team project today, and why.

## ANSWER
Buns maturity is newer, smaller, it's startup is much faster (would prefer bun), install spped is faster (bun install), typeScript runs `.ts` directly and Bun has strong Node compatibility and can run many existing Node projects (would prefer node).

---

# CLASS 32: Express & TypeScript

# QUESTION 9
What does each request respond with, and **why**? Mention route order and express's "first matching route wins" rule in your answer.

## ANSWER

---

# QUESTION 10
In `app.get("/api/products/:id", handler)`, what type is `req.params.id`? Write the exact expression you'd use to get it as a **number**, and explain why Express does not convert it for you.

## ANSWER 

