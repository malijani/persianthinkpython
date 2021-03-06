# فصل پنجم

**شرطی و بازگشتی**

عملگر ماژول (Modulus)

عملگر ماژول بر روی اعداد صحیح (Integers) کار می کند و زمانی که عملوند
اول تقسیم بر عملگر دوم شد، باقی مانده را بر می گرداند.در Python عملگر
ماژول نشانه ی "% "است. نحو آن مانند بقیه عملگر هاست.

&gt;&gt;&gt; quotient = 7/3\
&gt;&gt;&gt; print quotient\
2\
&gt;&gt;&gt; remainder =7%3\
&gt;&gt;&gt; print remainder\
1

بنابراین 7 تقسیم بر 3 دارای خارج قسمت 2 و باقی مانده ی 1 است.

عملگر ماژول بسیار کاربردی است. به عنوان مثال شما می توانید بررسی کنید که
آیا عددی بر عدد دیگر تقسیم پذیر است یا خیر. در صورتی که x%y برابر با صفر
شود در این صورت x برy تقسیم پذیر است.

همچنین، شما می توانید راست ترین رقم از یک عدد را استخراج نمایید. به
عنوان مثال x%10 کم ارزش ترین رقم بر مبنا ی 10 را بر می گرداند. به طر
مشابه x%100 2 رقم کم ارزش را بر می گرداند.

عبارت بولی (Boolean Expression)

یک عبارات بولی عبارتی است که یا درست(true) است و یا غلط(false). مثال زیر
از عملگر == استفاده می کند ، که دو عملوند را مقایسه کرده و در صورت برابر
بودن مقدار true و در غیر اینصورت false را بر می گرداند.

&gt;&gt;&gt; 5==5\
True\
&gt;&gt;&gt; 5==6\
False

True و False مقادیر خاص متعلق به type bool (نوع بول) هستند; آنها رشته
نیستند.

&gt;&gt;&gt; type(True)\
&lt;type ‘bool’&gt;\
&gt;&gt;&gt; type(False)\
&lt;type ‘bool’&gt;

عملگر == یکی از عملگرهای رابطه ای است(relational operators); بقیه این
عملگر ها عبارت اند از:

x!=y \# نیست y برابر x\
x &gt;y \# است y بزرگتر از x\
x&lt;y\# است y کوچکتر از x\
x&gt;=y\# است y بزرگتر یا مساوی از x\
x&lt;=y\# است y کوچکتر یا مساوی از x

با اینکه ممکن است عملیات های ذکر شده برای شما آشنا باشند، نشانه های
Python از نشانه ی های ریاضیاتی متفاوت هستند.یکی از خطا های رایج استفاده
از تک علامت مسای “=” به جای دو مساوی "==" است. به یاد داشته باشید که "="
یک عملگر انتسابی و "==" یک عملگر رابطه ای است. عملگر های مانند "&gt;=" و
یا "&lt;=" وجود ندارند.

عملگر های منطقی (Logical Operators)

3 عملگر منطقی وجود دارد: and ، orو not . معنای (semantic) این عملگر ها
شبیه معنای آن ها در زبان انگلیسی است. به عنوان مثال x&gt;0 and x&lt;10
صحیح است تنها در صورتی که x بزرگتر از 0 و کوچکتر از 10 باشد.

N%2==0 or n%3==0 هنگامی که هر یک از شروط آن صحیح باشد،زمانی که x بر 2 و
یا 3 بخش پذیر است، صحیح است.

عملگر not یک عبارت بولی را منفی می کند، بنابراین not (x&gt;y) صحیح است
اگر x&gt;y نا صحیح باشد که در این حالت x کوچکتر و یا مساوی y است.

به طور دقیق، عملوند های عملگر های منطقی باید عبارات بولی باشند، اما
پیاتون آنچنان سخت گیر نیست! هر مقدار غیر صفر به عنوان یک "true" تفسیر می
شود.

&gt;&gt;&gt; 17 and True\
True

این انعطاف پذیری می تواند مفید باشد، اما پیچیدگی های خاصی وجود دارد که
ممکن است باعث سردرگمی شوند. ممکن است بخواید از آنها دوری کنید (بغیر از
هنگامی که بدانید در حال انجام چه کاری هستید!)

اجرای شرطی (Conditional Execution)

برای نوشتن یک برنامه ی کارا، تقریبا همیشه نیازمند توانایی بررسی شروط و
تغییر رفتار برنامه بر اساس آن ها هستیم. جملات شرطی این توانایی را به ما
می دهند. ساده ترین حالت، عبارت if است:

If x&gt;0:\
print ‘x is positive’

عبارت بولی بعد از if شرط (condition) نامیده می شود. اگر صحیح باشد، جمله
ی فاصله دار شده اجرا می شود. در غیر این صورت، هیچ چیز اتفاق نمی افتد.

عبارت if ساختاری مشابه با تعریف تابع دارد: یک سر تیتر(header) با یک بدنه
ی فاصه دار شده. جملاتی شبیه به این را جملات مرکب (compound statements)
می نامند.

