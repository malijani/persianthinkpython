# فصل ۱۲

تاپل (tuple)

تاپل یک دنباله از مقدار هاست. مقدارها می توانند از هر نوعی باشند، و
بوسیله اعداد صحیح شماره گذاری می‌شوند، بنابراین با این حساب تاپل ها
بسیار شبیه به لیست‌ها هستند. تفاوت مهم بین تاپل و لیست غیر قابل تغییر
بودن آنهاست.

به صورت نحوی یک تاپل لیستی از مقدارهای جدا شده توسط کاما است:

&gt;&gt;&gt; t = ‘a’, ‘b’, ‘c’, ‘d’, ‘e’

اگرچه اجباری نیست ولی قرار دادن تاپل بین پرانتز متداول است:

&gt;&gt;&gt; t = ( ‘a’, ‘b’, ‘c’, ‘d’, ‘e’ )

برای ساختن یک تاپل بصورت تک عنصری باید یک کاما در انتها استفاده کرد:

&gt;&gt;&gt; t1 = ‘a’,

&gt;&gt;&gt; type(t1)

&lt;type ‘tuple’&gt;

یک مقدار به صورت تک عنصری داخل پرانتز تاپل محسوب نمی‌شود:

&gt;&gt;&gt; t2 = (‘a’)

&gt;&gt;&gt; type(t2)

&lt;type ‘str’&gt;

یک راه دیگر برای ایجاد تاپل استفاده از تابع درون سازی شده tuple است.
بدون آرگومان این تابع یک تاپل خالی می‌سازد:

&gt;&gt;&gt; t = tuple()

&gt;&gt;&gt; print t

()

اگر آرگومان یک دنباله‌ (رشته، لیست یا تاپل) باشد، نتیجه یک تاپل با عناصر
دنباله است:

&gt;&gt;&gt; t = tuple(‘lupins’)

&gt;&gt;&gt; print t

(‘l’, ‘u’, ‘p’, ‘i’, ‘n’, ‘s’)

از آنجایی که tuple یک تابع درون سازی شده است از استفاده آن به عنوان نام
متغییر خودداری کنید.

اغلب عمگرهای لیست بر روی تاپل نیز کار می‌کنند. عمگر براکت شاخص یک عنصر
را مشخص می‌کند:

&gt;&gt;&gt; t = (‘a’, ‘b’, ‘c’, ‘d’, ‘e’)

&gt;&gt;&gt; print t\[0\]

‘a’

عمگر برش (slice Operator) یک بازه ای از عناصر را انتخاب می‌کند:

&gt;&gt;&gt; print t\[1:3\]

(‘b’, ‘c’)

اما اگر سعی کنید یکی از عناصر تاپل را تغییر دهید خطا دریافت خواهید کرد:

&gt;&gt;&gt; t\[0\] = ‘A’

TypeError: object doesn't support item assignment

نمی‌توانید یک عنصر از تاپل را تغییر دهید ولی در عوض می توانید یک تاپل را
با یک تاپل دیگر جایگزین کنید:

&gt;&gt;&gt; t = (‘A’,) + t\[1:\]

&gt;&gt;&gt; print t

(‘A’, ‘b’, ‘c’, ‘d’, ‘e’)

۱۲.۲ انتصاب تاپلی

معمولا بسیار مفید است که مقدار دو متغییر را جابه‌جا کنیم. در انتصاب‌های
رایج باید از یک متغییر موقت استفاده کنید. برای مثال برای جابه‌جای a و b:

&gt;&gt;&gt; temp = a

&gt;&gt;&gt; a = b

&gt;&gt;&gt; b = temp

این روش سخت است در حالی که **انتصاب تاپلی **زیبا تر است:

&gt;&gt;&gt; a, b = b, a

بخش چپ یک تاپل از متغییرهاست، بخش راست یک تاپل از عبارات. هر مقدار به
متغییر مربوطه انتصاب داده می‌شود. همه عبارات در سمت راست قبل از انتصاب
ارزیابی می‌شوند.

