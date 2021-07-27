![](RackMultipart20210727-4-urx4df_html_f72a2a50906a1676.png)

**راهنمای**** WEB SDK **** مای آیدی**

**نسخه**  **1.0**

**مقدمه**  **:**

برای استفاده از WEB SDK مای آیدی در وب سایت خود باید ابتدا فایل های مربوطه را در پروژه خود اضافه کرده سپس فانکشن مختص به لود شدن sdk را صدا بزنید.

جهت رفع هرگونه مشکل و یا پرسش با پشتیبانی در تماس باشید.

**بخش اول نصب برروی پروژه**  **:**

1. فایل sdk مای آیدی را از آدرس‌ [myid-web.zip](https://cdn.myid.ir/sdk/myid-web.zip)دانلود کنید.

1. افزودن فایل ها :

فایل site.css در فولدر css را به پروژه خود اضافه کنید . این فایل برای اضافه شدن استایل sdk می باشد.

\&lt;link href=&quot;css/site.css&quot; rel=&quot;stylesheet&quot;/\&gt;

فایل های مربوط به پوشه js را در پروژه خود اضافه کنید .

\&lt;script src=&quot;js/hilz.js&quot;\&gt;\&lt;/script\&gt;
\&lt;script src=&quot;js/hico.js&quot;\&gt;\&lt;/script\&gt;

دو فایل hilz.js و hico.jsمربوط به لود شدن sdk و فرایند اتصال به ماژول هوش مصنوعی هستند.

توجه داشته باشید فایل Present.wasm حتماً باید در کنار فایل های جاوا اسکریپت و در فولدر js باشد.

1. **دریافت توکن**** :**

ابتدا قبل از شروع استفاده شما باید توکن sdk را دریافت کنید .

جهت [راهنمای دریافت توکن](#TOKEN)[کلیک کنید](#TOKEN)[.](#TOKEN)

برای انجام عملیات متد plive را فراخوانی کرده.

پالامتر اول متد نام آیدی تگ html هست که میخواهید در آن sdk نمایش داده شود.

در مثال پایین liveness-here نام آیدی باکس دلخواه شما برای لود شدن احراز میباشد.

پارامتر های دومین ورودی متد:

| **نام پارامتر** | **Values** | **توضیحات** |
| --- | --- | --- |
| **sdkKey** |
| توکن دریافتی در بخش 3 **دریافت توکن** |
| **apiKey** |
| از طرف مای آیدی برای شما ارسال شده است.بر اساس هر دامین نیاز به یک کی مجزا می باشد. |
| **referenceId** |
| کد یکتا برای شناسایی احراز از سمت شما |
| **Method** | Normal / photoID | استفاده برای لایونس یا مچینگ تصاویر |
| **url** |
| ادرس وب سرویس مای ایدی و همیشه در همین آدرس میماند. |
| **language** | fa/en | برای تعیین زبان sdk / فارسی یا انگلیسی |
| **Styles srcImage** | آدرس یک تصویر | می توانید لوگوی خود را بجای لوگوی مای آیدی نمایش دهید. |

\&lt;div class=&quot;live-container&quot; id=&quot;liveness-here&quot;\&gt;\&lt;/div\&gt;

\&lt;script type=&quot;text/javascript&quot;\&gt;
plive(&#39;liveness-here&#39;,
{
url: &quot;https://service.myid.ir/api/v1/service/websdk&quot;,
language: &quot;fa&quot;,
method: &quot;normal&quot;,
owner: &quot;MyID&quot;,

styles: {
// bgColor\_form: &#39;red&#39;,
// bgColor\_btn: &#39;black&#39;,
// txtColor\_btn: &#39;white&#39;,
// txtColor\_form: &#39;yellow&#39;,
srcImage\_logo: &#39;https://cdn.myid.ir/public/logo-myid.png&#39;
},
additional: [
{name: &quot;Authorization&quot;, value: &quot;VtfZpRWLQLBoGkUAG2Ur0PEiDihjRADIAilioMsb1MIwKyeq49vukiIYnrds&quot;},
{name: &quot;x-reference&quot;, value: &#39;MD-&#39;+Math.round(new Date().getTime()/1000)},
]
},
function (isOK, code, message) {
console.log(code);
console.log(message);
//if (isOK)
//document.getElementById(&quot;status&quot;).innerHTML = &quot;احراز انجام شد و صحیح است.&quot;;
//else
//document.getElementById(&quot;status&quot;).innerHTML = &quot;احراز انجام شد و صحیح نیست.&quot; + code + &#39;: &#39; + message;

return ;
}
)
\&lt;/script\&gt;

پارامتر های خروجی callback

| **نام پارامتر** | **نوع خروجی** | **توضیحات** |
| --- | --- | --- |
| **isOK** | boolean | در صورت صحیح بودن لایونس True و در غیر اینصورت false بر گردانده میشود. |
| **code** | Int | کد خطا در صورت صحیح بودن 200 برگردانده میشود. |
| **message** | String | متن خطا |

کد های خطا :

| **StatusCode** | **توضیحات** |
| --- | --- |
| **200** | احراز هویت با موفقیت انجام ش د |
| **441** | فیلد dataدرخواست خالی است |
| **491** | اجرای سرویس برای دامنه مبدا مجاز نیست |
| **442** | فیلد dataمقدار درست ندارد |
| **452** | فیلد فایل درخواست خالی است |
| **480** | حجم فایل ارسالی بیش از حد مجاز است |
| **453** | نوع فایل ارسالی مجاز نیست |
| **458** | فایل دارای رمزنگاری معتبر نیست |
| **472** | تصویری برای کاربر یافت نش د |
| **459** | در بررسی حقیقی بودن ویدئو مشکلی بوجود آمد ه |
| **401** | ویدئو ارسالی جعلی تشخیص داده شد ه |
| **202** | طول ویدئو کمتر از حد مجاز است |
| **203** | طول ویدئو جهت بررسی کیفیت تصویر کمتر از حد مجاز اس ت |
| **457** | در ارتباط با بانک اطلاعاتی مشکل پیش آمد ه |

**دریافت توکن**** :**

برای دریافت TOKEN باید در برنامه تابع زیر را صدا بزنید

توجه داشته باشید که تاریخ انقضای tokenسی روزه می باشد و باید هر سی روز یک توکن جدید دریافت کنید.

آدرس ارسالی : [http://service.myid.ir/api/v1/token](http://service.myid.ir/api/v1/token)

پارامتر های ارسالی :

| **نام** | **توضیحات** |
| --- | --- |
| **Authorization** | شما میتوانید KEY را از پنل مای آیدی خود در بخش apiتوسعه دهندگان برای پروژه خود ایجاد نمایید. |

پارامتر های دریافتی :

| **نام** | **توضیحات** |
| --- | --- |
| **package\_name** | نام پکیج ثبت شده شما در لیست api ها |
| **Token** | تو کن قابل استفاده |
| **expired\_at** | زمان انقضای توکن |

5

[MYID.IR](http://MYID.IR/)
