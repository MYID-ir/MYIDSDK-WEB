![](myid_logo.png)

**راهنمایWEB SDK مای آیدی**

**نسخه 1.0**

برای استفاده از WEB SDK مای آیدی مراحل زیر را در پروژه‌ی خود اعمال کنید:

**بخش اول نصب برروی پروژه : **

1.  فایل‌ [myid-web.zip](https://cdn.myid.ir/sdk/myid-web.zip) را دانلود
    کرده .

2.  فایل های مربوط به پوشه js را در پروژه خود اضافه کنید .

&lt;script src="js/hico.js"&gt;&lt;/script&gt;\
&lt;script src="js/hire.js"&gt;&lt;/script&gt;\
&lt;script src="js/data.js"&gt;&lt;/script&gt;\
&lt;script src="js/hilz.js"&gt;&lt;/script&gt;

فایل data.js باز کنید و توکن دریافتی خود را وارد نمایید.

var ***pk*** = 'TOKEN';

[راهنمای دریافت توکن](#TOKEN)

فایل site.css به پروژه خود اضافه کنید .

&lt;link href="css/site.css" rel="stylesheet"/&gt;

&lt;div class="live-container" id="liveness-here"&gt;&lt;/div&gt;\
&lt;script type="text/javascript"&gt;\
plive('liveness-here',\
{\
url: "https://service.myid.ir/api/v1/service/websdk",\
language: "fa",\
method: "normal", // photoID

userId: "1020304050",\
styles: {\
\
srcImage\_logo: 'https://cdn.myid.ir/public/logo-myid.png'\
},\
additional: \[\
{name: "Authorization", value: "APIKEY"},\
\]\
},\
function (isOK, code, message) {\
if (isOK)\
***document***.getElementById("status").innerHTML = "احراز انجام شد و
صحیح است.";\
else\
***document***.getElementById("status").innerHTML = "احراز انجام شد و
صحیح نیست." + code + ': ' + message;\
}\
)\
&lt;/script&gt;

متد plive را فراخوانی کرده liveness-here نام آیدی باکس دلخواه شما برای
لود شدن احراز میباشد.

در این قسمت APIKEY خود را وارد نمایید.

{name: "Authorization", value: "APIKEY"},

در صورتی که میخواهید از liveness استفاده کنید

Method را برابر normal و برای سرویس تطابق چهره برابر photoID قرار دهید

<span id="TOKEN" class="anchor"></span>**دریافت توکن: **

برای دریافت TOKEN باید در برنامه تابع زیر را صدا بزنید

توجه داشته باشید که تاریخ انقضای token سی روزه می باشد و باید هر سی روز
یک توکن جدید دریافت کنید.

آدرس ارسالی : http://service.myid.ir/api/v1/token

پارامتر های ارسالی :

نام             توضیحات
  --------------- -----------------------------------------------------------------------------------------------
Authorization   شما میتوانید KEY را از پنل مای آیدی خود در بخش api توسعه دهندگان برای پروژه خود ایجاد نمایید.

پارامتر های دریافتی :

نام             توضیحات
  --------------- -------------------------------------
package\_name   نام پکیج ثبت شده شما در لیست api ها
Token           تو کن قابل استفاده
expired\_at     زمان انقضای توکن