تعداد متغییرها در سمت چپ و تعداد مقدارها در سمت راست باید برابر باشند:

&gt;&gt;&gt; a, b = 1, 2, 3

ValueError: too many values to unpack

به طور عمومی تر بخش سمت راست می‌تواند هر نوعی از دنباله (رشته، لیست یا
تاپل) باشد. برای مثال برای دو نیم کردن یک ادرس ایمیل به نام کاربری و
دامنه باید نوشت:

&gt;&gt;&gt; addr =
‘[*monty*](mailto:monty@python.org)[*@*](mailto:monty@python.org)[*python*](mailto:monty@python.org)[*.*](mailto:monty@python.org)[*org*](mailto:monty@python.org)’

&gt;&gt;&gt; uname, domain = addr.split(‘@’)

مقدار بازگشتی از split یک لیست با دو عنصر است که عنصر اول به uname و
دومی به domin منتصب می‌گردد.

&gt;&gt;&gt; print uname

monty

&gt;&gt;&gt; print domain

python.org

۱۲.۳ تاپل به عنوان مقدار بازگشتی

موکدا گفته شد که یک تابع فقط یک مقدار می‌تواند برگرداند، اما اگر مقدار
یک تاپل باشد نتیجه همانند بازگشت چند مقداری است. برای مثال اگر بخواهید
دو عدد صحیح را تقسیم کنید و مقدار خارج قسمت و باقی مانده را محاسبه کنید،
بهتر است بجای اینکه ابتدا x/y و بعد x%y را حساب کنیم هر دو را باهم
محاسبه کنیم.

تابع درون سازی شد divmod دو آرگان می‌گیرد و یک مقدار تاپل متشکل از دو
مقدار خارج قسمت و باقی مانده را بر می‌گرداند. می‌توانید نتایج را به صورت
یک تاپل ذخیره کنید:

&gt;&gt;&gt; t = divmod(7, 3)

&gt;&gt;&gt; print t

(2, 1)

یا از انتصاب تاپلی برای ذخیره بطور جداگانه استفاده کنید:

&gt;&gt;&gt; quot, rem = divmod(7, 3)

&gt;&gt;&gt; print quot

2

&gt;&gt;&gt; print rem

1

نمونه ای از یک تابع که یک تاپل بر می‌گرداند:

def min\_max(t):

return min(t), max(t)

max و min توابع درون سازی هستند که بزرگترین و کوچکترن عنصر یک دنباله را
پیدا می‌کنند.

تابع min\_max هر دو را محاسبه و بصورت یک تاپل رو مقداری بر می‌گرداند.

۱۲.۴ آرگومان های تاپلی به طول متغییر

توابع می‌توانند تعداد متغییری از آرگومان ها را بگیرند. یک نام پارامتر که
با \* شروع شود آرگومان ها را **جمع آوری کرده** و در یک تاپل می‌ریزد.
برای مثال printall هر تعدادی آرگومان دریافت می‌کند و همه را چاپ می‌کند:

def printall(\*arg):

print args

برای پارامتر جمع آوری کننده می‌توانید هر نامی که دوست دارید انتخاب کنید،
اما args متعارف است. تابع به صورت زیر کار می‌کند:

&gt;&gt;&gt; printall(1, 2.0, ’3’)

(1, 2.0, ‘3’)

مکمل جمع آوری کننده، **پخش کننده** است. اگر یک دنباله از مقدارها داشته
باشیم و بخواهیم که به عنوان یک مجموعه ورودی‌ها به یک تابع ارسال کنیم\*
می‌توان از عملگر \* استفاده کرد برای مثال divmod دقیقا دو ورودی می‌گیرد،
با یک تاپل به عنوان ورودی کار نمی‌کند:

&gt;&gt;&gt; t = (7, 3)

&gt;&gt;&gt; divmod(t)

TypeError: divmod expected 2 arguments, got 1

اما اگر تاپل را پخش کنید کار می‌کند:

&gt;&gt;&gt; divmod(\*t)

(2, 1)

