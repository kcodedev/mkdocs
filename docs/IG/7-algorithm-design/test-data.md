# 🧪 Test Data Types

Testing requires different types of data to thoroughly validate algorithms. Use normal, abnormal, extreme, and boundary data for comprehensive testing.

---

## ✅ Normal Data

Typical, expected input values:

- **Definition**: Valid data within normal operating range
- **Purpose**: Verify algorithm works under standard conditions
- **Example**: Age = 25 (for age validation 0-120)

---

## ❌ Abnormal Data

Invalid data that should be rejected:

- **Definition**: Data that fails validation checks
- **Purpose**: Test error handling and rejection
- **Example**: Age = 150 (outside valid range)

---

## 🎯 Extreme Data

Largest/smallest acceptable values:

- **Definition**: Boundary values that are still valid
- **Purpose**: Test algorithm limits
- **Example**: Age = 120 (maximum valid age)

---

## 🔸 Boundary Data

Values at the edges of valid ranges:

- **Definition**: Largest/smallest valid + adjacent invalid values
- **Purpose**: Test edge cases thoroughly
- **Example**: Ages 0, 1, 119, 120, 121

---

## 📊 Test Data Examples

For age validation (0-120):

| Type | Values | Expected Result |
|------|--------|-----------------|
| Normal | 25, 45, 67 | Accept |
| Abnormal | -5, 150, "abc" | Reject |
| Extreme | 0, 120 | Accept |
| Boundary | -1, 0, 1, 119, 120, 121 | -1,121 reject; others accept |

---

## 🧪 Testing Strategy

1. **Normal data first**: Ensure basic functionality
2. **Boundary testing**: Check edge cases
3. **Extreme values**: Test limits
4. **Abnormal data**: Verify error handling
5. **Invalid types**: Test type checking

---

## 📈 Test Coverage

Good testing covers:

- All code paths
- All validation checks
- All error conditions
- All boundary conditions

---

## 📝 **Key Points:**
 
- Normal data tests typical operation ✅
- Abnormal data tests error handling ✅
- Extreme data tests algorithm limits ✅
- Boundary data tests edge cases ✅
- Comprehensive testing ensures reliability ✅
