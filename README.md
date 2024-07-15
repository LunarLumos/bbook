
### Bash Hello World

```bash
#!/bin/bash
echo "Hello, World!"
```
Output:
```
Hello, World!
```

### Variables

```bash
NAME="John"
AGE=30
echo "My name is $NAME and I am $AGE years old."
```
Output:
```
My name is John and I am 30 years old.
```

### Conditional Statements

```bash
NUM=10
if [ $NUM -eq 10 ]; then
  echo "Number is 10."
elif [ $NUM -gt 10 ]; then
  echo "Number is greater than 10."
else
  echo "Number is less than 10."
fi
```
Output:
```
Number is 10.
```

### Loops

#### For Loop

```bash
for i in {1..5}; do
  echo "Iteration $i"
done
```
Output:
```
Iteration 1
Iteration 2
Iteration 3
Iteration 4
Iteration 5
```

#### While Loop

```bash
COUNT=0
while [ $COUNT -lt 5 ]; do
  echo "Count: $COUNT"
  ((COUNT++))
done
```
Output:
```
Count: 0
Count: 1
Count: 2
Count: 3
Count: 4
```

### Functions

```bash
say_hello() {
  echo "Hello, $1!"
}

say_hello "Alice"
```
Output:
```
Hello, Alice!
```

### Arithmetic

```bash
NUM1=20
NUM2=5
echo "Addition: $((NUM1 + NUM2))"
echo "Subtraction: $((NUM1 - NUM2))"
echo "Multiplication: $((NUM1 * NUM2))"
echo "Division: $((NUM1 / NUM2))"
echo "Modulus: $((NUM1 % NUM2))"
```
Output:
```
Addition: 25
Subtraction: 15
Multiplication: 100
Division: 4
Modulus: 0
```

### Arrays

```bash
FRUITS=("Apple" "Banana" "Cherry")
echo "First fruit: ${FRUITS[0]}"
echo "All fruits: ${FRUITS[@]}"
```
Output:
```
First fruit: Apple
All fruits: Apple Banana Cherry
```

### Bash Arguments

```bash
echo "First argument: $1"
echo "Second argument: $2"
```
Output (assuming script is named `script.sh` and executed with arguments `arg1` and `arg2`):
```
First argument: arg1
Second argument: arg2
```

### Input

```bash
echo "Enter your name:"
read NAME
echo "Hello, $NAME!"
```
Output (assuming user inputs `Alice`):
```
Enter your name:
Alice
Hello, Alice!
```

### Concatenate Strings

```bash
STR1="Hello"
STR2="World"
echo "$STR1 $STR2"
```
Output:
```
Hello World
```

### Debugging

```bash
set -x  # Start debugging from here
NUM=15
if [ $NUM -lt 10 ]; then
  echo "Number is less than 10."
else
  echo "Number is greater than or equal to 10."
fi
set +x  # Stop debugging
```
Output:
```
+ NUM=15
+ '[' 15 -lt 10 ']'
+ echo 'Number is greater than or equal to 10.'
Number is greater than or equal to 10.
```

### Comments

```bash
# This is a comment
echo "This line is executed."
```
Output:
```
This line is executed.
```

### Read Files

```bash
while IFS= read -r line; do
  echo "Line: $line"
done < "file.txt"
```
Output (assuming `file.txt` contains lines `Line 1` and `Line 2`):
```
Line: Line 1
Line: Line 2
```

### Redirections

```bash
echo "Hello" > output.txt  # Redirect stdout to a file
cat < input.txt  # Redirect input from a file
```
Output:
```
(No output displayed for redirection examples)
```

### Switch-Case Statements

```bash
FRUIT="Apple"
case $FRUIT in
  "Apple")
    echo "Selected fruit is Apple."
    ;;
  "Banana")
    echo "Selected fruit is Banana."
    ;;
  "Cherry")
    echo "Selected fruit is Cherry."
    ;;
  *)
    echo "Unknown fruit."
    ;;
esac
```
Output:
```
Selected fruit is Apple.
```

This tutorial now includes a section on switch-case statements (`case`) in Bash, demonstrating how to use it with example code and showing the expected output or behavior.