**تمرین ۱۲.۱: **بسیاری از توابع درون سازی شده از آرگومان‌های تاپلی به
طول متغییر استفاده می‌کنند برای مثال max و min می‌توانند هر تعدادی از
رورودی را دریافت کنند:

&gt;&gt;&gt; max(1, 2, 3)

3

اما sum نمی‌تواند:

&gt;&gt;&gt; sum(1, 2, 3)

TypeError: sum expected at most 2 arguments, got 3

یک تابع بنویسید به نام sumall که هر تعدادی از ورودی را دریافت کرده و جمع
آنها را برگرداند.

**۱۲.۵ لیست‌ها و تاپل‌ها**

تابع zip یک تابع درون سازی شده است که دو یا بیشتر دنباله را گرفته و در
یک لیستی از از تاپل‌ها که هر تاپل شامل یک عنصر از رشته است "فشرده"
می‌کند. در پایتون ۳ zip یک iterator از تاپل‌ها را بر می‌گرداند، برای
اغلب اهداف iterator مانند یک لیست رفتار می‌کند.

بک نمونه فشرده شده از یک رشته و یک لیست:

&gt;&gt;&gt; s = ‘abc’

&gt;&gt;&gt; t = \[0, 1, 2\]

&gt;&gt;&gt; zip(s, t)

\[(‘a’, 0), (‘b’, 1), (‘c’, 2)\]

نتیجه یک لیست از تاپل‌ها است که هر تاپل شامل یک کاراکتر از رشته و عنصر
متناضر آن از لیست است.

اگر دنباله ها طول یکسان نداشته باشند، نتیجه هم اندازه دنباله با طول
کوچکتر خواهد بود.

&gt;&gt;&gt; zip(‘Anne’, ‘Elk’)

\[(‘A’, ‘E’), (‘n’, ‘l’), (‘n’, ‘k’)\]

می‌توانید از انتصاب تاپلی در یک حلقه for برای پیمایش یک لیست از تاپل‌ها
استفاده کنید:

t = \[(‘1’, 0), (‘b’, 1), (‘c’, 2)\]

for letter, number in t:

print number, letter

هر بار که حلقه اجرا می‌شود، پایتون تاپل بعدی در لیست را انتخاب می‌کند و
عناصر آن را به letter و number نسبت می‌دهد. خروجی حلقه به شکل زیر است:

0 a

1 b

2 c

اگر zip، for و انتصاب تاپلی را ترکیب کنید، یک چیز کاربردی برای پیمایش دو
(یا بیشتر) دنباله در یک زمان بدست می‌آورید. برای مثال has\_match دو
دنباله‌ t1 و t2 را گرفته و مقدار true را درصورتی که بر میگردانند به شرطی
که شاخص i ای وجود داشته باشد که به ازای آن داشته باشیم t1\[i\]==
t2\[i\]:

def has\_match(t1, t2):

for x, y in zip(t1, t2):

if x == y:

return True

return False

اگر نیاز دارید که عناصر یک دنباله و شاخص‌های آن را پیمایش کنید،
می‌توانید از تابع درون سازی شده enumerate استفاده کنید:

for index, element in enumerate(‘abc’):

print index, element

خروجی این حلقه بصورت زیر است:

0 a

1 b

2 c

**۱۲.۶ دیکشنری‌ها و تاپل‌ها**

دیکشنری‌ها متدی بنام item دارند که لیستی از تاپل‌ها را برمی‌گرداند بطوری
که هر تاپل یک جفت کلید-مقدار است.

&gt;&gt;&gt; d = {‘a’:0, ‘b’:1, ‘c’:2}

&gt;&gt;&gt; t = d.items()

&gt;&gt;&gt; print t

\[(‘a’, 0), (‘c’, 2), (‘b’, 1)\]

همان طوری که از دیکشنری انتظار می‌رود هیچ ترتیب خاصی در آن وجود ندارد.
در پایتون ۳ items یک iterator برمی‌گرداند، برای اغلب اهداف iterator
مانند یک لیست رفتار می‌کند.

