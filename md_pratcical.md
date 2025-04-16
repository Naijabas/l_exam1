# Linux Practical Exam – Predicted Questions & Answers

This file contains 20 predicted Linux practical exam questions with **commands**, **descriptions**, and **examples**.

---

## 🔹 Working with Files & Directories

### 1. Create a directory structure
```bash
mkdir -p /home/student/COMP3044/MidTest/scripts /home/student/COMP3044/MidTest/assignments /home/student/COMP3044/MidTest/docs
```
*Creates nested folders as specified.*

---

### 2. Create and populate a file
```bash
echo "Midterm is coming" > /home/student/COMP3044/MidTest/docs/reminder.txt
```
*Creates a text file with content.*

---

### 3. Rename a file
```bash
mv /home/student/COMP3044/MidTest/docs/reminder.txt /home/student/COMP3044/MidTest/docs/midterm_note.txt
```
*Renames the file.*

---

### 4. Copy files
```bash
cp /home/student/COMP3044/MidTest/docs/*.txt /home/student/COMP3044/MidTest/assignments/
```
*Copies all `.txt` files.*

---

### 5. Move files
```bash
mv /home/student/COMP3044/MidTest/docs/midterm_note.txt /home/student/COMP3044/MidTest/scripts/
```
*Moves the file.*

---

### 6. View file content
```bash
cat midterm_note.txt
less midterm_note.txt
head midterm_note.txt
```
*Views file content using different tools.*

---

### 7. Relative and Absolute Paths
```bash
cd ../../scripts
pwd
```
*Navigates using relative paths and confirms location.*

---

## 🔹 Permissions, Ownership & Links

### 8. Change permissions
```bash
chmod 644 midterm_note.txt
```
*Sets file permission to `rw-r--r--`.*

---

### 9. Create a symbolic link
```bash
ln -s /home/student/COMP3044/MidTest/scripts/midterm_note.txt /home/student/COMP3044/MidTest/assignments/note_link.txt
```
*Creates a soft link.*

---

### 10. Set sticky bit on directory
```bash
chmod +t /home/student/COMP3044/MidTest/assignments/
```
*Prevents non-owners from deleting others' files in directory.*

---

## 🔹 User & Group Management

### 11. Create a user and group
```bash
sudo groupadd midgroup
sudo useradd -m -G midgroup testuser
```
*Creates a group and adds a user to it.*

---

### 12. Change ownership
```bash
sudo chown testuser:midgroup /home/student/COMP3044/MidTest/assignments/note_link.txt
```
*Changes owner and group.*

---

## 🔹 System and Security

### 13. Show logged-in users
```bash
who
w
users
```
*Displays currently logged-in users.*

---

### 14. Check disk usage
```bash
df -h
du -sh /home/student/
```
*Shows available disk space and usage of a directory.*

---

### 15. Change password
```bash
sudo passwd testuser
```
*Prompts to set a new password.*

---

## 🔹 Input/Output, Redirection, and Pipes

### 16. Redirect output
```bash
ls -l /etc > etc_list.txt
cat etc_list.txt
```
*Writes list of `/etc` files to a new file.*

---

### 17. Use a pipe
```bash
ls *.sh | wc -l
```
*Counts `.sh` files using a pipe.*

---

### 18. Append text to a file
```bash
echo "Done studying" >> midterm_note.txt
```
*Appends text to the end of a file.*

---

## 🔹 Advanced Tasks

### 19. Use find
```bash
find /home/student/COMP3044/ -name "*.txt"
```
*Finds all `.txt` files under the specified folder.*

---

### 20. Check command/script exit status
```bash
ls /home && echo $?
```
*Shows exit status (`0` = success, `1` = error).*

---
