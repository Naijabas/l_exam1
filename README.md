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

useradd jane                  # Add a user [Run As root]
useradd -u 1000 jane          # Add, also assign UID [Run As root]
useradd -g users jane         # Add, also assign to group users
useradd -G sales,research jane # Add, also assign to groups
useradd -m jane               # Add, also make home dir
useradd -mb /test jane        #Add, also specify custom home directory
useradd -mk /home/sysadmin jane   # Add, make the dir skeleton dir
useradd -c 'Jane Doe' jane    # COmment

useradd -u 1009 -g users -G sales,research -m -c 'Jane Doe' jane
# created jane user, with UID 1009, added two groups, -m create home dir, added comment 'Jane Doe'


grep '/home/jane' /etc/passwd # Viewing jane details
grep jane /etc/passwd         # Find jane in the passwd file
grep jane /etc/shadow         # ///
grep jane /etc/group          # Find Jane in the group file
grep jane /etc/gshadow        # group shadow

sudo deluser olduser          # Delete user
userdel -r jane               # -r deletes user, home directory, and mail spool

useradd -D                     # View Default useradd settings
grep -Ev '^#|^$' /etc/login.defs    # Load /login/defs
```

### Groups
```bash
sudo groupadd devs            # Create group
sudo usermod -aG devs user1   # Add user to group
groups user1                  # View groups
groups                        # List all foods

chgrp research sample         # Chnage the sample dir group owner to research

grep root /etc/group          # View local groups
getent group root              # View Local and Network-Based groups
groupadd -g 1005 research     # Create a group called research by passing a GID of 1005
groupadd devs                 # Automatically assign gid

grep research /etc/group      # Find the just created group

groupadd -r sales            # -r makes you assign id lower than 1000 (which is reserved for system)
getent group sales            # Using getent to get group

groupmod -n clerks sales      # Change name of a group from sales to clerks
groupmod -g 10003 clerks      # Change id of clerks
find / -nogroup               # To find files not owned by any group
groupdel clerks               # delete a group
```


### Group change/Owner
```bash
chgrp -R development test_dir # change the group recursively
chown user /path/to/file      # make user 'user' own the part
chown user:group /path/to/file # Change owner of a file

chown :developers /home/basit/project.txt # Sets the group of project.txt to developers, owner remains the same.
chown .developers /home/basit/project.txt # Same thing
```

### Passwords
```bash
passwd                        # Change own password
sudo passwd username          # Change another user's password

passwd jane                   # Change Jane's password

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


chmod g+w abc.txt             # This gives group owner write access
chmod ug+x,o-r abc.txt        # this gives user and group owner executable, and remove read access from others
chmod u=rx abc.txt            # this gives user owner read and executable

# u	user owner
# g	group owner
# o	others
# a	all (user owner, group owner, and others)
# r	read
# w	write
# x	execute

# 4	Read
# 2	Write
# 1	Execute



chmod u+s file                # Set setuid
chmod 4775                    # Set setuid (4000 to set)
chmod u-s file                # Remove setuid
chmod 0775 file               # Remove setuid (0***)

chmod g+s file                # Set setgid
chmod 2775                    # Set setgid (2000 to set)
chmod g-s file                # Remove setgid
chmod 0775 file               # Remove setgid (0***)

chmod o+t file                # Set sticky
chmod 1775                    # Set sticky (1000 to set)
chmod o-t file                # Remove sticky
chmod 0775 file               # Remove sticky (0***)

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

ln target link_name          # 
ls -li file.*                # To view link details

ls -l /etc/grub.conf         # To view details of the link
ln -s target link_name       # To create a Symbolic link

```

### View Shadow File
```bash
tail -5 /etc/shadow
```


### View User Information
```bash
id
id root
id -g                       # View group assigned
id -G                       # View secondary group assigned
```bash
```
who                          # View Current User
who -b -r                    # the -b option shows the last time the system started (booted), and the -r option shows the time the system reached the current runlevel:
```


more test.txt               # To read a file
### 

> ✅ Tip: Use `man command` (e.g., `man ls`) to learn more about any command.
