# Linux Practical Exam Cheatsheet

## 📁 Working with Files and Folders

### View Files
```bash
cat file.txt       # View file content
less file.txt      # View file with scroll
head file.txt      # First 10 lines
tail file.txt      # Last 10 lines
```

### Create Files/Folders
```bash
touch file.txt               # Create file
mkdir mydir                 # Create directory
mkdir -p dir1/dir2          # Create nested directories
```

### Delete Files/Folders
```bash
rm file.txt                 # Delete file
rm -r mydir                 # Delete directory
rm -rf mydir                # Force delete
```

### Copy Files/Folders
```bash
cp file.txt newfile.txt           # Copy file
cp -r mydir/ newdir/              # Copy directory
```

### Move or Rename Files/Folders
```bash
mv file.txt newname.txt          # Rename
mv file.txt /path/to/dest/       # Move
```

### Absolute and Relative Paths
```bash
cd /home/user/docs          # Absolute path
cd ../../folder             # Relative path
```

### Pipes and Redirection
```bash
ls | grep "txt"             # Pipe: output of ls to grep
cat file.txt > out.txt      # Redirect output to file (overwrite)
cat file.txt >> out.txt     # Append output to file
sort < file.txt             # Input redirection
```

## 🔐 System and User Security

### View Logged In Users
```bash
who
w
```

### Check Login History
```bash
last                        # History of logged in users
```

### Firewall (Basic)
```bash
sudo ufw status
sudo ufw enable
sudo ufw allow 22/tcp
```

## 👥 Managing Users, Groups, Passwords

### Users
```bash
sudo adduser newuser          # Add user
sudo deluser olduser          # Delete user
```

### Groups
```bash
sudo groupadd devs            # Create group
sudo usermod -aG devs user1   # Add user to group
groups user1                  # View groups
```

### Passwords
```bash
passwd                        # Change own password
sudo passwd username          # Change another user's password
```

## 🔑 Ownership and Permissions

### Ownership
```bash
chown user:group file.txt     # Change owner
ls -l                         # View owner and permissions
```

### Permissions
```bash
chmod u+x file.sh             # Add execute to owner
chmod 755 file.sh             # rwxr-xr-x
chmod 644 file.txt            # rw-r--r--
```

### Default Permissions
- Controlled by `umask`
```bash
umask                        # Check default
umask 022                    # Set default (644 for files, 755 for dirs)
```

## 🔐 Special Permissions and Links

### Special Permissions
```bash
chmod +s file.sh             # SetUID (run as owner)
chmod +g file.sh             # SetGID (run as group)
chmod +t dir/                # Sticky Bit (prevent file deletion by others)
```

### Links
```bash
ln file.txt link1            # Hard link
ln -s file.txt link2         # Symbolic (soft) link
```

### View Shadow File
```
tail -5 /etc/shadow
```


### View User Information
```
id
id root
id -g                       # View group assigned
id -G                       # View secondary group assigned
```
```
who                          # View Current User
who -b -r                    # the -b option shows the last time the system started (booted), and the -r option shows the time the system reached the current runlevel:
```

> ✅ Tip: Use `man command` (e.g., `man ls`) to learn more about any command.