محدودیتی بر تعداد جملاتی که می توانند در بدنه قرار گیرند وجود ندارد، اما
وجود حداقل یک جمله اجباری است. گاها، داشتن بدنه ای بدون جمله کاربردی است
(معمولا به عنوان مکانی برای کدی که هنوز ننوشته اید). در این حالت از
عبارت pass استفاده می کنید، که در واقع هیچ کاری انجام نمی دهد :

if x &lt; 0 :\
pass\#need to handle negative values!

اجرای جایگزین (alternative execution)

دومین حالت عبارت if ، اجرای جایگزین است، که در آن 2 احتمالی که شرط اجرای
آن را مشخص می نماید وجود دارد. ساختاری نحوی آن به صورت زیر است:

if x%2 == 0:\
print ‘x is even’\
else:\
print ‘x is odd’

در صورتی که باقی مانده ی x تقسیم بر 2 برابر صفر باشد، ما می دانیم که x
زوج است، و برنامه پیغامی مبنی بر زوج بودن آن را نمایش می دهد. در صورتی
که شرط اشتباه باشد، بخش دوم عبارت اجرا می شود.از آنجایی که شرط باید یکی
از حالات صحیح و یا غلط باشد، دقیقا یکی از جایگزین ها اجرا می شود. به
جایگزین ها شاخه ها (branches) نیز گفته می شود، زیرا آن ها شاخه های در
جریان اجرا می باشند.

شروط زنجیر وار (chained conditionals)

گاها بیش از 2 احتمال و 2 شاخه مورد نیاز است. یکی از راه های نمایش محاسبه
ی این چنینی شروط زنجیر وارد است:

if x &lt; y:\
print ‘x is less than y’\
elif x &gt; y:\
print ‘x is greater than y’\
else:\
print ‘x and y are eqaul’

elif مخفف else if است. بار دیگر، فقط یکی از شاخه ها اجرا می شود. در
تعداد عبارات elif محدودیتی وجود ندارد. در صورتی که قسمت else ای وجود
دارد، باید حتما در پایان باشد، اما لزومی بر تنها یکی بودن آن وجود ندارد.

if choice == ‘a’:\
draw\_a()\
elif choice == ‘b’:\
draw\_b()\
elif choice == ‘c’:\
draw\_c()

هر یک از شروط به ترتیب قرار گیری بررسی می شوند. در صورتی که اولین شرط
غلط باشد، دومین شرط بررسی می شود، در به همین ترتیب تا آخر بررسی می شوند.
در صورتی که یکی از شروط درست باشد، شاخه ی متناظر اجرا شده، و جمله به
پایان می رسد. حتی اگر بیش از یک عبارت درست باشد تنها اولین شاخه ی صحیح
اجرا می شود.

شروط تو در تو (Nested Conditionals)

یک شرط می توند درون شرطی دیگر جایگزاری شود. ما می توانیم یک مثال تقسیم
بر 3 بخش را مانند زیر بنوسیسم :

if x == y:\
print ‘x and y are equal’\
else:\
if x &lt;y :\
print ‘x is less than y’\
else :\
print ‘x is greater than y’

شرط خارجی تر متشکل از 2 شاخه است. اولین شاخه شامل یک عبارت ساده است.
شاخه ی دوم شامل یک عبارت if دیگر است، که برای خود 2 شاخه ی دیگر دارد.
این 2 شاخه، هر دو شامل یک عبارت ساده اند. با این حال می توانستند خود
شامل عبارات شرطی باشند.

اگر چه فاصله دار شدن عبارت باعث خوانا شدن ساختار می گردد، شروط تو در تو
به سرعت خوانایی خود را از دست می دهند. به طور کلی، دوری کردن از آنها در
صورت توانایی ایده ی مناسبی است.

عملگر های منطقی معمولا راحی برای سادگی شروط تو در تو ارائه می کنند. به
عنوان مثال، ما می توانیم کد زیر را با یک شرط باز نویسی کنیم:

if 0 &lt; x:\
if x &lt;10:\
print ‘x is a positive single-digit number.’

عبارت print تنها زمانی اجرا می شود که از هر دو شرط درست باشند، بنا بر
این ما می توانی همین اثر را از عملگر and بگیریم:

if 0 &lt; x and x &lt; 10 :\
print ‘x is a positive single-digit number.’

\
بازگشت (Recursion)

فراخوانی یک تابع توسط تابعی دیگر مجاز است; همچین برای یک تابع فراخوانی
خودش نیز مجاز می باشد. ممکن است دلیل خوب بودن این کار واضح نباشد، اما
مشخص شده است که این کار خارق العاده ترین چیزی است که یک برنامه می تواند
انجام دهد. به عنوان مثال به تابع زیر دقت نمایید :

def countdown(n):\
if n &lt;= 0:\
print ‘blastoff’\
else:\
print n\
countdown(n-1);<span id="anchor"></span>def countdown(n):\
if n &lt;= 0:\
print ‘blastoff’\
else:\
print n\
countdown(n-1);


