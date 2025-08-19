# 🐚 Shell Scripting – Complete Guide (Basic → Advanced)

---

## 📌 1. Basics of Shell & Scripting

### 🔹 What is a Shell?

* Shell = Command-line interpreter between user and kernel.
* Common shells:

  * `sh` → Bourne Shell
  * `bash` → Bourne Again Shell (most popular)
  * `zsh`, `fish`, `ksh` → Advanced shells

### 🔹 Running Scripts

```bash
# Create a script
nano hello.sh

# Script content:
#!/bin/bash
echo "Hello, World!"

# Make executable
chmod +x hello.sh

# Run
./hello.sh
```

---

## 📌 2. Variables

### 🔹 Defining

```bash
name="Shiva"
age=23
```

### 🔹 Accessing

```bash
echo "My name is $name and I am $age years old."
```

### 🔹 Read Input

```bash
echo "Enter your city:"
read city
echo "You live in $city"
```

---

## 📌 3. Operators

* **Arithmetic** → `$(( ))`

```bash
x=10
y=5
echo $((x+y))   # 15
echo $((x*y))   # 50
```

* **String comparison**

```bash
str1="hello"
str2="world"

if [ "$str1" = "$str2" ]; then
  echo "Equal"
else
  echo "Not Equal"
fi
```

---

## 📌 4. Conditional Statements

```bash
if [ $age -ge 18 ]; then
   echo "Adult"
elif [ $age -ge 13 ]; then
   echo "Teen"
else
   echo "Child"
fi
```

---

## 📌 5. Loops

### 🔹 For Loop

```bash
for i in {1..5}; do
  echo "Number: $i"
done
```

### 🔹 While Loop

```bash
count=1
while [ $count -le 5 ]; do
  echo "Count: $count"
  ((count++))
done
```

### 🔹 Until Loop

```bash
n=1
until [ $n -gt 3 ]; do
  echo "n=$n"
  ((n++))
done
```

---

## 📌 6. Functions

```bash
greet() {
  echo "Hello, $1!"
}

greet Shiva
```

---

## 📌 7. Command-Line Arguments

```bash
# script.sh
echo "Script name: $0"
echo "First arg: $1"
echo "Second arg: $2"
echo "All args: $@"
echo "Arg count: $#"

# Run
./script.sh foo bar
```

---

## 📌 8. Arrays

```bash
arr=(apple banana cherry)

echo "${arr[0]}"      # apple
echo "${arr[@]}"      # apple banana cherry
echo "${#arr[@]}"     # 3
```

---

## 📌 9. Input & Output Redirection

```bash
ls > files.txt       # Write output
cat < files.txt      # Read input
ls >> files.txt      # Append
wc -l < files.txt    # Count lines
```

---

## 📌 10. Pipelines

```bash
cat access.log | grep "ERROR" | sort | uniq -c
```

---

## 📌 11. Exit Status & Error Handling

```bash
ls /notexist
echo $?   # 2 (non-zero means error)

if command -v git >/dev/null; then
  echo "Git installed"
else
  echo "Git not found"
fi
```

---

## 📌 12. Scheduling Jobs (Automation)

* **At**

```bash
echo "echo 'Backup done'" | at now + 1 minute
```

* **Cron**

```bash
crontab -e
# Example: Run backup every day at 2 AM
0 2 * * * /home/user/backup.sh
```

---

## 📌 13. Advanced Text Processing

### 🔹 Using `awk`

```bash
awk '{print $1, $3}' file.txt
```

### 🔹 Using `sed`

```bash
sed 's/error/issue/g' logfile.txt
```

### 🔹 Using `cut`

```bash
cut -d',' -f1,3 data.csv
```

---

## 📌 14. Debugging Scripts

```bash
bash -x script.sh   # Debug mode
set -e              # Exit on error
set -u              # Treat unset vars as error
```

---

## 📌 15. Advanced Concepts

### 🔹 Traps (Signal Handling)

```bash
trap "echo 'Script interrupted!'; exit" SIGINT
while true; do
  echo "Running..."
  sleep 1
done
```

### 🔹 Background & Parallel Jobs

```bash
./long_task.sh &
jobs
fg %1
```

### 🔹 Process Substitution

```bash
diff <(ls dir1) <(ls dir2)
```

---

## 📌 16. Real-World Automation Examples

* **Backup Script**

```bash
#!/bin/bash
tar -czf backup_$(date +%F).tar.gz /home/user/data
```

* **Log Monitoring**

```bash
tail -f /var/log/syslog | grep "ERROR"
```

* **Disk Usage Alert**

```bash
#!/bin/bash
usage=$(df / | awk 'NR==2 {print $5}' | sed 's/%//')
if [ $usage -gt 80 ]; then
  echo "Disk almost full: $usage%" | mail -s "Alert" admin@example.com
fi
```

