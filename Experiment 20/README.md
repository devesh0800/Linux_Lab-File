# Shell Script to Find GCD, LCM, and Check Whether a Given Number is Prime

## Introduction

Mathematical computations such as finding the Greatest Common Divisor (GCD), Least Common Multiple (LCM), and checking whether a number is prime are fundamental problems in programming and algorithm design. Automating these computations using shell scripting helps students understand arithmetic operations, conditional logic, and iterative constructs in Bash.

The problem is to write a shell script that accepts user input to compute the GCD and LCM of two numbers and checks whether a given number is prime, demonstrating arithmetic operations, loops, and decision-making in Bash scripting.

---

## Course Outcome Mapping

| CO | Description |
|----|-------------|
| CO2 | Ability to write Bash scripts to perform computational tasks |
| CO4 | Application of conditional statements and looping constructs in scripting |

---

## Learning Outcomes

| LO | Description |
|----|-------------|
| LO1 | Accept numerical input from the user in a shell script |
| LO2 | Compute the GCD of two numbers using an iterative method |
| LO3 | Compute the LCM using the relationship between GCD and LCM |
| LO4 | Determine whether a given number is prime using loop-based logic |

---

## Theory

### Greatest Common Divisor (GCD)

The GCD of two integers is the largest positive integer that divides both numbers without leaving a remainder.

### Least Common Multiple (LCM)

The LCM of two integers is the smallest positive integer that is divisible by both numbers.

It can be calculated using:
```
LCM(a, b) = (a × b) / GCD(a, b)
```

### Prime Number

A prime number is a natural number greater than 1 that has exactly two distinct divisors: 1 and itself.

### Commands Used

| Command | Description |
|---------|-------------|
| read | Accept user input |
| while | Loop for GCD calculation |
| for | Loop for prime checking |
| $(( )) | Arithmetic operations |
| if | Conditional statements |
| echo | Display output |

---

## Procedure

### A. Writing the Shell Script

1. Open the terminal.
2. Create a script file:
   ```
   nano math_ops.sh
   ```
3. Enter the following script:
   ```bash
   #!/bin/bash
   echo "Enter first number:"
   read a
   echo "Enter second number:"
   read b
   x=$a
   y=$b

   # GCD calculation
   while [ $y -ne 0 ]
   do
     temp=$y
     y=$((x % y))
     x=$temp
   done
   gcd=$x
   lcm=$(( (a * b) / gcd ))

   echo "GCD of $a and $b is: $gcd"
   echo "LCM of $a and $b is: $lcm"

   echo "Enter a number to check for prime:"
   read n
   flag=0
   if [ $n -le 1 ]; then
     flag=1
   fi
   for ((i=2; i<=n/2; i++))
   do
     if [ $((n % i)) -eq 0 ]; then
       flag=1
       break
     fi
   done
   if [ $flag -eq 0 ]; then
     echo "$n is a Prime Number"
   else
     echo "$n is NOT a Prime Number"
   fi
   ```
4. Save and exit the editor.
5. Make the script executable:
   ```
   chmod +x math_ops.sh
   ```

### B. Executing the Script

6. Run the script:
   ```
   ./math_ops.sh
   ```

---

## Sample Execution

```bash
$ ./math_ops.sh
Enter first number:
12
Enter second number:
18
GCD of 12 and 18 is: 6
LCM of 12 and 18 is: 36
Enter a number to check for prime:
13
13 is a Prime Number
```

---

## Expected Output

- [x] Correct GCD and LCM values displayed.
- [x] Accurate identification of prime or non-prime number.
- [x] Script executes without errors.

---

## Result

A shell script was successfully written and executed to compute the GCD and LCM of two numbers and to check whether a given number is prime, demonstrating arithmetic operations, conditional logic, and loops in Bash scripting.

---

## Guidelines to Students

- Ensure valid integer input is provided.
- Understand the logic behind GCD and LCM calculations.
- Test the script with different input values.
- Avoid division by zero by validating inputs.

---

## Viva Questions

- What is GCD and why is it important?
  - **Answer:** GCD (Greatest Common Divisor) is the largest positive integer that divides both numbers without a remainder. It is important in simplifying fractions, cryptography, encryption algorithms, and finding common denominators in mathematical operations.

- How is LCM related to GCD?
  - **Answer:** LCM and GCD are related by the formula: `LCM(a, b) = (a × b) / GCD(a, b)`. Once GCD is known, LCM can be easily calculated using this relationship.

- Explain the algorithm used for GCD calculation.
  - **Answer:** The script uses the Euclidean algorithm. It repeatedly divides the larger number by the smaller number and stores the remainder until the remainder becomes 0. The last non-zero remainder is the GCD.

- What is a prime number?
  - **Answer:** A prime number is a natural number greater than 1 that has exactly two distinct positive divisors: 1 and itself. Examples include 2, 3, 5, 7, 11, 13, etc.

- Why do we check divisibility only up to n/2?
  - **Answer:** We check divisibility up to n/2 because no divisor of a number can be greater than half of that number (except the number itself). If no divisor is found by n/2, the number is prime.

- How can this script be optimized further?
  - **Answer:** For prime checking, optimization can be done by checking only up to the square root of n (`sqrt(n)`) instead of n/2, as any factor larger than the square root would have a corresponding smaller factor. Also, we can skip even numbers after checking 2.

- What happens if input values are zero?
  - **Answer:** If one input is 0, the GCD will be the other number (since any number divides 0), but the LCM formula `(a * b) / GCD` would result in division by zero if both are 0. The script should validate inputs to avoid this error.

---

## References

- Linux Man Pages: `man bash`, `man test`
- Introduction to Linux with Bash Scripting Lab (Dr. Rajesh Kumar)
