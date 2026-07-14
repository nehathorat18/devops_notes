# Shell Scripting Cheat Sheet

---

# Basics
## 1. Shebang (`#!/bin/bash`)

Tells Linux to run the script using Bash.

```bash
#!/bin/bash
echo "Hello"
```

---

## 2. Running a Script

Make the script executable:

```bash
chmod +x script.sh
```

Run the script:

```bash
./script.sh
```
---

## 3. Comments

Used to explain the code.

```bash
# This is a comment

echo "Hello"   # Inline comment
```

---

## 4. Variables

Store values in a variable.

```bash
NAME="Neha"
echo $NAME
```

Double quotes expand variables:

```bash
echo "Hello $NAME"
```

Single quotes print as text:

```bash
echo '$NAME'
```

---

## 5. Reading User Input

```bash
read NAME
echo "Hello $NAME"
```

---

## 6. Command-Line Arguments

```bash
echo $0   # Script name
echo $1   # First argument
echo $2   # Second argument
echo $#   # Number of arguments
echo $@   # All arguments
echo $?   # Exit status of last command
```

Run:

```bash
./script.sh DevOps Linux
```

Output:

```text
DevOps
Linux
```

---
# Operators and Conditionals

## 1. String Comparisons

Compare text values.

```bash
[ "$A" = "$B" ]   # Equal
[ "$A" != "$B" ]  # Not equal
[ -z "$A" ]       # Empty string
[ -n "$A" ]       # Not empty
```

Example:

```bash
NAME="Neha"

if [ "$NAME" = "Neha" ]; then
    echo "Match"
fi
```

---

## 2. Integer Comparisons

Compare numbers.

```bash
[ $A -eq $B ]   # Equal
[ $A -ne $B ]   # Not equal
[ $A -lt $B ]   # Less than
[ $A -gt $B ]   # Greater than
[ $A -le $B ]   # Less than or equal
[ $A -ge $B ]   # Greater than or equal
```

Example:

```bash
AGE=20

if [ $AGE -ge 18 ]; then
    echo "Adult"
fi
```

---

## 3. File Test Operators

Check file or directory.

```bash
-f file.txt    # File exists
-d folder      # Directory exists
-e file.txt    # File/Folder exists
-r file.txt    # Read permission
-w file.txt    # Write permission
-x file.sh     # Execute permission
-s file.txt    # File is not empty
```

---

## 4. if, elif, else

```bash
if [ $AGE -ge 18 ]; then
    echo "Adult"
elif [ $AGE -ge 13 ]; then
    echo "Teen"
else
    echo "Child"
fi
```

---

## 5. Logical Operators

```bash
&&   # AND
||   # OR
!    # NOT
```

Example:

```bash
[ $AGE -ge 18 ] && echo "Adult"
```

---

## 6. Case Statement

Used to check multiple values.

```bash
read CHOICE

case $CHOICE in
    1) echo "Start";;
    2) echo "Stop";;
    *) echo "Invalid";;
esac
```

---

# Loops

## 1. `for` Loop

Used to repeat a task for a list of items.

### List-based

```bash
for i in 1 2 3
do
    echo $i
done
```

### C-style

```bash
for ((i=1; i<=3; i++))
do
    echo $i
done
```

---

## 2. `while` Loop

Runs while the condition is true.

```bash
i=1

while [ $i -le 3 ]
do
    echo $i
    ((i++))
done
```

---

## 3. `until` Loop

Runs until the condition becomes true.

```bash
i=1

until [ $i -gt 3 ]
do
    echo $i
    ((i++))
done
```

---

## 4. Loop Control

### `break` - Stop the loop

```bash
for i in 1 2 3 4
do
    [ $i -eq 3 ] && break
    echo $i
done
```

### `continue` - Skip one iteration

```bash
for i in 1 2 3 4
do
    [ $i -eq 3 ] && continue
    echo $i
done
```

---

## 5. Loop Over Files

```bash
for file in *.log
do
    echo $file
done
```

Lists all `.log` files.

---

## 6. Loop Over Command Output

```bash
cat names.txt | while read line
do
    echo $line
done
```

Reads one line at a time from the file.
---
# Functions

## 1. Defining a Function

A function is a block of code that performs a specific task.

```bash
greet() {
    echo "Hello!"
}
```

---

## 2. Calling a Function

Call the function using its name.

```bash
greet() {
    echo "Hello!"
}

greet
```

Output:

```text
Hello!
```

---

## 3. Passing Arguments to Functions

Use `$1`, `$2` inside the function.

```bash
greet() {
    echo "Hello $1"
}

greet Neha
```

Output:

```text
Hello Neha
```

---

## 4. Return Values

### `return`

Returns an exit status (0-255).

```bash
check() {
    return 0
}

check
echo $?
```

### `echo`

Returns a value.

```bash
greet() {
    echo "Hello"
}

msg=$(greet)
echo $msg
```

Output:

```text
Hello
```

---

## 5. Local Variables

`local` makes a variable available only inside the function.

```bash
greet() {
    local NAME="Neha"
    echo $NAME
}

greet
```

---

# Text Processing Commands

## 1. `grep`

Search for text in a file.

```bash
grep "error" log.txt      # Search text
grep -i "error" log.txt   # Ignore case
grep -r "error" .         # Search recursively
grep -c "error" log.txt   # Count matches
grep -n "error" log.txt   # Show line number
grep -v "error" log.txt   # Exclude matches
grep -E "error|fail" log.txt   # Multiple patterns
```

---

## 2. `awk`

