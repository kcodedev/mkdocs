# ☢️ Nuclear Gandhi & Integer Underflow

![Nuclear Gandhi Meme](https://www.kxnet.com/wp-content/uploads/sites/16/2023/02/5f9.jpg?resize=640,400)

## 🕹 The Story
In the first **Civilization** game (1991), every leader had an **aggression rating** between **1** (very peaceful) and **12** (very aggressive).

- **Gandhi** started at aggression **1** 🕊️
- Switching to **Democracy** lowered aggression by **2** (more peaceful) 🗳️

### What Went Wrong?
Aggression was stored as an **unsigned 8-bit integer** (0–255).  
When Gandhi’s aggression dropped from `1` to `-1`, this caused an **integer underflow**.

```
1 - 2 = -1  ❌  (not possible for unsigned integers)
```

Instead of storing `-1`, the value **wrapped around**:

```
-1  →  255  (because 255 is the max value for an unsigned 8-bit integer)
```

### 🚀 The Result
- Gandhi instantly became the **most aggressive leader possible**.
- He started declaring war and building nukes 💥
- Players were confused (and amused) — hence the meme **"Nuclear Gandhi"**.

---

## 🧮 What is Integer Underflow?
Integer **underflow** happens when you subtract from the smallest possible value and go **below the range** the variable can store.

Example with unsigned 8-bit integers:

- Range: `0` to `255`
- `0 - 1` → wraps to `255`
- **Why?** Computers store numbers in binary. With unsigned integers, there’s no “negative” — so going below zero loops back to the top of the range.

---

## 📚 Fun Fact
Later *Civilization* games **deliberately coded** Gandhi to be nuke-happy as an Easter egg — even though the bug was fixed — keeping the legend alive.

```
Peaceful Gandhi? ✅
Peaceful Gandhi with nukes? ☢️✅✅
```
