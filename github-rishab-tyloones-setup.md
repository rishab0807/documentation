# 📘 GitHub Multi-Account Setup (WSL + Windows)

## Account: `rishab-tyloones`
**Email:** `rishab@tyloones.com`  
**OS:** Windows + WSL (Ubuntu)  
**Authentication:** SSH  
**Git Identity:** Folder-based configuration

---

## 🎯 Final Conventions (Do Not Change)

| Item | Value |
|---|---|
| GitHub username | `rishab-tyloones` |
| Email | `rishab@tyloones.com` |
| SSH key filename | `rishab_tyloones` |
| SSH host alias | `tyloones.github.com` |
| Workspace folder | `R:\work\rishab-tyloones` |
| Git author name | `rishab-tyloones` |

---

# 🐧 PART 1 — WSL (Linux Subsystem)

## 1️⃣ Create SSH key

```bash
ssh-keygen -t ed25519 -C "rishab@tyloones.com"
```

When prompted, enter the full path:

```
/home/hp/.ssh/rishab_tyloones
```

Fix permissions:

```bash
chmod 600 ~/.ssh/rishab_tyloones
chmod 644 ~/.ssh/rishab_tyloones.pub
```

---

## 2️⃣ Add SSH key to GitHub

```bash
cat ~/.ssh/rishab_tyloones.pub
```

GitHub → **Settings → SSH and GPG keys → New SSH key**  
Title: `rishab-tyloones`

---

## 3️⃣ Configure SSH (WSL)

Edit SSH config:

```bash
nano ~/.ssh/config
```

Add below coder-managed blocks:

```ssh
# -------- GitHub : rishab-tyloones --------
Host tyloones.github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/rishab_tyloones
    IdentitiesOnly yes
```

```bash
chmod 600 ~/.ssh/config
```

---

## 4️⃣ Test SSH (WSL)

```bash
ssh -T git@tyloones.github.com
```

Expected:

```
Hi rishab-tyloones! You've successfully authenticated, but GitHub does not provide shell access.
```

---

# 🪟 PART 2 — Windows

## 5️⃣ Copy SSH key from WSL → Windows

```bash
cp ~/.ssh/rishab_tyloones /mnt/c/Users/HP/.ssh/
cp ~/.ssh/rishab_tyloones.pub /mnt/c/Users/HP/.ssh/
```

Verify:

```bat
dir C:\Users\HP\.ssh
```

---

## 6️⃣ Configure SSH (Windows)

Open:

```bat
notepad C:\Users\HP\.ssh\config
```

Add at the bottom:

```ssh
# -------- GitHub : rishab-tyloones --------
Host tyloones.github.com
    HostName github.com
    User git
    IdentityFile C:/Users/HP/.ssh/rishab_tyloones
    IdentitiesOnly yes
```

---

## 7️⃣ Reset SSH agent (Windows)

```bat
ssh-add -D
ssh-add C:\Users\HP\.ssh\rishab_tyloones
```

---

## 8️⃣ Test SSH (Windows)

```bat
ssh -T git@tyloones.github.com
```

Expected:

```
Hi rishab-tyloones! You've successfully authenticated
```

---

# 📁 PART 3 — Git Identity (Author Name & Email)

## 9️⃣ Create workspace folder

```bat
mkdir R:\work\rishab-tyloones
```

---

## 🔧 10️⃣ Create Git identity file (WSL)

```bash
nano ~/.gitconfig-rishab-tyloones
```

```ini
[user]
    name = rishab-tyloones
    email = rishab@tyloones.com
```

---

## 🔧 11️⃣ Attach identity (WSL Git)

```bash
nano ~/.gitconfig
```

```ini
# rishab-tyloones (WSL)
[includeIf "gitdir:/mnt/r/work/rishab-tyloones/"]
    path = ~/.gitconfig-rishab-tyloones
```

---

## 🔧 12️⃣ Attach identity (Windows Git)

```bat
notepad C:\Users\HP\.gitconfig
```

```ini
# rishab-tyloones (Windows)
[includeIf "gitdir/i:R:/work/rishab-tyloones/"]
    path = C:/Users/HP/.gitconfig-rishab-tyloones
```

Copy identity file:

```bash
cp ~/.gitconfig-rishab-tyloones /mnt/c/Users/HP/.gitconfig-rishab-tyloones
```

---

# ✅ PART 4 — Verification

## WSL

```bash
cd /mnt/r/work/rishab-tyloones
git init
git config user.name
git config user.email
```

Expected:

```
rishab-tyloones
rishab@tyloones.com
```

---

## Windows

```bat
cd R:\work\rishab-tyloones
git config user.name
git config user.email
```

Expected:

```
rishab-tyloones
rishab@tyloones.com
```

---

# 🚀 How to Clone Repositories

```bash
git clone git@tyloones.github.com:rishab-tyloones/<repo>.git
```

---

# 🧠 Key Rules

- SSH decides which GitHub account you authenticate as
- Git config decides author name/email on commits
- WSL Git and Windows Git are separate
- One GitHub account = one SSH host alias
- Always provide a full path to ssh-keygen
