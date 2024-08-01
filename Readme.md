### Regular Expressions Basics

**1. Regular Expressions (Regex):**

- Regex ek pattern hota hai jo text search karne ya match karne ke kaam aata hai.

**2. Commonly Used Symbols:**

- `^` : Start of string
- `$` : End of string
- `.` : Any character except newline
- `*` : 0 or more times
- `+` : 1 or more times
- `?` : 0 or 1 time
- `\d` : Any digit (0-9)
- `\w` : Any word character (a-z, A-Z, 0-9, \_)
- `\s` : Any whitespace character
- `[]` : Any one of the characters inside
- `()` : Grouping
- `|` : Or operator

### Capture Groups

**1. Capture Groups:**

- Parentheses `()` use karte hain capture groups banane ke liye. Ye matched text ko capture karte hain.
- Example: `(abc)` match karega aur capture karega `abc`.

**2. Usage:**

- `/(ab)c/` isme `(ab)` group banayega aur `c` match karega.

### Positive Lookaheads

**1. Positive Lookahead:**

- `(?=...)` use karte hain positive lookahead ke liye. Ye ensure karta hai ki specified pattern match hona chahiye bina usko consume kiye.
- Example: `a(?=b)` match karega `a` ko agar uske baad `b` hai.

### Negative Lookaheads

**1. Negative Lookahead:**

- `(?!...)` use karte hain negative lookahead ke liye. Ye ensure karta hai ki specified pattern match nahi hona chahiye bina usko consume kiye.
- Example: `a(?!b)` match karega `a` ko agar uske baad `b` nahi hai.

### Spam Detection Project Notes

**1. DOM Elements:**

- HTML elements ko JavaScript me access karne ke liye `getElementById` use kiya.
- Example:
  ```javascript
  const messageInput = document.getElementById("message-input");
  ```

**2. Spam Patterns:**

- Spam detect karne ke liye different regex patterns banaye.
- Example:
  ```javascript
  const helpRegex = /please help|assist me/i;
  ```

**3. Deny List:**

- Sab regex patterns ko ek array me dala.
- Example:
  ```javascript
  const denyList = [helpRegex, dollarRegex, freeRegex, stockRegex, dearRegex];
  ```

**4. Check Function:**

- `some` method use kiya array ke elements pe regex test karne ke liye.
- Example:
  ```javascript
  const isSpam = (msg) => denyList.some((regex) => regex.test(msg));
  ```

**5. Event Listener:**

- Button click pe event listener add kiya jo message ko check karta hai aur result display karta hai.
- Example:
  ```javascript
  checkMessageButton.addEventListener("click", () => {
    if (messageInput.value === "") {
      alert("Please enter a message.");
      return;
    }
    result.textContent = isSpam(messageInput.value)
      ? "Oh no! This looks like a spam message."
      : "This message does not seem to contain any spam.";
    messageInput.value = "";
  });
  ```

### Practice & Spaced Repetition Tips

1. **Short Sessions:**

   - 20-30 minutes ke short sessions me study karo.

2. **Regular Intervals:**

   - Regular intervals pe revise karo jaise 1 day, 3 days, 1 week, etc.

3. **Active Recall:**

   - Apne aapko questions puchho aur answers likhne ki koshish karo.

4. **Mix Topics:**

   - Different topics ko mix karke revise karo taaki better retention ho.

5. **Use Notes:**
   - Ye notes bar-bar dekhne se cheezein yaad rehengi.

Ye notes aapko spaced repetition technique se revise karne me help karenge. Happy studying!
