# 🔢 Logic Expressions: Boolean Algebra

Logic expressions represent digital logic using mathematical notation. They describe circuit behavior using Boolean algebra operators.

---

## 📝 Basic Operators

### AND Operation
- **Symbol**: • or ∧
- **Expression**: A • B or A ∧ B
- **Meaning**: A AND B
- **Precedence**: High (evaluated first)

### OR Operation
- **Symbol**: + or ∨
- **Expression**: A + B or A ∨ B
- **Meaning**: A OR B
- **Precedence**: Medium

### NOT Operation
- **Symbol**: ¬ or ¯
- **Expression**: ¬A or Ā
- **Meaning**: NOT A
- **Precedence**: Highest

---

## 🧮 Writing Expressions

### From Problem Statements
**Problem**: Light turns on if switch A OR switch B is pressed, AND power is on.

**Expression**: Light = (A + B) • Power

### From Truth Tables
**Truth Table**:
| A | B | Output |
|---|---|--------|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

**Expression**: Output = A + B

### From Circuit Diagrams
```
     A ──┐
         ├── OR ── Output
     B ──┘
```
**Expression**: Output = A + B

---

## 🔄 Expression Simplification

### Boolean Algebra Laws
- **Commutative**: A + B = B + A, A • B = B • A
- **Associative**: (A + B) + C = A + (B + C)
- **Distributive**: A • (B + C) = A • B + A • C
- **Absorption**: A + A • B = A, A • (A + B) = A

### De Morgan's Theorems
- ¬(A + B) = ¬A • ¬B
- ¬(A • B) = ¬A + ¬B

---

## 📊 Karnaugh Maps

Visual method for simplifying expressions:

**Example 2-variable K-map**:
```
     BC
    00 01 11 10
A 0| 0  1  1  0 |
  1| 0  1  1  0 |
```

**Simplified expression**: A + B

---

## 🎯 Expression Types

### Sum of Products (SOP)
- **Form**: A • B + A • C
- **OR of ANDs**: Each term is product
- **Implementation**: OR gate with AND gates

### Product of Sums (POS)
- **Form**: (A + B) • (A + C)
- **AND of ORs**: Each term is sum
- **Implementation**: AND gate with OR gates

---

## 🔧 Converting Between Forms

### SOP to POS
(A + B) • (A + C) = ¬(¬(A + B) + ¬(A + C))

### POS to SOP
¬(A • B) = ¬A + ¬B

### Using De Morgan's Laws
- Move negations through parentheses
- Change AND to OR and OR to AND
- Double negation elimination

---

## ✅ Verification

### Truth Table Method
1. **Create expression truth table**
2. **Compare with requirements**
3. **Verify all combinations match**

### Circuit Simulation
1. **Build circuit from expression**
2. **Test all input combinations**
3. **Confirm outputs match specification**

📝 **Key Points:**
- Logic expressions use Boolean algebra ✅
- AND (•), OR (+), NOT (¬) operators ✅
- Expressions derived from problems, tables, circuits ✅
- Boolean laws enable simplification ✅
- SOP and POS are standard forms ✅
- Verification ensures correctness ✅