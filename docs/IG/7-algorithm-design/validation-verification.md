# ✅ Validation and Verification

Validation ensures data is reasonable and complete. Verification checks data accuracy. Both are crucial for reliable program operation.

---

## 🔍 Validation Checks

Ensure input data meets requirements:

- **Range Check**: Value within acceptable limits
  - Example: Age between 0-120
- **Length Check**: Data correct length
  - Example: Phone number has 10 digits
- **Type Check**: Data correct type
  - Example: Number field contains digits only
- **Presence Check**: Required data provided
  - Example: Name field not empty
- **Format Check**: Data follows correct pattern
  - Example: Email contains @ symbol

---

## 🔎 Verification Checks

Confirm data accuracy:

- **Visual Check**: Manual review of data
- **Double Entry Check**: Enter data twice, compare
- **Check Digit**: Mathematical validation
  - Example: ISBN, credit card numbers

---

## 📋 Check Digit Example

ISBN-10 validation uses check digit:

- Multiply each digit by position (10 to 1)
- Sum the products
- Result should be divisible by 11

---

## 🎯 When to Use

- **Validation**: Automatic checks during input
- **Verification**: Manual checks after input
- **Both**: Ensure data quality and accuracy

---

## 🚨 Error Handling

Handle invalid data appropriately:

- **Prompt for correction**: Ask user to re-enter
- **Use defaults**: Substitute valid values
- **Reject input**: Prevent invalid data entry
- **Log errors**: Record issues for review

---

## 📝 **Key Points:**

- Validation checks data reasonableness ✅
- Verification confirms data accuracy ✅
- Range, length, type, presence, format checks ✅
- Visual and double entry verification methods ✅
- Check digit for mathematical validation ✅
