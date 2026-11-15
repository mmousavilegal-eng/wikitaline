# سامانه مدیریت استراحت پشتیبانی طلایین

این پروژه یک وب‌اپ فارسی برای ثبت استراحت کارشناسان با Firebase Authentication و Cloud Firestore است.

## فایل‌ها
- `index.html`: رابط کاربری و منطق برنامه
- `firestore.rules`: قوانین دسترسی Firestore

## ۱) ساخت پروژه Firebase
1. در https://console.firebase.google.com یک پروژه بسازید.
2. در Project settings > General > Your apps یک Web App بسازید.
3. مقادیر Firebase SDK config را کپی کنید.
4. در `index.html` مقدارهای `YOUR_API_KEY`، `YOUR_PROJECT_ID`، `YOUR_MESSAGING_SENDER_ID` و `YOUR_APP_ID` را با مقادیر واقعی جایگزین کنید.

## ۲) فعال‌کردن ورود
1. در Firebase Console به Authentication > Sign-in method بروید.
2. روش Email/Password را فعال کنید.

## ۳) ساخت دیتابیس و انتشار قوانین
1. به Firestore Database بروید و دیتابیس را بسازید.
2. در تب Rules، تمام محتوای `firestore.rules` را جایگزین و Publish کنید.

## ۴) ساخت اولین مدیر
1. از سایت با ایمیل خود یک حساب بسازید.
2. در Firebase Console به Firestore بروید.
3. در مجموعه `users` سندی با شناسه UID همان کاربر را پیدا کنید.
4. فیلد `role` را از `employee` به `admin` تغییر دهید.
5. از سایت خارج و دوباره وارد شوید. پنل مدیریت نمایش داده می‌شود.

نکته: شناسه UID را از Authentication > Users می‌توانید بردارید. نقش مدیر را به هیچ کاربر عادی ندهید.

## ۵) انتشار در GitHub Pages
1. یک مخزن GitHub بسازید.
2. `index.html` را در ریشه مخزن با همین نام قرار دهید.
3. در Settings > Pages، گزینه Deploy from a branch، شاخه `main` و پوشه `/ (root)` را انتخاب کنید.
4. آدرس منتشرشده را باز کنید.

در Firebase Authentication > Settings > Authorized domains، دامنه GitHub Pages خود را نیز اضافه کنید (مثلاً `username.github.io`).

## نکات مهم و محدودیت‌های نسخه اولیه
- اطلاعات حساب‌ها و سوابق در Firebase نگهداری می‌شوند و بین دستگاه‌ها همگام می‌شوند.
- ثبت‌نام عمومی در این نسخه روشن است؛ برای استفاده سازمانی بهتر است بعداً ثبت‌نام عمومی بسته و حساب‌ها توسط مدیر/مسئول ایجاد شوند.
- این نسخه گزارش‌های اخیر را نشان می‌دهد؛ فیلترهای پیشرفته بازه تاریخ، خروجی Excel و تنظیم سهمیه مجاز برای هر کاربر هنوز پیاده‌سازی نشده‌اند.
- ساعت شروع/پایان از زمان دستگاه کاربر گرفته می‌شود؛ برای ثبت زمان کاملاً قابل اعتماد و کنترل‌شده، باید منطق ثبت زمان به Cloud Functions منتقل شود.
- قوانین Firestore را قبل از استفاده واقعی بازبینی کنید و کلیدهای محرمانه یا رمز عبور را داخل کد قرار ندهید. Firebase Web config به‌تنهایی رمز عبور نیست، اما امنیت واقعی با Rules و تنظیمات Authentication تأمین می‌شود.
