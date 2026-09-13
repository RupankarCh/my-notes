# Assignment 6: Mail Server Configuration

Here is the complete practical guide structured step-by-step based on your notes.

---

## Part 1: Initial Postfix Setup & Configuration

### 1. Set Hostname and Edit Hosts File

```bash
# Set system hostname
hostnamectl set-hostname Postfix.bwu.com

# Verify hostname
hostnamectl

# Relogin to apply changes
logout
su -

```

Edit `/etc/hosts`:

```bash
vim /etc/hosts

```

Press `i` to enter Insert mode and add:

```text
192.168.10.2 Postfix.bwu.com localhost

```

Press `ESC`, type `:wq` and press `Enter` to save and exit.

---

### 2. Install Postfix and Mail Utilities

```bash
# Install Postfix
yum install postfix -y

# Start and enable Postfix service
systemctl start --now postfix.service

# Check service status
systemctl status postfix.service

# Install mail client (Prefer s-nail or mailx)
yum install mailx -y
# OR
yum install s-nail -y

```

---

### 3. Configure Postfix (`main.cf`)

```bash
cd /etc/postfix/
vim main.cf

```

> **Tip:** In Vim, enable line numbers by typing `ESC` then `:set nu`.

Uncomment (`#`) or edit the following line numbers:

* **Line 94:** Remove `#` and set `myhostname = Postfix.bwu.com`
* **Line 102:** Remove `#` and set `mydomain = bwu.com`
* **Line 118:** Remove `#` and set `myorigin = $mydomain`
* **Line 132:** Remove `#` and set `inet_interfaces = all`
* **Line 135:** Add `#` to `# inet_interfaces = localhost`
* **Line 138:** Check line for `inet_protocols = all`
* **Line 183 / 185:** Remove `#` and configure network IP range (e.g., `192.168.10.0/24`)
* **Line 283:** Remove `#` for `mynetworks = 127.0.0.0/8`
* **Line 438:** Remove `#`

Save and exit in Vim: `ESC` -> `:wq`

---

## Part 2: Sending & Checking Basic Mails

### 1. Basic Mail via Sendmail

```bash
# Install Sendmail
yum install sendmail -y

# Create mail content
vim /tmp/email.txt
# (Write any text content inside)

# View created file
cat /tmp/email.txt

# Start sendmail service
systemctl start --now sendmail

# Send mail to user
sendmail abc@localhost < /tmp/email.txt

```

#### To Check Received Mail (as Root or User):

Open a second terminal / root user tab:

```bash
cd /var/spool/mail
ls
cat abc

```

---

### 2. Sendmail with Subject & Attachments

```bash
# Create attachment file (e.g., calendar data)
cal > /tmp/cal.txt
cat /tmp/cal.txt

# Create mail body content
vim /tmp/mail.txt
# (Write any message body content inside)

# Send email with attachment (-a) and subject (-s)
mail -a /tmp/mail.txt -s "Calendar" abc@localhost < /tmp/cal.txt

```

#### To Check Received Mail:

```bash
cd /var/spool/mail
cat abc

```

---

## Part 3: User Creation & Testing via Telnet (SMTP)

### 1. Restart Service & Add Test Users

```bash
systemctl restart postfix.service

# Create test users
useradd Postfix1
passwd Postfix1

useradd abc
passwd abc

# Install Telnet for testing
yum install telnet -y

```

---

### 2. Test Sending Mail via Telnet (SMTP)

```bash
telnet localhost smtp

```

Type the following interactive SMTP commands:

```text
ehlo localhost
mail from: <abc>
rcpt to: <Postfix1>
data
hello !! (Mail Subject / Body)
.
quit

```

*(Note: A single dot `.` on its own line ends the body input, then `quit` exits SMTP).*

---

### 3. Check Mail Content in Maildir / Home Directory

```bash
cd /home/Postfix1/
ls
cd Maildir/
ls
cd new/
ls
cat <file_name>   # e.g., cat 178...80

```

---

### 4. Direct Mail Command Testing

```bash
su - # Log in with Postfix hostname
echo "hello msg" | mail -s "hi" Postfix1@localhost

```

#### Check Recipient Inbox:

```bash
cd /home/Postfix1
ls
cd Maildir/
ls
cd new/
ls
cat <file_name>

```

---

## Part 4: Mail Server Configuration Using Dovecot (POP3/IMAP)

### 1. Install and Configure Dovecot

```bash
# Install Dovecot
yum install dovecot -y

# Go to configuration directory
cd /etc/dovecot
vim dovecot.conf

```

* **Line 24:** Remove `#` to enable protocols.
* Save and exit (`:wq`).

---

### 2. Configure Sub-files in `conf.d/`

```bash
cd conf.d/
ls

```

#### Edit `10-mail.conf`:

```bash
vim 10-mail.conf

```

* **Line 24:** Remove `#`

#### Edit `10-auth.conf`:

```bash
vim 10-auth.conf

```

* **Line 10:** Remove `#`
* **Line 100:** Edit or set `auth_mechanisms = plain login`

#### Edit `10-master.conf`:

```bash
vim 10-master.conf

```

* **Line 102:** Set `user = postfix` (remove `#`)
* **Line 103:** Set `group = postfix` (remove `#`)

---

### 3. Start Dovecot & Retrieve Mail via POP3

```bash
# Start and enable Dovecot
systemctl start --now dovecot

# Connect via Telnet to POP3 port
telnet localhost pop3

```

Interactive POP3 commands:

```text
user <Receiver_Username>
pass <Receiver_Password>
retr 1

```

*(Use `retr 2`, `retr 3`, etc., to retrieve subsequent messages).*
