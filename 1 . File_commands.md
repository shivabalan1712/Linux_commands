# 🐧 Linux File Commands Cheat Sheet

---

## 📂 File & Directory Navigation  
- `pwd` → Print current working directory  
- `ls` → List files in directory  
  - `ls -l` → Long format (permissions, owner, size, date)  
  - `ls -a` → Show hidden files (`.` files)  
  - `ls -lh` → Human-readable sizes  
- `cd dir_name` → Change directory  
- `cd ..` → Go one directory up  
- `cd ~` → Go to home directory  

---

## 📁 File & Directory Creation  
- `touch file.txt` → Create empty file  
- `mkdir dir_name` → Create directory  
- `mkdir -p parent/child` → Create nested directories  

---

## 📝 File Viewing  
- `cat file.txt` → Show file content  
- `less file.txt` → Scroll through file (press `q` to quit)  
- `head -n 10 file.txt` → Show first 10 lines  
- `tail -n 10 file.txt` → Show last 10 lines  
- `tail -f file.txt` → Follow file updates (logs)  

---

## ✏️ File Editing  
- `nano file.txt` → Open file in **nano editor**  
- `vi file.txt` → Open file in **vim editor**  

---

## 🔄 File Management  
- `cp file1.txt file2.txt` → Copy file  
- `cp -r dir1 dir2` → Copy directory recursively  
- `mv file.txt newfile.txt` → Rename/move file  
- `rm file.txt` → Delete file  
- `rm -r dir_name` → Delete directory & contents  
- `rm -rf dir_name` → Force delete  

---

## 🔍 Searching & Finding  
- `find . -name "*.txt"` → Find all `.txt` files in current directory  
- `grep "word" file.txt` → Search for "word" inside file  
- `grep -r "word" dir/` → Search recursively in directory  

---

## 🔒 Permissions & Ownership  
- `ls -l` → Check permissions  
- `chmod 755 file.sh` → Change permissions  
- `chown user:group file.txt` → Change owner  

---

## 📦 Compression & Archiving  
- `tar -cvf archive.tar dir/` → Create tar archive  
- `tar -xvf archive.tar` → Extract tar archive  
- `gzip file.txt` → Compress file  
- `gunzip file.txt.gz` → Decompress  

---

## 📊 File Information  
- `file file.txt` → Show file type  
- `wc file.txt` → Word, line, character, and byte count  
- `stat file.txt` → Detailed file info (size, modified time)  
- `du -sh dir/` → Directory size  
- `df -h` → Disk space usage  

---

## 📄 File Command Options  

### 1. Version & Help  
- `file -v` → Show version  
- `file --help` → Show help  

---

### 2. Output Format  
- `file -b file.txt` → Show type only (brief, no filename)  
  ```bash
  `file -b notes.txt`
  # Output: ASCII text
- `file -i file.txt` → Show MIME type & encoding

  ```bash
  file -i notes.txt
  # Output: text/plain; charset=us-ascii
- `file --mime-type file.txt` → Only MIME type

- `file --mime-encoding file.txt` → Only encoding

### 3. Compressed Files

- `file -z archive.gz` → Look inside compressed file

- `file -Z archive.gz` → Show only inner file type

### 4. File Lists

- `file -f list.txt` → Read filenames from a file (`list.txt` contains one filename per line)

### 5. Symbolic Links

- `file -L symlink` → Follow symlink

- `file -h symlink` → Do not follow symlink (default in many cases)

### 6. Miscellaneous

- `file -k file` → Keep going, don’t stop at first match

- `file -N file` → Don’t pad output with spaces

- `file -p file` → Preserve access time of the file

## ⚡ Practical Examples

  ```bash
  file script.sh
  # Output: script.sh: Bourne-Again shell script, ASCII text executable

  file -i image.png
  # Output: image/png; charset=binary

  file -b report.pdf
  # Output: PDF document, version 1.7

  file -z data.tar.gz
  # Output: data.tar.gz: gzip compressed data, was "data.tar"

```

# File Search

## 🔍 Using find

### Search for a file by name (case-sensitive):

