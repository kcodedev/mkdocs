# Boolean Algebra

This document covers the fundamentals of Boolean algebra, including its basic operations, De Morgan's laws, and applications in simplifying logic circuits and expressions.

## Understanding Boolean Algebra

Boolean algebra is a mathematical system developed by George Boole that deals with binary variables and logical operations. It forms the foundation of digital logic design and computer science.

### Basic Concepts

- **Variables**: Represented by letters (A, B, C, etc.) have values of 0 or 1
- **Constants**: 0 (False) and 1 (True)
- **Operations**: AND (∧), OR (∨), NOT (¬)

### Truth Values

| A | B | A ∧ B | A ∨ B | ¬A |
|---|---|-------|-------|----|
| 0 | 0 | 0     | 0     | 1  |
| 0 | 1 | 0     | 1     | 1  |
| 1 | 0 | 0     | 1     | 0  |
| 1 | 1 | 1     | 1     | 0  |

## Basic Laws and Theorems

### Commutative Laws
- A ∧ B = B ∧ A
- A ∨ B = B ∨ A

### Associative Laws
- (A ∧ B) ∧ C = A ∧ (B ∧ C)
- (A ∨ B) ∨ C = A ∨ (B ∨ C)

### Distributive Laws
- A ∧ (B ∨ C) = (A ∧ B) ∨ (A ∧ C)
- A ∨ (B ∧ C) = (A ∨ B) ∧ (A ∨ C)

### Identity Laws
- A ∧ 1 = A
- A ∨ 0 = A

### Null Laws
- A ∧ 0 = 0
- A ∨ 1 = 1

### Idempotent Laws
- A ∧ A = A
- A ∨ A = A

### Complement Laws
- A ∧ ¬A = 0
- A ∨ ¬A = 1
- ¬(¬A) = A

### Absorption Laws
- A ∧ (A ∨ B) = A
- A ∨ (A ∧ B) = A

## De Morgan's Laws

De Morgan's laws are fundamental theorems in Boolean algebra that relate the AND and OR operations through negation.

### First Law: ¬(A ∧ B) = ¬A ∨ ¬B
"The complement of the intersection is the union of the complements"

**Proof:**

| A | B | A ∧ B | ¬(A ∧ B) | ¬A | ¬B | ¬A ∨ ¬B |
|---|---|-------|-----------|----|----|----------|
| 0 | 0 | 0     | 1         | 1  | 1  | 1        |
| 0 | 1 | 0     | 1         | 1  | 0  | 1        |
| 1 | 0 | 0     | 1         | 0  | 1  | 1        |
| 1 | 1 | 1     | 0         | 0  | 0  | 0        |

### Second Law: ¬(A ∨ B) = ¬A ∧ ¬B
"The complement of the union is the intersection of the complements"

**Proof:**

| A | B | A ∨ B | ¬(A ∨ B) | ¬A | ¬B | ¬A ∧ ¬B |
|---|---|-------|-----------|----|----|----------|
| 0 | 0 | 0     | 1         | 1  | 1  | 1        |
| 0 | 1 | 1     | 0         | 1  | 0  | 0        |
| 1 | 0 | 1     | 0         | 0  | 1  | 0        |
| 1 | 1 | 1     | 0         | 0  | 0  | 0        |

## Performing Boolean Algebra Using De Morgan's Laws

### Example 1: Simplify ¬(A ∧ B ∧ C)

Using De Morgan's first law:
¬(A ∧ B ∧ C) = ¬A ∨ ¬B ∨ ¬C

### Example 2: Simplify ¬(A ∨ B ∨ C)

Using De Morgan's second law:
¬(A ∨ B ∨ C) = ¬A ∧ ¬B ∧ ¬C

### Example 3: Complex Expression
Simplify: ¬(A ∧ (B ∨ C))

First, apply De Morgan's second law to the inner expression:
¬(A ∧ (B ∨ C)) = ¬A ∨ ¬(B ∨ C)

Then apply De Morgan's first law:
¬A ∨ (¬B ∧ ¬C)

Using distributive law:
(¬A ∨ ¬B) ∧ (¬A ∨ ¬C)

## Simplifying Logic Circuits Using Boolean Algebra

### Example 1: Basic Circuit Simplification

**Original Expression:** A ∧ (A ∨ B)

**Simplification:**
A ∧ (A ∨ B) = A (absorption law)

**Circuit Reduction:**
```
Original:     Simplified:
   ┌───┐           ┌───┐
   │ A ├───┐       │ A │
   └───┘   │       └───┘
           ├─── AND
   ┌───┐   │
   │ B │   │
   └───┘ ──┘
```

### Example 2: Using De Morgan's Laws

**Original Expression:** ¬(A ∧ B) ∨ ¬(C ∧ D)

**Simplification:**
¬(A ∧ B) ∨ ¬(C ∧ D) = (¬A ∨ ¬B) ∨ (¬C ∨ ¬D) (De Morgan's first law)

**Further simplification:**
¬A ∨ ¬B ∨ ¬C ∨ ¬D

### Example 3: Complex Circuit Simplification

**Original Expression:** (A ∧ B) ∨ (A ∧ ¬B) ∨ (¬A ∧ B)

**Simplification:**
(A ∧ B) ∨ (A ∧ ¬B) ∨ (¬A ∧ B) = A ∧ B ∨ A ∧ ¬B ∨ ¬A ∧ B

Factor out common terms:
= (B ∨ ¬B) ∧ A ∨ B ∧ ¬A

= 1 ∧ A ∨ B ∧ ¬A

= A ∨ (B ∧ ¬A)

This represents an XOR gate: A ⊕ B

## Applications in Digital Design

**Circuit Optimization**

- Reduce number of gates
- Minimize propagation delay
- Lower power consumption
