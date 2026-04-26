# Understanding Virtual Terminals in Linux, Display Managers, X Clients, and Window Managers

## Introduction

In many real-world applications such as log analysis, report generation, and glossary processing, it is often required to access the last few entries of a file and display them in reverse order. Bash scripting provides support for arrays, which can be effectively used to store file content and manipulate it programmatically.

The problem is to write a shell script that reads the last few lines of a glossary file, stores them in an array, and prints them in reverse order, demonstrating the use of arrays and reverse traversal in Bash scripting.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts for automation and data manipulation |
| CO4 | Use of scripting logic, arrays, and control structures |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Read file content and store it in an array |
| LO2 | Access and manipulate array elements in Bash |
| LO3 | Print file content in reverse order using scripting logic |
| LO4 | Apply array-based scripting to real-world text processing tasks |

---

## Theory

### Arrays in Bash

An array in Bash can store multiple values indexed numerically. Arrays are useful when dealing with collections of data such as file lines.

Basic array syntax:
```bash
array[index]=value
```

Access all elements:
```bash
${array[@]}
```

### Reverse Order Processing

Reverse traversal involves accessing array elements from the last index to the first, which is useful for reversing file content or recent log entries.

### Commands Used

| Command | Description |
|---------|-------------|
| tail | Display last lines of a file |
| read | Read input line |
| array | Store data in indexed format |
| for loop | Iterate through array |
| echo | Display output |

---

## Procedure

### A. Creating a Glossary File

1. Open the terminal.
2. Create a glossary file:
   ```
   nano glossary.txt
   ```
3. Enter sample content:
   ```
   Linux: Open-source operating system
   Bash: Shell scripting language
   Kernel: Core of operating system
   File System: Structure for storing data
   Networking: Communication between systems
   ```
4. Save and exit the editor.

### B. Writing the Shell Script

5. Create a script file:
   ```
   nano reverse_glossary.sh
   ```
6. Enter the following script:
   ```bash
   #!/bin/bash
   declare -a lines
   index=0
   while read line
   do
     lines[$index]="$line"
     index=$((index + 1))
   done < <(tail -n 5 glossary.txt)
   echo "Glossary entries in reverse order:"
   for ((i=index-1; i>=0; i--))
   do
     echo "${lines[$i]}"
   done
   ```
7. Save and exit the editor.
8. Make the script executable:
   ```
   chmod +x reverse_glossary.sh
   ```

### C. Executing the Script

9. Run the script:
   ```
   ./reverse_glossary.sh
   ```

---

## Sample Execution

```bash
$ ./reverse_glossary.sh
Glossary entries in reverse order:
Networking: Communication between systems
File System: Structure for storing data
Kernel: Core of operating system
Bash: Shell scripting language
Linux: Open-source operating system
```

---

## Expected Output

- [x] Last glossary entries stored successfully in an array.
- [x] Entries displayed in reverse order.
- [x] Output formatted correctly.

---

## Result

A shell script was successfully written and executed to read the end of a glossary file, store entries in an array, and print them in reverse order using Bash scripting.

---

## Guidelines to Students

- Ensure the glossary file exists before running the script.
- Modify `tail -n` value to change number of entries.
- Use arrays carefully with proper indexing.
- Practice array traversal for better scripting skills.

---

## Viva Questions

- What is an array in Bash?
  - **Answer:** An array in Bash is a variable that can hold multiple values, indexed numerically starting from 0. It allows storing and manipulating collections of data like file lines, user lists, or any sequence of values in a single variable.

- How are array elements accessed?
  - **Answer:** Array elements are accessed using the syntax `${array[index]}` for a single element, or `${array[@]}` to access all elements. For example, `${lines[0]}` accesses the first element, and `${lines[@]}` expands to all elements.

- What does tail -n do?
  - **Answer:** The `tail` command displays the last part of a file. The `-n` option specifies the number of lines to display. For example, `tail -n 5 file.txt` displays the last 5 lines of the file.

- How is reverse traversal achieved in the script?
  - **Answer:** Reverse traversal is achieved using a C-style `for` loop: `for ((i=index-1; i>=0; i--))`. It starts from the last index and decrements until 0, printing each element in reverse order: `${lines[$i]}`.

- Why are arrays useful in shell scripting?
  - **Answer:** Arrays are useful for storing multiple related values, organizing data, and performing operations on collections. They enable complex data manipulation, sorting, searching, and efficient processing of file contents, user inputs, and system data.

- Can this script work without arrays? How?
  - **Answer:** Yes, the script can work without arrays using command substitution with `tac` (reverse cat). For example: `tail -n 5 glossary.txt | tac` would output the last 5 lines in reverse order directly, though using arrays demonstrates array manipulation skills.

- How can the script be modified to accept user input?
  - **Answer:** The script can accept the filename as a command-line argument (`$1`) and the number of lines as another argument (`$2`). For example: `filename=${1:-glossary.txt}` and `lines=${2:-5}`, then use `tail -n $lines "$filename"` to make it flexible.

---

## References

- Linux Man Pages: `man tail`, `man tac`, `man bash`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