```bash
find /path/to/search -type f -name "filename.txt"
```

- `/path/to/search` → directory to start searching (use / for entire system or . for current directory).

- `type f` → search only files.

- `name` → match exact name.

### 👉 Example: search in current directory

```bash
find . -type f -name "test.txt"
```

### Case-insensitive search:

``` bash 
find . -type f -iname "test.txt"
```


### Search for all `.txt` files:

```bash
find . -type f -name "*.txt"
```


## ⚡ Using locate (faster, but requires updated database)
```bash
locate filename.txt
```

### 👉 If database is outdated, update it with:
```bash
sudo updatedb
```
### ✅ Practical Tip

If you only know part of the filename:
```bash
find . -type f -name "*part*"
```
### 📂 Search inside files with grep

Basic usage:
```bash
grep "search_text" filename
```

Search inside all files in a directory:
```bash
grep "search_text" *
```

Recursive search through subdirectories:
```bash
grep -r "search_text" /path/to/search
```

Case-insensitive search:
```bash
grep -i "search_text" filename
```

Show line numbers where matches occur:
```bash
grep -n "search_text" filename
```
### 🔥 Combine with `find`

Example: Find all `.txt` files containing the word "error":
```bash
find . -type f -name "*.txt" -exec grep -i "error" {} +
```
## 🔧 Advanced Tricks with find
### 1️⃣ Search by file size
```bash
find . -type f -size +10M
```


- `+10M` → bigger than 10 MB

- `-10M` → smaller than 10 MB

- `100k` → exactly 100 KB

### 2️⃣ Search by last modified time

Files modified in the last 1 day:
```bash
find . -type f -mtime -1
```

- `-mtime` -1 → modified less than 1 day ago

- `-mtime` +7 → modified more than 7 days ago

### 3️⃣ Search by permissions

Find world-writable files:
```bash
find . -type f -perm 777
```

### 4️⃣ Search by owner / group
```bash
find /var/log -type f -user root
find /home -type f -group admin
```
### 5️⃣ Search and execute a command

Delete all `.tmp` files:
```bash
find . -type f -name "*.tmp" -exec rm -f {} \;
```
## ⚡ Faster Alternatives
`fd` (user-friendly `find`)
```bash
fd filename
fd -e txt
```

- Much faster and simpler syntax.

### `rg` (ripgrep – faster `grep`)

Search inside files:
```bash
rg "error"
rg -i "warning" *.log
```
## 📝 Quick Comparison

| Tool     | Purpose                                | Speed     |
|----------|----------------------------------------|-----------|
| `find`   | Search by name, size, time, perms, etc | Medium    |
| `locate` | Super-fast name search (needs updatedb)| Fast      |
| `grep`   | Search inside files                    | Medium    |
| `rg`     | Faster alternative to grep             | Very Fast |
| `fd`     | Simpler & faster alternative to find   | Very Fast |

## 📂 Viewing & Managing Files in CLI
### 🔍 View file contents

- Show full content:
```bash
cat filename.txt
```

- Show with line numbers:
```bash
nl filename.txt
```

- Scroll through long files (page by page):
```bash
less filename.txt
```

(Navigate with ↑ ↓, search with `/word`, quit with `q`)

- View first / last lines:
```bash
head filename.txt    # first 10 lines
tail filename.txt    # last 10 lines
tail -f logfile.log  # live updates (great for logs)
```
### 🛠️ Edit files directly from terminal

- With nano (simple editor):
```bash
nano filename.txt
```

- With vim (advanced editor):
```bash
vim filename.txt
```
### 📦 Copy / Move / Delete

- Copy file:
```bash
cp file.txt backup.txt
```

- Move/rename file:
```bash
mv oldname.txt newname.txt
```

- Delete file:
```bash
rm file.txt
```

(Delete recursively with `rm -r folder/`)

## 🔑 File Permissions & Ownership

- Check permissions:
```bash
ls -l
```

- Change permissions:
```bash
chmod 755 script.sh
```

- Change owner:
```bash
sudo chown user:group file.txt
```