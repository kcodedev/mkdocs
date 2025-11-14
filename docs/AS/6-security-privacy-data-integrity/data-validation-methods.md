# Data Validation Methods

Data validation methods check data at the point of entry or creation to ensure it meets predefined criteria. These methods prevent invalid or incorrect data from entering systems, maintaining data integrity from the start.

## Range Check

**Purpose**: Ensures numerical values fall within acceptable minimum and maximum limits.

**How it works**: Compares input value against predefined upper and lower bounds.

**Examples**:
- Age: Must be between 0 and 120
- Temperature: Must be between -50°C and 60°C
- Exam score: Must be between 0 and 100

**Implementation**:
```python
def validate_age(age):
    if 0 <= age <= 120:
        return True
    return False
```

## Format Check

**Purpose**: Ensures data follows a specific pattern or structure.

**How it works**: Uses regular expressions or pattern matching to verify format.

**Examples**:
- Email addresses: Must contain @ symbol and valid domain
- Phone numbers: Must follow country-specific format
- Dates: Must be in DD/MM/YYYY or MM/DD/YYYY format
- Postal codes: Must match country-specific patterns

**Implementation**:
```python
import re

def validate_email(email):
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return re.match(pattern, email) is not None
```

## Length Check

**Purpose**: Ensures text fields contain the correct number of characters.

**How it works**: Verifies that string length falls within specified minimum and maximum limits.

**Examples**:
- Username: Must be 3-20 characters long
- Password: Must be at least 8 characters long
- Credit card number: Must be exactly 16 digits
- National ID: Must be exactly 9 characters

**Implementation**:
```python
def validate_username(username):
    return 3 <= len(username) <= 20
```

## Presence Check

**Purpose**: Ensures required fields are not empty or null.

**How it works**: Checks that mandatory data fields contain values.

**Examples**:
- Name fields in registration forms
- Required address information
- Essential medical data in patient records
- Mandatory tax information

**Implementation**:
```python
def validate_required_field(field):
    return field is not None and str(field).strip() != ""
```

## Existence Check

**Purpose**: Verifies that referenced data exists in the system.

**How it works**: Checks against existing records or lookup tables.

**Examples**:
- Customer ID must exist in customer database
- Product code must be in inventory system
- Department code must match organizational structure
- Foreign key relationships in databases

**Implementation**:
```python
def validate_customer_id(customer_id, customer_database):
    return customer_id in customer_database
```

## Limit Check

**Purpose**: Ensures values do not exceed reasonable operational limits.

**How it works**: Compares against business rule limits rather than absolute ranges.

**Examples**:
- Daily transaction limit: Cannot exceed $10,000
- Inventory reorder point: Must be less than maximum stock level
- Loan amount: Cannot exceed 5 times annual salary
- Class enrollment: Cannot exceed room capacity

**Implementation**:
```python
def validate_transaction_limit(amount, daily_limit):
    return amount <= daily_limit
```

## Check Digit

**Purpose**: Detects errors in identification numbers using mathematical algorithms.

**How it works**: Calculates a check digit based on the other digits and compares with provided digit.

**Examples**:
- **ISBN**: International Standard Book Number
- **Credit Cards**: Uses Luhn algorithm (Mod 10)
- **UPC**: Universal Product Code
- **IBAN**: International Bank Account Number

**Implementation** (Luhn Algorithm for credit cards):
```python
def validate_credit_card(number):
    def luhn_checksum(card_num):
        def digits_of(n):
            return [int(d) for d in str(n)]
        digits = digits_of(card_num)
        odd_digits = digits[-1::-2]
        even_digits = digits[-2::-2]
        checksum = sum(odd_digits)
        for d in even_digits:
            checksum += sum(digits_of(d*2))
        return checksum % 10

    return luhn_checksum(number) == 0
```

## Type Check

**Purpose**: Ensures data is of the correct data type.

**How it works**: Verifies that input matches expected data types.

**Examples**:
- Age must be integer, not text
- Price must be decimal/float, not text
- Date must be date type, not string
- Boolean fields must be true/false

**Implementation**:
```python
def validate_integer(value):
    try:
        int(value)
        return True
    except ValueError:
        return False
```

## Cross-Field Validation

**Purpose**: Validates relationships between multiple fields.

**How it works**: Checks logical relationships between different data fields.

**Examples**:
- End date must be after start date
- Total must equal sum of parts
- Password confirmation must match password
- Shipping address required if delivery method selected

**Implementation**:
```python
def validate_date_range(start_date, end_date):
    return start_date <= end_date
```

## List Validation

**Purpose**: Ensures values are from an approved list of options.

**How it works**: Checks input against predefined acceptable values.

**Examples**:
- Country must be from approved country list
- Status must be "Active", "Inactive", or "Pending"
- Payment method must be from accepted payment types
- Job title must match organizational job codes

**Implementation**:
```python
def validate_country(country, valid_countries):
    return country in valid_countries
```

## Custom Validation Rules

**Purpose**: Implements business-specific validation logic.

**How it works**: Uses custom algorithms or rules specific to the application domain.

**Examples**:
- Complex business rules in financial systems
- Medical validation rules in healthcare systems
- Engineering constraints in design systems
- Legal compliance rules in regulatory systems

## Implementation Considerations

### User Interface Design
- Provide immediate feedback for validation failures
- Use clear, helpful error messages
- Guide users toward correct input formats

### Performance
- Balance thorough validation with system performance
- Consider client-side vs server-side validation
- Cache validation results when appropriate

### Maintenance
- Keep validation rules synchronized across systems
- Document validation logic for future maintenance
- Test validation rules thoroughly

### Security
- Validation should not be bypassed for security
- Prevent injection attacks through proper validation
- Validate all inputs, not just user interfaces

Data validation is crucial for maintaining data quality and preventing errors that could lead to incorrect business decisions or system failures.