از طرف دیگر می‌توانید از یک لیست برای مقدار دهی اولیه یک دیکشنری جدید
استفاده کنید:

&gt;&gt;&gt; t = \[(‘a’, 0), (‘c’, 2), (‘b’, 1)\]

&gt;&gt;&gt; d = dict(t)

&gt;&gt;&gt; print d

{‘a’:0, ‘c’:2, ‘b’:1}

ترکیب dict با zip یک راه دقیق برای ایجاد دیکشنری نتیجه می‌دهد:

&gt;&gt;&gt; d = dict(zip(‘abc’, range(3))

&gt;&gt;&gt; print d

{'a':0, 'b':1, 'c':2}

همچنین متد update دیکشنری یک لیستی از تاپل ها را گرفته و به صورت جفت
کلید-مقدار به انتهای آنها اضافه می‌کند:

for key, val in d.items():\
print val, key

خروجی حلقه به صورت زیر است:

0 a

1 c

2 b

استفاده از تاپل به عنوان کلید در دیکشنری متداول است ( در درجه اول چون
نمی‌توان از لیست استفاده کرد). برای مثال یک دفترچه تلفن احتمالا بصورت
نگاشت جفت نام خوانوادگی، نام به شماره تلفن در نظر گرفته شده. فرض کنید ما
last و first و number را تعریف کردیم، می‌توان نوشت:

directory\[last, first\] = number

عبارت داخل براکت یک تاپل است. می‌توان از انتصاب تاپلی برای پیمایش این
دفتر تلفن استفاده کرد.

for last, first in directory:\
print first, last, directory\[last,first\]

این حلقه کلیدها را در دیکشنری پیمایش می‌کند، که تاپل هستند. هر عنصر از
هر تاپلی را به last و first نسبت می‌دهد سپس نام و شماره تلفن مربوط به آن
را چاپ می‌کند.

دو روش برای نمایش تاپل در دیاگرام حالت وجود دارد. نسخه مفصل تر شاخص‌ها و
عناصر را بصورتی که در یک لیست ظاهر می‌شوند نمایش داده شده. برای مثال
تاپل ('Cleese', 'John') در شکل ۱۲.۲ شاهر شده.

اما در یک دیاگارم بزرگتر احتمالا می‌خواهید که جزییات را رها کنید. برای
مثال دیاگرام دفترچه تلفن به شکل ۱۲.۱ ظاهر می‌شود.

اینجا تاپل‌ها با استفاده از نحو پایتون به صورت مختصر نویسی گرافیکی نمایش
داده شده‌اند.

شماره تلفن استفاده شده در این دیاگرام شماره شکایات بی بی سی است به همین
خاطر لطفا زنگ نزنید.

**۱۲.۷ مقایسه تاپل‌ها**

اوپراتورهای رابطه‌ای بر روی تاپل‌ها و بقیه دنباله‌ها کار می‌کنند. پایتون
مقایسه را با اولین عنصر از هر دنباله شروع می‌کند. اگر برابر بودند عنصر
بعدی چک می‌شود و به همین ترتیب ادامه پیدا می‌کند تا زمانی که اولین عنصر
متفاوت پیدا شود. عناصر بعدی در نظر گرفته نمی‌شوند (حتی اگر خیلی بزرگتر
باشند).

&gt;&gt;&gt; (0, 1, 2) &lt; (0, 3, 4)

True

&gt;&gt;&gt; (0, 1, 2000000) &lt; (0, 3, 4)

True

تابع sort نیز همانگونه عمل می کند. در درجه ی اول بر اساس عنصر اول اقدام
به مرتب کردن می نماید، اما در صورت یکسانی کلمات، بر اساس عنصر دوم مرتب
می کند و به همین ترتیب ادامه می دهد.

این ویژگی خود را به یک الگو به نام DSU به شکل زیر تعریف می‌کند:

Decorate: تزیین کردن یک دنباله بوسیله ساختن لیستی از تاپل‌ها با یک یا
بیشتر کلیدهای مرتب شده که در پی عناصر دنباله می‌ایند.

Sort: لیستی از تاپل ها

Undecorate: استخراج عناصر مرتب شده از دنباله

برای مثال فرض کنید یک لیست از کلمات دارید و می‌خواهید به ترتیب از طولانی
ترین نا کوتاه ترین آنها را مرتب کنید:

def sort\_by\_lenght(words):

t = \[\]

for word in words:

t.append((len(word), word))

t.sort(reverse=True)

res = \[\]

for length, word in t:

res.append(word)

return res

اولین حلقه لیستی از تاپل ها می‌سازد که هر تاپل یک کلمه است که در پی
اندازه طولش می‌آید.

تابع sort طول اولین عنصر را مقایسه می‌کند و فقط در صورتی عنصر دوم را در
نظر می‌گیرد که برابر باشند. کلمه کلیدی ورودی reverse=True به sort
می‌گویید به ترتیب کم شدن عمل کند.

حلقه دوم لیست تاپل ها را پیمایش کرده و یک لیست از کلمات به صورت نزولی از
طولشان می‌سازد.

**تمرین ۱۲.۲: **در این مثال با مقایسه کلمات مشکل برابری حل شد، به این
شکل که کلمات با طول یکسان بر اساس حروف الفبا به صورت برعکس مرتب می‌شدند.
برای یک برنامه دیگه ممکنه بخواهید که بصورت تصادفی مرتب بشوند. این مثال
را به گونه ای تغییر بدهید که کلمات با طول یکسان به صورت تصادفی مرتب
شوند. راهنمایی: تابع random در ماژول random را نگاه کنید. جواب:
http://thinkpython.com/code/unstable\_ sort.py

**۱۲.۸ دنباله‌ای از دنباله‌ها**

من بیشتر روی لیستی از تاپل‌ها متمرکز شدم درحالی که همه مثال های این فصل
روی لیستی از لیست‌ها نیز کار می‌کنند. برای فرار کردن از شمارش ترکیب‌های
احتمالی، بعضی وقت‌ها استفاده از لیستی از لیست‌ها ساده تر است.

در بسیاری از موارد می‌توان انواع دنباله‌ها (رشته، لیست، تاپل) را به جای
یکدیگر استفاده کرد. پس چرا و چطور ما یکی را از بین بقیه انتخاب کنیم؟

برای شروع واضح است که رشته‌ها محدودتر از بقیه دنباله‌ها هستند چون که فقط
می توانند حروف را بپذیرند. همچنین غیر قابل تغییر هستند. اگر بخواهید
توانایی تغییر کاراکترها را در رشته داشته باشید ( نه ایجاد یک رشته جدید
)، احتمالا از یک لیست از کاراکترها استفاده خواهید کرد.

استفاده از لیست خیلی متداول تر از تاپل است، بیشتر چون قابل تغییر هستند.
اما موارد کمی هستند که تاپل را ترجیح خواهید داد:

1.  در بعضی موارد مانند جمله return بصورت نخوی ساده تر است که یک تاپل
    ایجاد کنیم تا یک لیست. در بقیه موارد احتمالا لیست را ترجیح
    خواهید داد.
2.  اگر بخواهید از یک دنباله به عنوان کلید دیکشنری استفاده کنید باید از
    یک نوع غیرقابل تغییر مثل تاپل یا لیست استفاده کنید.
3.  اگر یک دنباله را به عنوان ورودی برای یک تابع می‌فرستید، استفاده از
    تاپل پتانسیل رخداد رفتار غیر منتظره را جاهش می‌دهد.

چون تاپل‌ها غیرقابل تغییر هستند، متدهایی مثل sort و reverse را فراهم
نمی‌کند در حالی که در لیست وجود دارند. اما پایتون توابع درونسازی شده
sorted و reversed را فراهم کرده که که هر نوع دنباله ای را به عنوان
پارامتر گرفته و یک لیست جدید با همان عناصر اما با ترتیب متفاوتی بر
می‌گرداند.

**۱۲.۹ خطایابی**

لیست‌ها، تاپل‌ها و دیکشنری‌ها بطور عمومی به عنوان **ساختمان داده**
شناخته می‌شوند. در این فصل ساختمان‌های داده‌ای ترکیبی‌ای دیدیم مثل لیستی
از تاپل‌ها و دیکشنری‌ها که شامل تاپل به عنوان کیلد و لیست به عنوان مقدار
بودند. ساختمان‌های داده‌ای ترکیبی کاربردی هستند اما مستعد چیزی هستند که
من به آنها shape error می‌گویم. که خطاهایی هستند که وقتی یک ساختمان
داده‌ای نوع، اندازه یا ترکیب اشتباه دارد رخ می‌دهند. برای مثال اگر شما
انتظار یک لیست با یک عدد صحیح را داشته باشید و من یک عدد صحیح ساده بدهم
( نه در داخل یک لیست )، کار نخواهد کرد.

برای کمک به خطایابی این نوع از خطاها، یک ماژول به نام structshape نوشتم
که یک تابع به نام structshape فراهم می‌کند که هر نوعی از ساختمان داده‌ای
را به عنوان ورودی دریافت کرده و یک خلاصه از ساختار ان بصورت رشته باز
می‌گرداند. می‌تواند از ادرس زیر آن را دریافت کنید:
[*http*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*://*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*www*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*.*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*greenteapress*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*.*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*com*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*/*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*thinkpython*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*/*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*code*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*/*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*structshape*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*.*](http://www.greenteapress.com/thinkpython/code/structshape.py)[*py*](http://www.greenteapress.com/thinkpython/code/structshape.py)

یک مثال از نتیجه یک لیست ساده:

&gt;&gt;&gt; from structshape import structshape

&gt;&gt;&gt; t = \[1, 2, 3\]

&gt;&gt;&gt; print structshape(t)

list if 3 int

یک برنامه بهتر احتمالا باید می‌نوشت "list of 3 ints" ولی درگیر صیغه جمع
نشدن ساده تر است.

یک نمونه از لیستی از لیست‌ها:

&gt;&gt;&gt; t2 = \[\[1, 2\], \[3, 4\], \[5, 6\]\]

&gt;&gt;&gt; print structshape(t2)

list of 3 list of 2 int

اگر عناصر لیست از یک نوع نباشند structshape بر اساس نوعشان گروه بندی می
کند:

&gt;&gt;&gt; t3 = \[1, 2, 3, 4.0, ‘5’, ‘6’, \[7\], \[8\], 9\]

&gt;&gt;&gt;print structshape(t3)

list of (3 int, float, 2 str, 2 list of int, int)

یکن نمونه از تاپل:

&gt;&gt;&gt; s = ‘abc’

&gt;&gt;&gt; lt = zip(t, s)

&gt;&gt;&gt; print structshape(lt)

list of 3 tuple of (int, str)

و یک نمونه دیکشنری که به صورت عدد صحیح به رشته ساخته شده:

&gt;&gt;&gt; d = dict(lt)

&gt;&gt;&gt; print structshape(d)

 dict of 3 int -&gt; str

اگر با پیگیری ساختمان داده‌ای خودتان مشکل دارید structshape می‌تواند کمک
کند.

**۱۲.۱۰ واژه نامه**

**تاپل (tuple):** یک دنباله غیر قابل تغییر از عناصر

**انتصاب تاپلی (tuple assignment):** یک انتصاب با یک دنباله در سمت راست
و سک تاپل از متغییر ها در سمت چپ. سمت راست ارزش گذاری شده و سپس عناصر ان
به متغییرهای سمت چپ منتصب می‌شوند.

**جمع آوری کننده (gather):** عمل سرهم کردن یک ورودی تاپلی با طول متغییر

**پخش کننده (scatter):** عمل تلقی کردن یک دنباله به عنوان لیستی از
ورودی‌ها

**DSU:** اختصار "decorate-sort-undecorate"، یک الگو شامل ساخت یک لیست از
تاپل‌ها، مرتب کردن و استخراج نتایج است.

**ساختمان داده (data structure):** یک مجموعه از مقدارهای مرتبط که اغلب
به صورت لیست، دیکشنری، تاپل و غیره هستند.

**شکل ساختمان داده (shape of data structure):** یک خلاصه از نوع، اندازه
و ترکیب ساختمان داده.

**۱۲.۱۱ تمرین ها**

**تمرین ۳**

تابعی بنویسید به اسم most\_frequent که یک رشته را به عنوان ورودی میگیرد
و به ترتیب فراوانی حروف آنها را چاپ کند. چند رشته از زبان های مختلفی
پیدا کنید و ببینید که فراوانی حروف در زبان های مختلف به چه شکل است.
نتیجه هایی که بدست آورده‌اید را با جدول های موحود در اینجا مقایسه کنید.
[*http*](http://en.wikipedia.org/wiki/Letter_frequencies)[*://*](http://en.wikipedia.org/wiki/Letter_frequencies)[*en*](http://en.wikipedia.org/wiki/Letter_frequencies)[*.*](http://en.wikipedia.org/wiki/Letter_frequencies)[*wikipedia*](http://en.wikipedia.org/wiki/Letter_frequencies)[*.*](http://en.wikipedia.org/wiki/Letter_frequencies)[*org*](http://en.wikipedia.org/wiki/Letter_frequencies)[*/*](http://en.wikipedia.org/wiki/Letter_frequencies)[*wiki*](http://en.wikipedia.org/wiki/Letter_frequencies)[*/*](http://en.wikipedia.org/wiki/Letter_frequencies)[*Letter*](http://en.wikipedia.org/wiki/Letter_frequencies)[*\_*](http://en.wikipedia.org/wiki/Letter_frequencies)[*frequencies*](http://en.wikipedia.org/wiki/Letter_frequencies)
راه‌حل:
[*http*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*://*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*www*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*.*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*greenteapress*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*.*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*com*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*/*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*thinkpython*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*/*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*code*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*/*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*most*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*\_*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*frequent*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*.*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)[*py*](http://www.greenteapress.com/thinkpython/code/most_frequent.py)

**تمرین ۴ **و باز هم آناگرام

1.  برنامه‌ای بنویسید که لیست لغات موجود در یک فایل را بگیرد (قسمت ۹.۱)
    و مجموعه‌هایی که آناگرامند را چاپ کند.\
    این یک مثال از نتیجه احتمالی است:\
    \[‘deltas’, ‘desalt’, ‘lasted’, ‘salted’, ‘slated’, ‘staled’\]\
    \[‘retainers’, ‘ternaries’\]\
    \[‘generating’, ‘greatening’\]\
    \[‘resmelts’, ‘smelters’, ‘termless’\]\
    راهنمایی: شاید بخواهید که یک دیکشنری بسازید که لیستی از حروف بسازد و
    در بین لغات بگردد و لغاتی که با آن حروف می‌توان ساخت را پیدا کنید.
    سوالی که مطرح است این است که چطور میخواهید از حروف به عنوان کلید در
    دیکشنری استفاده کنید؟
2.  برنامه پیش را طوری ویرایش کنید که مجموعه آناگرام ها رو به ترتیب
    بزرگی آنها چاپ کند.
3.  در بازی Scrabble وقتی برنده میشوید که تمام هفت خانه در قسمت خودتان
    را بازی کنید که به همراه حرف روی تخته یک کلمه هشت حرفی ایجاد کند.
    کدام مجموعه ۸ حرفی محتمل ترین برد را ایجاد میکند؟\
    راهنمایی: هفت مجموعه وجود دارد.\
    راه‌حل:‌
    [*http*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*://*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*www*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*.*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*greenteapress*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*.*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*com*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*/*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*thinkpython*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*/*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*code*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*/*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*anagram*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*\_*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*sets*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*.*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)[*py*](http://www.greenteapress.com/thinkpython/code/anagram_sets.py)

**تمرین ۵**

دو کلمه یک زوج متاتز را تشکیل میدهند اگر با جابجا کردن دو کاراکتر از یکی
از آنها، تبدیل به کلمه دیگر میشود; به طور مثال دو کلمه "converse" و
"conserve". برنامه‌ای بنویسید که تمام زوج‌های متاتز را در دیکشنری پیدا
کند. راهنمایی: تمام زوج لغات را بررسی نکنید، همچنین همه جایگزینی‌ها را
بررسی نکنید. راه‌حل:
[*http*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*://*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*www*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*.*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*greenteapress*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*.*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*com*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*/*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*thinkpython*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*/*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*code*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*/*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*metathesis*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*.*](http://www.greenteapress.com/thinkpython/code/metathesis.py)[*py*](http://www.greenteapress.com/thinkpython/code/metathesis.py)
این تمرین از مثالی در اینجا الگو گرفته شده
است:‌[*http*](http://puzzler.org)[*://*](http://puzzler.org)[*puzzler*](http://puzzler.org)[*.*](http://puzzler.org)[*org*](http://puzzler.org)

**تمرین ۶**

یک مثال دیگر از سایت
[*http*](http://cartalk.com/content/puzzlers)[*://*](http://cartalk.com/content/puzzlers)[*cartalk*](http://cartalk.com/content/puzzlers)[*.*](http://cartalk.com/content/puzzlers)[*com*](http://cartalk.com/content/puzzlers)[*/*](http://cartalk.com/content/puzzlers)[*content*](http://cartalk.com/content/puzzlers)[*/*](http://cartalk.com/content/puzzlers)[*puzzlers*](http://cartalk.com/content/puzzlers)

طولانی ترین کلمه انگلیسی، که با کم کردن هر کدام از حرف‌هایش یک کلمه
معنی‌دار انگلیسی باقی می‌ماند، کدام است؟

حروف میتوانند از هر طرف کلمه یه حتی از وسط آن حذف شوند ولی نمی‌توان حروف
را جابجا کرد. هر بار که یک حرف را حذف میکنید یک کلمه انگلیسی جدید ایجاد
میشود. در نهایت به یک حرف میرسید که یک کلمه یک حرفی را تشکیل میدهد، و آن
کلمه هم باید یک کلمه انگلیسی معنی دار باشد (در دیکشنری پیدا شود). من
میخواهم بدانم طولانی ترین کلمه چیست و چند کاراکتر دارد؟

من یک مثال ساده میزنم: sprite. شما با کلمه sprite شروع میکنید و هر بار
که یک کاراکتر را از داخل کلمه حذف میکنیم، مثل r و کلمه باقی‌مانده میشود
spite و حرف e را حذف میکنیم و کلمه spit بوجود می‌آید و s را حذف میکنیم و
سپس i.

برنامه ای بنویسید که تمام کلمه‌هایی که به این شکل قابل تغییرند را پیدا
کند و از بین آنها طولانی ترین کلمه را پیدا کند.

این تمرین کمی از باقی تمرین‌ها چالش برانگیزتر است. چند پیشنهاد:

1.  ممکن است بخواهید تابعی بنویسید که کلمه‌ای را بگیرد و لیستی از تمام
    کلماتی که میتوان با حذف یک کاراکتر ایجاد کرد را پیدا کند. این‌ها
    فرزندان آن کلمه‌اند.
2.  به همین شکل هر کلمه که فرزندانش به این شکل فرزندانشان پیدا شود
    قابل کاهش‌اند. برای حالت پایه میتواند رشته خالی را قابل‌کاهش
    فرض کنید.
3.  لیست کلماتی که من ارائه دادم words.txt شامل کلمات تک حرفی نمیشود. در
    نتیجه بهتر است که I و A و رشته خالی را به آن اضافه کنید.
4.  برای بهبود کارایی برنامه را بهبود ببخشید بهتر است کلماتی که
    کاهش‌پذیرند را نگه‌داری کنید.

راه‌حل: http://www.greenteapress.com/thinkpython/code/reducible.py