Print specific columns.

```bash
awk '{print $1}' file.txt
awk -F: '{print $1}' /etc/passwd
```

---

## 3. `sed`

Edit text.

```bash
sed 's/old/new/' file.txt        # Replace first match
sed 's/old/new/g' file.txt       # Replace all matches
sed '/error/d' file.txt          # Delete matching lines
sed -i 's/foo/bar/g' file.txt    # Edit file directly
```

---

## 4. `cut`

Extract columns.

```bash
cut -d',' -f1 file.csv
```

---

## 5. `sort`

Sort data.

```bash
sort file.txt      # Alphabetical
sort -n file.txt   # Numerical
sort -r file.txt   # Reverse
sort -u file.txt   # Unique
```

---

## 6. `uniq`

Remove duplicate lines.

```bash
uniq file.txt
uniq -c file.txt
```

---

## 7. `tr`

Replace or delete characters.

```bash
echo "hello" | tr 'a-z' 'A-Z'
echo "hello123" | tr -d '0-9'
```

---

## 8. `wc`

Count lines, words, and characters.

```bash
wc file.txt
wc -l file.txt
wc -w file.txt
wc -c file.txt
```

---

## 9. `head` / `tail`

Show first or last lines.

```bash
head -5 file.txt
tail -5 file.txt
tail -f app.log
```

---

# Useful Patterns and One-Liners

## 1. Find and Delete Old Files

Delete files older than 7 days.

```bash
find . -type f -mtime +7 -delete
```

---

## 2. Count Lines in All `.log` Files

```bash
wc -l *.log
```

---

## 3. Replace Text in Multiple Files

Replace "old" with "new" in all `.txt` files.

```bash
sed -i 's/old/new/g' *.txt
```

---

## 4. Check if a Service is Running

```bash
systemctl status nginx
```

Or

```bash
ps -ef | grep nginx
```

---

## 5. Check Disk Usage

```bash
df -h
```

---

## 6. Read a CSV File

```bash
awk -F',' '{print $1,$2}' users.csv
```

---

## 7. Watch Errors in a Log File

```bash
tail -f app.log | grep "ERROR"
```

---

# Error Handling and Debugging

## 1. Exit Codes

`$?` shows the status of the last command.

- `0` = Success
- Non-zero = Error

```bash
ls

echo $?
```

Exit the script manually:

```bash
exit 0   # Success
exit 1   # Error
```

---

## 2. `set -e`

Exit the script if any command fails.

```bash
#!/bin/bash
set -e

mkdir test
cd test
```

---

## 3. `set -u`

Stop the script if an undefined variable is used.

```bash
#!/bin/bash
set -u

echo $NAME
```

---

## 4. `set -o pipefail`

Returns an error if any command in a pipeline fails.

```bash
set -o pipefail

cat file.txt | grep "error"
```

---

## 5. `set -x`

Shows each command before it runs (Debug Mode).

```bash
set -x

NAME="Neha"
echo $NAME
```

---

## 6. `trap`

Run a command before the script exits.

```bash
cleanup() {
    echo "Cleaning up..."
}

trap cleanup EXIT
```

---

### Bonus — Quick Reference Table


| Topic | Key Syntax | Example |
|--------|------------|---------|
| Shebang | `#!/bin/bash` | `#!/bin/bash` |
| Run Script | `chmod +x file.sh` | `./script.sh` |
| Comment | `#` | `# This is a comment` |
| Variable | `VAR="value"` | `NAME="DevOps"` |
| User Input | `read VAR` | `read NAME` |
| Argument | `$1`, `$2` | `./script.sh DevOps Linux` |
| Exit Status | `$?` | `echo $?` |
| If | `if [ condition ]; then` | `if [ -f file.txt ]; then` |
| Case | `case ... esac` | `case $choice in` |
| String Compare | `[ "$A" = "$B" ]` | `[ "$NAME" = "Neha" ]` |
| Integer Compare | `[ $A -eq $B ]` | `[ $AGE -ge 18 ]` |
| File Check | `-f`, `-d`, `-e` | `[ -f file.txt ]` |
| For Loop | `for i in list; do` | `for i in 1 2 3; do` |
| While Loop | `while [ condition ]` | `while [ $i -le 5 ]` |
| Until Loop | `until [ condition ]` | `until [ $i -gt 5 ]` |
| Function | `name() { ... }` | `greet() { echo "Hi"; }` |
| Grep | `grep pattern file` | `grep -i "error" log.txt` |
| Awk | `awk '{print $1}' file` | `awk -F: '{print $1}' /etc/passwd` |
| Sed | `sed 's/old/new/g' file` | `sed -i 's/foo/bar/g' config.txt` |
| Cut | `cut -d',' -f1` | `cut -d',' -f1 users.csv` |
| Sort | `sort file` | `sort names.txt` |
| Uniq | `uniq file` | `uniq -c names.txt` |
| Tr | `tr 'a-z' 'A-Z'` | `echo "hello" \| tr 'a-z' 'A-Z'` |
| Wc | `wc -l file` | `wc -l app.log` |
| Head | `head -5 file` | `head -5 app.log` |
| Tail | `tail -f file` | `tail -f app.log` |
| Exit | `exit 0` | `exit 1` |
| Debug | `set -x` | `set -x` |
| Stop on Error | `set -e` | `set -e` |
| Unset Variable | `set -u` | `set -u` |
| Pipe Errors | `set -o pipefail` | `set -o pipefail` |
| Trap | `trap cleanup EXIT` | `trap cleanup EXIT` |

---