![Logo](images/Logo.png)

# ماژول runtime_scaler
این ماژول ابزارهایی را برای [زمان بندی نرم افزار نهفته](doc/%D8%B2%D9%85%D8%A7%D9%86%20%D8%A8%D9%86%D8%AF%DB%8C%20%D9%86%D8%B1%D9%85%20%D8%A7%D9%81%D8%B2%D8%A7%D8%B1%20%D9%86%D9%87%D9%81%D8%AA%D9%87.md) ارائه می دهد
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
## استانداردها
این ماژول سازگار با استاندارد MISRA C:2012 نوشته شده است. توضیحات بیشتر در این مورد در [اینجا](MISRA.md) ارائه شده است.
## مستندات
- در فولدر doc راهنمای API های ماژول runtime_scaler ارائه شده است.
- در ابتدای فایل h راهنمای کامل نحوه استفاده از ماژول runtime_scaler نوشته شده است.
- در [زمان بندی در نرم افزار نهفته](doc/%D8%B2%D9%85%D8%A7%D9%86%20%D8%A8%D9%86%D8%AF%DB%8C%20%D9%86%D8%B1%D9%85%20%D8%A7%D9%81%D8%B2%D8%A7%D8%B1%20%D9%86%D9%87%D9%81%D8%AA%D9%87.md) مطلبی در مورد مبانی زمان بندی در نرم افزار نهفته موجود است. 

## محدودیت ها
دقت اجرای زمان بندی ها بستگی به اختلاف مقیاس زمان بندی های مورد نیاز و زمان اجرای عنصر اجرایی مادر دارد.

## مطالب مرتبط
- [ماژول کرونو](https://github.com/faraabin/chrono)
