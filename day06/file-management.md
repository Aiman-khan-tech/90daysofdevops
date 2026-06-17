# Day 06 - Linux Fundamentals: Read and Write Text Files

## Objective

Practice basic file input/output operations in Linux using fundamental commands.

---

## Commands Executed

### Create a file

```bash
touch notes.txt
```

Creates an empty file named `notes.txt`.

---

### Write text to the file

```bash
echo "Linux is powerful" > notes.txt
echo "DevOps relies heavily on Linux" >> notes.txt
```

* `>` creates or overwrites file content.
* `>>` appends content to an existing file.

---

### Write and display simultaneously

```bash
echo "Learning file operations today" | tee -a notes.txt
```

* `tee` displays output on the terminal and appends it to the file.

---

### Add additional lines

```bash
echo "Logs are text files" >> notes.txt
echo "Configuration files are important" >> notes.txt
echo "Automation starts with scripts" >> notes.txt
echo "Linux skills improve troubleshooting" >> notes.txt
echo "Practice builds confidence" >> notes.txt
```

---

## Read File Content

### Display complete file

```bash
cat notes.txt
```

Reads and displays the entire file.

### Display first 2 lines

```bash
head -n 2 notes.txt
```

Shows the first two lines of the file.

### Display last 2 lines

```bash
tail -n 2 notes.txt
```

Shows the last two lines of the file.

---

## Key Learnings

* `touch` creates files.
* `>` overwrites content.
* `>>` appends content.
* `cat` displays entire files.
* `head` and `tail` help inspect specific portions of a file.
* `tee` writes and displays output simultaneously.

## Why This Matters

Most Linux administration and DevOps work involves interacting with text files such as logs, configuration files, scripts, and automation artifacts. Understanding file operations is a foundational Linux skill.

