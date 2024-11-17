برای راه‌اندازی سرور **Quilt** روی یک سیستم لینوکسی، می‌توانید از مراحل زیر پیروی کنید. Quilt یک پلتفرم مدینگ برای ماینکرفت است که به عنوان جایگزین Fabric طراحی شده است و با آن سازگاری دارد.

---

### 1. **نصب پیش‌نیازها**
اطمینان حاصل کنید که سرور لینوکس شما به‌روز است و جاوا نصب شده است.

1. به‌روزرسانی سیستم:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. نصب جاوا (نیاز به جاوا 17 یا بالاتر):
   ```bash
   sudo apt install openjdk-17-jdk -y
   ```
   بررسی نسخه جاوا:
   ```bash
   java -version
   ```

---

### 2. **ایجاد دایرکتوری سرور**
پوشه‌ای برای سرور ایجاد کرده و وارد آن شوید:
```bash
mkdir quiltserver
cd quiltserver
```

---

### 3. **دانلود Quilt Installer**
Quilt Installer را از [QuiltMC Installer](https://quiltmc.org/en/install/server/) دانلود کنید.

1. دانلود مستقیم با `wget`:
   ```bash
   wget https://quiltmc.org/api/v1/download-latest-installer/java-universal -O quilt-installer
   ```
2. اجرای نصب‌کننده:
   ```bash
   java -jar quilt-installer install server <minecraft-version> [<loader-version>] [SERVER-INSTALL-OPTIONS]
   ```

3. هنگام اجرای نصب‌کننده:
   - **نسخه ماینکرفت:** نسخه‌ای که می‌خواهید سرور از آن استفاده کند را مشخص کنید (مثلاً 1.20.1).
   - **نوع سرور:** Quilt.
   - **پوشه سرور:** پوشه‌ای که می‌خواهید فایل‌های سرور در آن نصب شوند.

---

### 4. **پیکربندی سرور**
1. فایل `eula.txt` در پوشه سرور را باز کرده و مقدار `eula=false` را به `eula=true` تغییر دهید:
   ```bash
   nano eula.txt
   ```
2. ذخیره و خروج با `CTRL+O` و سپس `CTRL+X`.

---

### 5. **نصب مادها (اختیاری)**
برای اضافه کردن مادها:
1. وارد پوشه `mods` شوید:
   ```bash
   cd mods
   ```
2. مادهای مورد نظر خود را از سایت‌هایی مانند [Modrinth](https://modrinth.com/) یا [CurseForge](https://www.curseforge.com/) دانلود کرده و به این پوشه منتقل کنید.

---

### 6. **اجرای سرور**
برای اجرای سرور، دستور زیر را اجرا کنید:
```bash
java -Xmx2G -Xms2G -jar quilt-server-launch.jar nogui
```
- `-Xmx2G` و `-Xms2G`: مقدار حافظه رم اختصاص داده شده به سرور را مشخص می‌کند (می‌توانید این مقدار را بر اساس نیاز خود تغییر دهید).

---

### 7. **مدیریت سرور**
- برای اجرای سرور در پس‌زمینه از `screen` استفاده کنید:
  ```bash
  screen -S quiltserver java -Xmx2G -Xms2G -jar quilt-server-launch.jar nogui
  ```
- باز کردن مجدد محیط `screen`:
  ```bash
  screen -r quiltserver
  ```

---

### منابع اضافی برای دانلود مادها:
- [Modrinth](https://modrinth.com/)
- [CurseForge](https://www.curseforge.com/)
- [Quilt Project](https://quiltmc.org/)

---

با این مراحل، سرور Quilt شما آماده استفاده خواهد بود. اگر سوالی دارید، بپرسید! 😊