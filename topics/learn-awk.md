Aho, Weonbeger and Kernigha

Sun Jun  7 03:07:53 PM HKT 2026
# **AWK Tutorial: A Comprehensive Guide**

AWK (Aho, Weinberger, and Kernighan) is a powerful text processing tool in Unix/Linux environments. It excels at
manipulating structured data like CSV files, log files, and more. Here's a structured guide to get you started.

---

## **1. Basic Syntax**
AWK^[[1;3C processes text line by line, applying rules (patterns and actions). The general syntax is:

```sh
pattern { action }
```

- **Pattern**: A condition (e.g., a regular expression or logical expression).
- **Action**: Commands to execute if the pattern matches.

### **Examples**
- **Print all lines**:
  ```sh
  awk '{ print }' file.txt
  ```
- **Print specific lines** (e.g., lines containing "error"):
  ```sh
  awk '/error/ { print }' file.txt
  ```

---

## **2. Patterns and Actions**
### **Default Action**
If no action is specified, AWK prints the line:
```sh
awk '/pattern/' file.txt
```

### **Conditional Actions**
Use `if` or logical operators (`&&`, `||`, `!`) in patterns:
```sh
awk '/error && !/critical/' file.txt  # Lines with "error" but not "critical"
```

---

## **3. Variables and Built-In Variables**
### **Field Variables**
- `$1`, `$2`, etc.: Refer to fields separated by `FS` (default: whitespace).
- `NF`: Number of fields in the current line.
- `NR`: Number of records (lines) processed so far.
- `FS`: Field separator (default: whitespace).

### **Example: Print First Field**
```sh
awk '{ print $1 }' file.txt
```

### **Changing Field Separator**
Use `-F` to set a custom separator:
```sh
awk -F',' '{ print $1 }' data.csv  # Comma-separated values
```

---

## **4. Built-In Variables**
| Variable | Description |
|---------|-------------|
| `NR`    | Line number (starting at 1) |
| `NF`    | Number of fields in the current line |
| `FS`    | Field separator (default: whitespace) |
| `OFS`   | Output field separator (default: whitespace) |
| `ORS`   | Output record separator (default: newline) |

### **Example: Set Output Field Separator**
```sh
awk -F',' 'BEGIN { OFS=":" } { print $1, $2 }' data.csv
```

---

## **5. Common Tasks**
### **a. Extract Specific Fields**
```sh
awk '{ print $2, $4 }' file.txt  # Print 2nd and 4th fields
```

### **b. Filter Lines**
```sh
awk '/pattern/ { print }' file.txt  # Lines matching "pattern"
```

### **c. Count Lines/Fields**
```sh
awk '{ count++ } END { print "Total lines:", count }' file.txt
```

### **d. Sum Values**
```sh
awk '{ total += $3 } END { print "Total:", total }' data.csv
```

### **e. Process Multiple Files**
```sh
awk '{ print FILENAME, $1 }' file1.txt file2.txt
```

---

## **6. Advanced Topics**
### **a. Arrays**
Store and manipulate data:
```sh
awk '{ names[NR] = $1 } END { for (i in names) print names[i] }' file.txt
```

### **b. Loops and Conditions**
```sh
awk '{ for (i=1; i<=NF; i++) print $i }' file.txt  # Print all fields
```

### **c. Functions**
Define custom functions:
```sh
awk 'function square(x) { return x*x } { print square($1) }' numbers.txt
```

### **d. Regular Expressions**
Use regex in patterns:
```sh
awk '/^[A-Z]/ { print }' file.txt  # Lines starting with uppercase
```

---

## **7. Using AWK in Scripts**
### **Script File**
Save as `process.awk`:
```awk
# Print lines with "error"
/err/ { print }
```
Run with:
```sh
awk -f process.awk file.txt
```

### **Passing Variables**
Use `-v` to pass variables:
```sh
awk -v threshold=100 '{ if ($1 > threshold) print "High value" }' data.txt
```

---

## **8. Real-World Use Cases**
- **Log Analysis**: Extract timestamps, IP addresses, or error codes.
- **Data Transformation**: Convert CSV to TSV, filter rows, or calculate totals.
- **Automation**: Integrate with shell scripts for batch processing.

---

## **9. Tips and Tricks**
- **Quoting**: Use double quotes for patterns with shell variables.
- **Escaping**: Escape special characters (e.g., `$`, `*`) in shell commands.
- **Performance**: Avoid unnecessary operations in large files.

---

## **10. Conclusion**
AWK is a versatile tool for text processing. Start with simple examples, then explore advanced
features like arrays and regex. Practice with real data to master its power!

**Next Steps**:
- Try processing a CSV file.
- Experiment with `BEGIN` and `END` blocks.
- Combine AWK with `grep`, `sed`, or `sort` for complex tasks.
