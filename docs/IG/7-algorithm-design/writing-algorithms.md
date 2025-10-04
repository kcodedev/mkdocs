# ✍️ Writing Algorithms

Algorithms are step-by-step procedures to solve problems. They can be written in pseudocode, flowcharts, or programming code.

---

## 🎯 Algorithm Characteristics

- **Clear steps**: Each step clearly defined
- **Finite**: Must eventually terminate
- **Unambiguous**: No confusion about what to do
- **Input/Output**: Defined data requirements

---

## 📝 Writing in Pseudocode

Use structured English-like statements:

- **Variables**: Declare and use clearly named variables
- **Sequence**: Steps execute in order
- **Selection**: IF-THEN-ELSE for decisions
- **Iteration**: Loops for repetition
- **Modularity**: Break into procedures/functions

---

## 📊 Example Algorithm

Calculate average of test scores:

```
DECLARE Total, Count, Average : REAL
DECLARE Scores : ARRAY[1:10] OF REAL

Total ← 0
Count ← 0

FOR Index ← 1 TO 10 DO
  INPUT Scores[Index]
  Total ← Total + Scores[Index]
  Count ← Count + 1
ENDFOR

IF Count > 0 THEN
  Average ← Total / Count
  OUTPUT "Average:", Average
ELSE
  OUTPUT "No scores entered"
ENDIF
```

---

## 🔄 Control Structures

- **Sequence**: Execute steps in order
- **Selection**: Choose between alternatives
- **Iteration**: Repeat steps until condition met

---

## 📋 Best Practices

- **Meaningful names**: Use descriptive variable names
- **Comments**: Explain complex logic
- **Indentation**: Show structure clearly
- **Modular**: Break into smaller sub-algorithms
- **Testable**: Design for easy testing

---

## 🎨 Algorithm Patterns

- **Linear**: Straight sequence of steps
- **Branching**: Decision points with alternatives
- **Looping**: Repetitive operations
- **Recursive**: Algorithm calls itself

---

## 📝 **Key Points:**

- Algorithms solve problems step-by-step ✅
- Use clear, unambiguous language ✅
- Include sequence, selection, iteration ✅
- Test with different scenarios ✅
- Document with comments and structure ✅
