Chalo, aaj hum regex ke mazeed kuch patterns explore karte hain jo tumhare data structure aur algorithms ke problems solve karne mein madad karenge. Main hindi aur English mix karke samjhata hoon.

### 1. Basic Character Matching

**Problem 1: Create a regex pattern to match all occurrences of the word "code" in a given text, regardless of case.**

Regex pattern: `/code/gi`

- `/code/` => Ye pattern "code" ko match karega.
- `g` => Global flag, jo ki text mein saare occurrences ko match karega.
- `i` => Case-insensitive flag, jo ki uppercase aur lowercase, dono forms ko match karega.

Example:

```javascript
let text = "Code is fun. I like to code.";
let pattern = /code/gi;
let matches = text.match(pattern);
console.log(matches); // ["Code", "code"]
```

**Problem 2: Write a regex to find all instances of the word "bug" that are not part of larger words (e.g., should match "bug" but not "debug" or "buggy").**

Regex pattern: `/\bbug\b/g`

- `\b` => Word boundary, jo ensure karega ki "bug" poora word ho.
- `g` => Global flag, jo ki saare matches ko dhundega.

Example:

```javascript
let text = "bug is different from debug and buggy.";
let pattern = /\bbug\b/g;
let matches = text.match(pattern);
console.log(matches); // ["bug"]
```

### 2. Character Classes

**Problem 1: Create a regex to match any vowel (a, e, i, o, u) in a given string, regardless of case.**

Regex pattern: `/[aeiou]/gi`

- `[aeiou]` => Character class jo vowels ko match karega.
- `g` => Global flag for all occurrences.
- `i` => Case-insensitive flag.

Example:

```javascript
let text = "Regular Expressions are powerful!";
let pattern = /[aeiou]/gi;
let matches = text.match(pattern);
console.log(matches); // ["e", "u", "a", "e", "o", "i", "o", "a", "e", "o", "u"]
```

**Problem 2: Write a regex to match any non-digit character in a string.**

Regex pattern: `/\D/g`

- `\D` => Non-digit character class.

Example:

```javascript
let text = "123 Main St.";
let pattern = /\D/g;
let matches = text.match(pattern);
console.log(matches); // [" ", "M", "a", "i", "n", " ", "S", "t", "."]
```

### 3. Quantifiers

**Problem 1: Create a regex to match phone numbers in the format (xxx) xxx-xxxx, where x represents any digit.**

Regex pattern: `/\(\d{3}\) \d{3}-\d{4}/`

- `\(\d{3}\)` => Opening parenthesis ke saath 3 digits.
- `\d{3}` => 3 digits.
- `-` => Hyphen.
- `\d{4}` => 4 digits.

Example:

```javascript
let text = "Call me at (123) 456-7890.";
let pattern = /\(\d{3}\) \d{3}-\d{4}/;
let matches = text.match(pattern);
console.log(matches); // ["(123) 456-7890"]
```

**Problem 2: Write a regex to match HTML tags that may or may not have attributes (e.g., <p>, <div class="example">, <br />).**

Regex pattern: `/<[^>]+>/g`

- `<[^>]+>` => Opening angle bracket se start hone wale characters jo closing angle bracket tak jaaye.

Example:

```javascript
let text = '<p>Hello</p> <div class="example">World</div>';
let pattern = /<[^>]+>/g;
let matches = text.match(pattern);
console.log(matches); // ["<p>", "</p>", "<div class="example">", "</div>"]
```

### 4. Anchors and Boundaries

**Problem 1: Create a regex to match lines in a multi-line string that start with "Error:".**

Regex pattern: `/^Error:.+/gm`

- `^Error:` => Line start hone wali "Error:" ke saath.
- `.+` => Line mein koi bhi character jo "Error:" ke baad aaye.
- `m` => Multi-line mode flag.

Example:

```javascript
let text =
  "Error: Something went wrong\nSuccess: All good\nError: Another issue";
let pattern = /^Error:.+/gm;
let matches = text.match(pattern);
console.log(matches); // ["Error: Something went wrong", "Error: Another issue"]
```

**Problem 2: Write a regex to match whole words that end with "ing".**

Regex pattern: `/\b\w+ing\b/g`

- `\b\w+ing\b` => Words jo "ing" par khatam hote hain.

Example:

```javascript
let text = "I am singing while working on something interesting.";
let pattern = /\b\w+ing\b/g;
let matches = text.match(pattern);
console.log(matches); // ["singing", "working", "something"]
```

### 5. Groups and Capturing

