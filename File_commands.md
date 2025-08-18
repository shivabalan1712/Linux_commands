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
