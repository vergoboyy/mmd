برای راه‌اندازی سرور **Counter-Strike 1.6** روی سرور لینوکسی، مراحل زیر را دنبال کنید:

---

### 1. **نصب پیش‌نیازها**
ابتدا مطمئن شوید که سرور لینوکس شما به‌روز است و ابزارهای مورد نیاز نصب شده‌اند:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install lib32gcc-s1 wget curl -y
```

---

### 2. **ایجاد پوشه سرور**
یک دایرکتوری برای فایل‌های سرور ایجاد کنید و وارد آن شوید:

```bash
mkdir cs16server
cd cs16server
```

---

### 3. **دانلود SteamCMD**
`SteamCMD` ابزار رسمی برای نصب و مدیریت سرورهای بازی‌های Steam است. برای دانلود آن:

```bash
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
tar -xvzf steamcmd_linux.tar.gz
```

---

### 4. **نصب سرور CS 1.6**
1. **اجرای SteamCMD:**

```bash
./steamcmd.sh
```

2. **نصب سرور CS 1.6:**

در محیط SteamCMD، دستورات زیر را وارد کنید:

```bash
login anonymous
force_install_dir /home/your user/cs16server
app_update 90 validate
exit
```

**نکته:** `/home/your user/cs16server` را با مسیر دلخواه خود جایگزین کنید.

---

### 5. **تنظیمات سرور**
1. وارد پوشه سرور شوید:
   ```bash
   cd /home/your user/cs16server
   ```
2. فایل کانفیگ سرور را باز کنید:
   ```bash
   nano hlds_run
   ```
   تنظیمات مربوط به پورت، نقشه پیش‌فرض، تعداد بازیکنان و دیگر تنظیمات را تغییر دهید.

---

### 6. **اجرای سرور**
برای راه‌اندازی سرور، از دستور زیر استفاده کنید:

```bash
./hlds_run -game cstrike +map de_dust2 +maxplayers 16 -port 27015
```

- `+map`: نقشه‌ای که سرور با آن شروع شود.
- `+maxplayers`: تعداد بازیکنان حداکثر.
- `-port`: شماره پورت سرور.

---

### 7. **اتصال به سرور**
1. از طریق بازی CS 1.6، آدرس IP سرور را در قسمت **Find Servers** وارد کنید.
2. در صورت نیاز، پورت را نیز اضافه کنید (مانند `your-ip:27015`).

---

### 8. **نکات اضافی**
- **پشتیبانی از پلاگین‌ها:** برای افزودن پلاگین‌ها یا مادها می‌توانید از AMX Mod X استفاده کنید. اطلاعات بیشتر در [AMX Mod X](https://www.amxmodx.org/) موجود است.
- **راه‌اندازی در پس‌زمینه:** برای اجرای سرور در پس‌زمینه از `screen` یا `tmux` استفاده کنید:
  ```bash
  screen -S cs16server ./hlds_run -game cstrike +map de_dust2 +maxplayers 16 -port 27015
  ```

- **فایروال:** اگر فایروال فعال است، پورت مورد نظر را باز کنید:
  ```bash
  sudo ufw allow 27015
  ```

با این مراحل سرور شما آماده استفاده است! اگر مشکلی پیش آمد، بپرسید. 😊