**Problem 1: Create a regex to extract the protocol, domain, and path from a URL (e.g., "https://www.example.com/path/to/page").**

Regex pattern: `/^(https?):\/\/([^\/]+)(\/.*)?$/`

- `(https?)` => Capturing group for protocol (http or https).
- `\/\/` => Escaped slashes.
- `([^\/]+)` => Capturing group for domain.
- `(\/.*)?` => Optional capturing group for path.

Example:

```javascript
let url = "https://www.example.com/path/to/page";
let pattern = /^(https?):\/\/([^\/]+)(\/.*)?$/;
let matches = url.match(pattern);
console.log(matches); // ["https://www.example.com/path/to/page", "https", "www.example.com", "/path/to/page"]
```

**Problem 2: Write a regex to match and capture repeated words in a sentence (e.g., "The the quick brown fox").**

Regex pattern: `/\b(\w+)\s+\1\b/g`

- `(\w+)` => Capturing group for a word.
- `\s+` => One or more whitespace characters.
- `\1` => Backreference to the first capturing group.

Example:

```javascript
let text = "The the quick brown fox.";
let pattern = /\b(\w+)\s+\1\b/g;
let matches = text.match(pattern);
console.log(matches); // ["The the"]
```

### 6. Lookahead and Lookbehind

**Problem 1: Create a regex to match passwords that are at least 8 characters long and contain at least one uppercase letter, one lowercase letter, and one digit.**

Regex pattern: `^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$`

- `(?=.*[a-z])` => Lookahead for at least one lowercase letter.
- `(?=.*[A-Z])` => Lookahead for at least one uppercase letter.
- `(?=.*\d)` => Lookahead for at least one digit.
- `[A-Za-z\d]{8,}` => At least 8 characters long, consisting of letters and digits.

Example:

```javascript
let password = "Password123";
let pattern = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[A-Za-z\d]{8,}$/;
console.log(pattern.test(password)); // true
```

**Problem 2: Write a regex to match all numbers in a string that are not preceded by a dollar sign ($).**

Regex pattern: `(?<!\$)\b\d+\b`

- `(?<!\$)` => Negative lookbehind for dollar sign.
- `\b\d+\b` => Whole numbers.

Example:

```javascript
let text = "$100 and 200 dollars";
let pattern = /(?<!\$)\b\d+\b/g;
let matches = text.match(pattern);
console.log(matches); // ["200"]
```

### 7. Alternation

**Problem 1: Create a regex to match either "color" or "colour" in a given text.**

Regex pattern: `/colou?r/g`

- `u?` => Optional "u".

Example:

```javascript
let text = "color and colour are the same.";
let pattern = /colou?r/g;
let matches = text.match(pattern);
console.log(matches); // ["color", "colour"]
```

**Problem 2: Write a regex to match dates in either MM/DD/YYYY or DD-MM-YYYY format.**

Regex pattern: `/\b(\d{2}[\/-]\d{2}[\/-]\d{4})\b/g`

- `\d{2}[\/-]\d{2}[\/-]\d{4}` => Two digits, followed by "/" or "-", followed by two digits, followed by "/" or "-", followed by four digits.

Example:

```javascript
let text = "Dates: 12/25/2020 and 25-12-2020.";
let pattern = /\b(\d{2}[\/-]\d{2}[\/-]\d{4

})\b/g;
let matches = text.match(pattern);
console.log(matches); // ["12/25/2020", "25-12-2020"]
```

### 8. Escaping Special Characters

**Problem 1: Create a regex to match literal asterisks (\*) in a string, ignoring their special meaning in regex.**

Regex pattern: `/\*/g`

- `\*` => Escaped asterisk.

Example:

```javascript
let text = "Use * for multiplication.";
let pattern = /\*/g;
let matches = text.match(pattern);
console.log(matches); // ["*"]
```

**Problem 2: Write a regex to match email addresses, properly escaping special characters like dots and at-signs.**

Regex pattern: `/[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}/`

- `[a-zA-Z0-9._%+-]+` => User name.
- `@` => At-sign.
- `[a-zA-Z0-9.-]+` => Domain name.
- `\.[a-zA-Z]{2,4}` => Top-level domain.

Example:

```javascript
let text = "Contact me at example.email@example.com.";
let pattern = /[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}/;
let matches = text.match(pattern);
console.log(matches); // ["example.email@example.com"]
```

Yeh thoda lamba ho gaya, lekin regex samajhne ke baad tum kisi bhi text ko easily process kar sakte ho. Happy coding!
