![Logo](images/Logo.png)

# ماژول runtime_scaler
این ماژول ابزارهایی را برای اجرای کد به صورت دوره ای با زمان بندی های مشخص ارائه میدهد
## زمان بندی نرم افزار نهفته
در بسیاری از بخش های نرم افزار نهفته نیاز است که بخشی از کد به صورت دوره ای با دوره اجرای مشخص اجرا شود.
 مثال های زیر از جمله این موارد است : 
 - چشمک زدن یک نمایشگر
 - اجرای دیبانس بر روی ورودی دیجیتال یک کلید فشاری
 - نمونه برداری از مبدل آنالوگ به دیجیتال و اجرای فیلتر بر روی آن
 - ذخیره کردن اطلاعات در حافظه
 - اجرای حلقه های کنترلی
 - اجرای منطق سطح بالای نرم افزار (مانند ماشین حالت)
 - ارسال دوره ای اطلاعات بر روی پورت سریال
 - چک کردن شرایط رخ دادن یک رویداد
 - . . . 

برخی از این کاربردها نیاز به دقت زمانی بالا و برخی نیاز به دقت زمانی پایین دارد. 
در مورد دسته دوم (دوره زمانی با دقت پایین) که اتفاقا در بسیاری از کاربردها، تعداد آن بیشتر از دسته اول (دوره زمانی با دقت بالا) است، نیاز به ابزاری برای اجرای این کدها داریم.
 برای اطلاعات بیشتر در مورد زمان بندی نرم افزار نهفته به ؟؟؟؟ مراجعه کنید.

## قابلیت ها
- قابلیت اجرای کد با دوره های زمانی مختلف در مقیاس میکروثانیه، میلی ثانیه و ثانیه
- قابلیت اجرای کد با ایجاد Prescaler نسبت به عنصر اجرایی اصلی

## چگونه استفاده کنید
- مخزن را کلون کرده و فایل runtime_scaler.h را به پروژه خود اضافه کنید.
- حالا ماژول آماده استفاده است.
- در فایل فایل h اطلاعات کامل در مورد نحوه استفاده از ماژول نوشته شده است.
- در زیر نحوه استفاده از ماکروهای مختلف ماژول runtime_scaler  در مقیاس میلی ثانیه نوشته شده است. نحوه استفاده از بقیه مقیاس های زمانی مشابه یکدیگر است.
```c

//Example
while(1)
{
	//func1() runs every 100ms
	RUN_EVERY_MS_(func1, 100)
	{
		func1();
		RUN_END_;
	}

	//func2() runs every 200ms
	RUN_EVERY_MS_(func2, 200)
	{
		func2();
		RUN_END_;
	}

	//func3() runs every 5th iteration while the while(1) loop is running
	RUN_EVERY_QTY_(func3, 5)
	{
		func3();
		RUN_END_;
	}
}

```
## شروع استفاده
برای کلون کردن ماژول runtime_scaler می توانید از دستور زیر استفاده کنید : 
```bash
git clone <ssh code>
```
## وابستگی ها
ماژول runtime_scaler برای کار کردن نیاز به ماژول کرونو دارد.

## پلتفرم های پشتیبانی شده
ماژول runtime_scaler در زبان های ++C/C قابل استفاده بوده و به هیچ میکروکنترلر خاصی وابستگی ندارد.
## مثال ها
در مخزن، فولدری به نام example وجود دارد. در این فولدر مثالی در محیط Keil IDE و بر روی بورد Nucleo-L432KC تعریف شده است که استفاده از قابلیت های مختلف ماژول runtime_scaler در آن نشان داده شده است.
در این مثال از تیک سخت افزاری بوسیله یک تایمر 32 بیتی برای راه اندازی ماژول کرونو (به عنوان پیش نیاز) استفاده شده است.
## مستندات
- در فولدر doc راهنمای API های ماژول runtime_scaler ارائه شده است.
- در ابتدای فایل h راهنمای کامل نحوه استفاده از ماژول runtime_scaler نوشته شده است.
- در فولدر example مثالی برای استفاده از ماژول runtime_scaler موجود است.
- در ؟؟؟ مطلبی در مورد مبانی زمان بندی در نرم افزار نهفته موجود است. 

## محدودیت ها
دقت اجرای زمان بندی ها بستگی به اختلاف مقیاس زمان بندی های مورد نیاز و زمان اجرای عنصر اجرایی مادر دارد.
