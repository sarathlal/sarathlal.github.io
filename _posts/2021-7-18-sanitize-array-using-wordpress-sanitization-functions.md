---
title: Sanitize array using WordPress sanitization functions
layout: post
tags:
  - WordPress
---

When working with arrays in WordPress, sanitizing data is a critical step to ensure security and data integrity. Arrays often hold large volumes of structured data—from user input to API responses. Proper sanitization prevents vulnerabilities such as Cross-Site Scripting (XSS) and ensures consistent application behavior.

This guide focuses on sanitizing arrays, whether single-dimensional or multi-dimensional, using WordPress functions. We'll tackle common challenges and leverage tools like `array_map` and `map_deep` to simplify the process.

---

### **Why Sanitizing Arrays is Critical in WordPress**

Arrays are frequently used in WordPress development for:

- Storing user input from forms.
- Handling structured data from APIs or custom queries.
- Managing bulk options or metadata stored in the database.

Without proper sanitization, arrays can:

- Introduce security vulnerabilities (e.g., XSS attacks).
- Corrupt data when unexpected inputs are processed.
- Cause errors or unpredictable behavior in applications.

---

### **Challenges of Sanitizing Arrays**

**1. Single-Dimensional Arrays:**
Sanitizing each key-value pair manually can be tedious and error-prone.

**2. Multi-Dimensional Arrays:**
For nested arrays, a recursive approach is required to sanitize every element, regardless of depth.

---

### **Handling Single-Dimensional Arrays**

To sanitize a flat array, the `array_map()` function is a simple and efficient solution. Here’s an example:

```php
$array = [
    'name' => 'John <script>alert("hack");</script>',
    'email' => 'john.doe@example.com',
];

$sanitized_array = array_map('sanitize_text_field', $array);

print_r($sanitized_array);
```

**Explanation:**

- `sanitize_text_field`: Strips unwanted tags or scripts from text inputs.
- `array_map`: Applies this sanitization function to each element in the array.

**Result:**
The sanitized array ensures all input is safe for further processing or storage.

---

### **Handling Separate Sanitization for Keys and Values**

In some cases, you may need to sanitize the keys and values of an array using different sanitization functions. For example:

```php
$array = [
    'key_1' => 'array element 1',
    'key_2' => 'array element 2',
];

$keys = array_keys($array);
$keys = array_map('sanitize_key', $keys);

$values = array_values($array);
$values = array_map('sanitize_text_field', $values);

$array = array_combine($keys, $values);

print_r($array);
```

**Explanation:**

- `sanitize_key`: Ensures the array keys are valid and safe.
- `sanitize_text_field`: Sanitizes the array values as text.
- `array_combine`: Combines the sanitized keys and values back into a single array.

This approach is useful when working with associative arrays that require strict sanitization of both keys and values.

---

### **Handling Multi-Dimensional Arrays**

Nested arrays require a recursive approach for sanitization. Manually iterating through each level of nesting can be cumbersome. Instead, WordPress provides the `map_deep()` function.

#### Example: Using `map_deep()` to Sanitize a Nested Array

```php
$array = [
    'user' => [
        'name' => 'John <script>alert("hack");</script>',
        'email' => 'john.doe@example.com',
    ],
    'meta' => [
        'bio' => '<p>Some bio</p>',
        'website' => 'https://example.com',
    ],
];

$sanitized_array = map_deep( $array, 'sanitize_text_field' );

print_r($sanitized_array);
```

**Explanation:**

- `map_deep`: Recursively applies the `sanitize_text_field` function to all elements in the array, regardless of depth.

This method ensures that even deeply nested arrays are sanitized without extra effort.

---

### **Best Practices for Array Sanitization**

- **Use the Right Function:** Choose a WordPress sanitization function appropriate for the data type:
  - `sanitize_text_field` for general text.
  - `sanitize_email` for email addresses.
  - `esc_url_raw` for URLs.
  - `sanitize_key` for array keys.
- **Handle Nested Arrays Recursively:** Always use recursive methods like `map_deep()` for multi-dimensional arrays.
- **Validate Data Types:** Ensure sanitization is only applied to applicable data types (e.g., strings).
- **Test Thoroughly:** Verify that sanitized arrays behave as expected in all scenarios.

---

Sanitizing arrays in WordPress is essential for maintaining security and reliability. For single-dimensional arrays, `array_map` offers a quick and easy solution. For multi-dimensional arrays, `map_deep` simplifies the process by recursively applying sanitization functions. When dealing with associative arrays, you can sanitize keys and values separately for maximum control.

By adopting these techniques and best practices, you can ensure that your WordPress applications handle arrays securely and efficiently.


