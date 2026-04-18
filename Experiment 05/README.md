# Searching for Files and Text Using grep and Related Tools

## Introduction

In Linux systems, large volumes of data are often stored in text files such as logs, configuration files, and scripts. Manually searching for specific information inside these files is inefficient and error-prone. Linux provides powerful text-searching utilities that enable users to quickly locate patterns, keywords, or strings within files and command outputs.

This experiment searches for specific patterns and text within files using Linux commands such as grep, fgrep, and related options, and understanding their importance in log analysis, troubleshooting, and automation tasks.

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Search for specific text patterns in files using grep |
| LO2 | Use different options of grep for case-insensitive and recursive searching |
| LO3 | Differentiate between grep, fgrep, and egrep |
| LO4 | Apply text searching in real-world scenarios such as log analysis |

---

## Theory

### Text Searching in Linux

Linux treats most data as plain text, making text-processing tools extremely powerful. Searching text efficiently is essential for:

- Log file analysis
- Configuration troubleshooting
- Security monitoring
- Automation scripts

### grep Command

The grep command searches for a pattern in files or input streams and prints matching lines.

**Basic syntax:**
```bash
grep [options] pattern filename
```

### Related Commands

| Command | Description |
|---------|-------------|
| `grep` | General pattern searching |
| `fgrep` | Fast grep (searches fixed strings, no regular expressions) |
| `egrep` | Extended grep (supports extended regular expressions) |

> **Note:** In modern Linux systems, egrep and fgrep are implemented using `grep -E` and `grep -F`.

---

## Commands Reference

| Command | Description |
|---------|-------------|
| `grep` | Search text using patterns |
| `grep -i` | Case-insensitive search |
| `grep -n` | Show line numbers |
| `grep -r` | Recursive search |
| `grep -v` | Invert match |
| `fgrep` | Search fixed strings |
| `cat` | Display file content |
| `ls` | List files |

---

## Procedure

### Step 1: Create Working Directory

```bash
mkdir grep_lab              # Create working directory
cd grep_lab                  # Change into directory
```

### Step 2: Create Sample Text File

```bash
nano sample.txt
```

**Add the following content:**
```
Linux is powerful
Linux is secure
Bash scripting is useful
Cyber Security uses Linux
```

**Save and exit:** Press `Ctrl + O`, then `Ctrl + X`

### Step 3: Display File Contents

```bash
cat sample.txt
```

### Step 4: Basic grep Search

```bash
grep "Linux" sample.txt
```

**Output:**
```
Linux is powerful
Linux is secure
Cyber Security uses Linux
```

### Step 5: Case-Insensitive Search

```bash
grep -i "linux" sample.txt
```

### Step 6: Display Line Numbers

```bash
grep -n "Linux" sample.txt
```

**Output:**
```
1:Linux is powerful
2:Linux is secure
4:Cyber Security uses Linux
```

### Step 7: Invert Match (Non-Matching Lines)

```bash
grep -v "Linux" sample.txt
```

**Output:**
```
Bash scripting is useful
```

### Step 8: Search Fixed Strings with fgrep

```bash
fgrep "Bash scripting" sample.txt
```

### Step 9: Recursive Search

```bash
# Create subdirectory with files
mkdir logs
echo "Linux server running" > logs/server.log
echo "Windows server running" > logs/windows.log

# Search recursively
grep -r "Linux" .
grep -r "Linux" logs/
```

### Step 10: Combine Options

```bash
grep -in "linux" sample.txt     # Case-insensitive with line numbers
grep -iv "linux" sample.txt     # Case-insensitive, inverted
grep -rn "Linux" .              # Recursive with line numbers
```

---

## Expected Output

- [x] Matching lines containing the search pattern are displayed
- [x] Line numbers are shown where applicable
- [x] Case-insensitive and inverted searches work correctly
- [x] Recursive search finds patterns in subdirectories

---

## Results

Text searching operations were successfully performed using grep and related commands. The student gained practical experience in locating specific patterns within files, which is essential for log analysis and automation tasks.

---

## Viva Questions

- What is the use of grep command?
- Difference between grep and fgrep.
- What does grep -v do?
- How do you perform case-insensitive search?
- What is recursive search?
- Where is grep commonly used in cyber security?
- Difference between grep and egrep.

**Answers:**

**What is the use of grep command?**
`grep` (Global Regular Expression Print) searches for specified patterns or text within files and displays matching lines. It is used to find specific information quickly in large text files.

**Difference between grep and fgrep:**
- `grep` interprets patterns as regular expressions
- `fgrep` (fixed grep) searches for literal strings only, without regex interpretation, making it faster for searching fixed strings

**What does grep -v do?**
`grep -v` inverts the match, displaying all lines that do NOT contain the specified pattern. It is useful for filtering out unwanted content.

**How do you perform case-insensitive search?**
Use the `-i` option: `grep -i "pattern" filename`

**What is recursive search?**
Recursive search (`grep -r`) searches through all files in a directory and its subdirectories. It is useful when searching for patterns across multiple files and folders.

**Where is grep commonly used in cyber security?**
- Log analysis and monitoring
- Searching authentication logs for suspicious activity
- Finding specific patterns in network traffic captures
- Scanning configuration files for security settings
- Malware analysis by searching strings in files

**Difference between grep and egrep:**
- `grep` supports basic regular expressions
- `egrep` (extended grep) supports extended regular expressions including `+`, `?`, `|`, and parentheses for grouping
- In modern systems, `egrep` is equivalent to `grep -E`

---

## Tips

- Use case-insensitive search when exact case is unknown
- Avoid recursive search on system directories without permission
- Practice pattern matching on different files
- Understand the difference between fixed-string and regex-based searching
- Use `grep -n` to quickly locate line numbers for editing
- Combine multiple options like `grep -rni` for powerful searches
- Use quotes around patterns with special characters

---

## References

- grep Manual: `man grep`
- Regular Expressions: https://www.gnu.org/software/grep/manual/html_node/Regular-Expressions.html
- Cyber Security Log Analysis: https://www.tecmint.com/grep-command-for-searching-in-linux/

