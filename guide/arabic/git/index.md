---
title: Git
localeTitle: اذهب
---
## بوابة

Git هو نظام تحكم في إصدار الموزعة مفتوح المصدر تم إنشاؤه عام 2005 بواسطة Linus Torvalds وآخرون من مجتمع تطوير Linux. يمكن أن يعمل Git مع العديد من أنواع المشاريع ، ولكنه يستخدم بشكل شائع في التعليمات البرمجية المصدر للبرامج.

التحكم في الإصدار هو نظام يتتبع التغييرات في ملف أو مجموعة من الملفات على مدار الوقت. عندما يكون لديك سجل بهذه التغييرات ، فإنه يتيح لك العثور على إصدارات محددة لاحقًا ، أو مقارنة التغييرات بين الإصدارات ، أو استرداد الملفات التي ربما قمت بحذفها ، أو إعادة الملفات إلى الإصدارات السابقة.

يعني نظام التحكم في إصدار _الموزعة_ أن المستخدمين المختلفين يحتفظون بمستودعاتهم الخاصة لمشروع ، بدلاً من العمل من مستودع مركزي واحد. يتمتع المستخدمون تلقائيًا بقدرات تتبع كاملة للملفات وسجل تاريخ المشروع بالكامل دون الحاجة إلى الوصول إلى خادم أو شبكة مركزية.

عندما تتم تهيئة Git في دليل مشروع ، يبدأ تعقب تغييرات الملف وتخزينها كـ "مجموعات تغيير" أو "تصحيحات". يقدم المستخدمون الذين يعملون معاً في مشروع مجموعات التغيير الخاصة بهم والتي يتم تضمينها (أو رفضها) في المشروع.

**جدول المحتويات**

*   [فهم ثلاثة أقسام من مشروع Git](#understand-the-three-sections-of-a-git-project)
*   [تثبيت Git](#install-git)
*   [تكوين بيئة Git](#configure-the-git-environment)
*   [تهيئة Git في مشروع](#initialize-git-in-a-project)
*   [الحصول على مساعدة في جيت](#get-help-in-git)
*   [مصادر](#sources)
*   [معلومات اكثر](#more-information)

### فهم ثلاثة أقسام من مشروع Git

سيتضمن مشروع Git الأقسام الثلاثة التالية:

1.  دليل جيت
2.  دليل العمل (أو شجرة العمل)
3.  منطقة التدريج

**دليل Git** (الموجود في مشروعك `YOUR-PROJECT-PATH/.git/` ) هو المكان الذي تخزن فيه Git كل ما تحتاجه لتتبع المشروع بدقة. يتضمن ذلك بيانات التعريف وقاعدة بيانات الكائنات التي تتضمن إصدارات مضغوطة من ملفات المشروع.

**دليل العمل** هو المكان الذي يقوم فيه المستخدم بإجراء تغييرات محلية على المشروع. يسحب دليل العمل ملفات المشروع من قاعدة بيانات كائن دليل Git ويضعها على الجهاز المحلي للمستخدم.

**منطقة التدريج** عبارة عن ملف (يُطلق عليه أيضًا اسم "الفهرس" أو "المرحلة" أو "ذاكرة التخزين المؤقت") الذي يخزن معلومات حول ما سيحدث في التزامك التالي. الالتزام هو عندما تخبر Git بحفظ هذه التغييرات المرحلية. يأخذ Git لقطة من الملفات كما هي ، ويقوم بتخزين هذه اللقطة بشكل دائم في دليل Git.

مع ثلاثة أقسام ، هناك ثلاث حالات رئيسية يمكن أن يكون الملف فيها في أي وقت محدد: الالتزام ، التعديل ، أو التدريج. يمكنك _تعديل_ ملف في أي وقت تقوم فيه بإجراء تغييرات عليه في دليل العمل الخاص بك. بعد ذلك ، يتم _تنظيمه_ عند نقله إلى منطقة التدريج. أخيرا ، _ارتكبت_ بعد ارتكاب.

### تثبيت Git

*   أوبونتو: `sudo apt-get install git`
*   ويندوز: [تنزيل](https://git-scm.com/download/win)
*   Mac: [تنزيل](https://git-scm.com/download/mac)

### تكوين بيئة Git

يحتوي Git على أداة `git config` التي تسمح لك بتخصيص بيئة Git الخاصة بك. يمكنك تغيير طريقة Git ووظائفها من خلال تحديد متغيرات تهيئة معينة. قم بتشغيل هذه الأوامر من واجهة سطر الأوامر على جهازك (Terminal في Mac أو موجه الأوامر أو Powershell في Windows).

هناك ثلاثة مستويات حيث يتم تخزين هذه المتغيرات التكوين:

1.  النظام: يقع في `/etc/gitconfig` ، ويطبق الإعدادات الافتراضية على كل مستخدم للكمبيوتر. لإجراء تغييرات على هذا الملف ، استخدم خيار `--system` باستخدام أمر `git config` .
2.  المستخدم: يقع في `~/.gitconfig` أو `~/.config/git/config` ، يطبق الإعدادات على مستخدم واحد. لإجراء تغييرات على هذا الملف ، استخدم الخيار `--global` باستخدام أمر `git config` .
3.  المشروع: يقع في مشروعك `YOUR-PROJECT-PATH/.git/config` ، يطبق الإعدادات على المشروع فقط. لإجراء تغييرات على هذا الملف ، استخدم الأمر `git config` .

إذا كانت هناك إعدادات تتعارض مع بعضها البعض ، فستتجاوز التهيئات على مستوى المشروع المستويات على مستوى المستخدم ، وستتجاوز التهيئات على مستوى المستخدم تلك التي على مستوى النظام.

ملاحظة لمستخدمي Windows: تبحث Git عن ملف التكوين على مستوى المستخدم ( `.gitconfig` ) في دليل `$HOME` الخاص بك ( `C:\Users\$USER` ). يبحث Git أيضًا عن `/etc/gitconfig` ، على الرغم من أنه يتعلق بجذر MSys ، وهو المكان الذي تقرر فيه تثبيت Git على نظام Windows الخاص بك عند تشغيل برنامج التثبيت. إذا كنت تستخدم الإصدار 2.x أو أحدث من Git لـ Windows ، فهناك أيضًا ملف تهيئة على مستوى النظام في `C:\Documents and Settings\All Users\Application Data\Git\config` على Windows XP ، وفي `C:\ProgramData\Git\config` على ويندوز فيستا وأحدث. لا يمكن تغيير ملف التهيئة هذا إلا بواسطة `git config -f FILE` كمسؤول.

#### أضف اسمك والبريد الإلكتروني

يتضمن Git اسم المستخدم والبريد الإلكتروني كجزء من المعلومات الموجودة في الالتزام. ستحتاج إلى إعداد هذا ضمن ملف التهيئة على مستوى المستخدم باستخدام هذه الأوامر:

```shell
git config --global user.name "My Name"
git config --global user.email "myemail@example.com"
``` 

#### تغيير محرر النص الخاص بك

يستخدم Git تلقائيًا محرر النصوص الافتراضي ، ولكن يمكنك تغيير ذلك. في ما يلي مثال لاستخدام محرر Atom بدلاً منه (الخيار `--wait` يخبر shell بانتظار محرر النص حتى تتمكن من القيام `--wait` فيه قبل أن ينتقل البرنامج):

```shell
git config --global core.editor "atom --wait"
``` 

#### إضافة اللون إلى إخراج Git

يمكنك تكوين shell الخاص بك لإضافة اللون إلى إخراج Git باستخدام هذا الأمر:

```shell
git config --global color.ui true
``` 

للاطلاع على جميع إعدادات التهيئة ، استخدم الأمر `git config --list` .

### تهيئة Git في مشروع

بعد تثبيت Git وتهيئته على جهاز الكمبيوتر ، ستحتاج إلى تهيئته في مشروعك لبدء استخدام صلاحيات التحكم في الإصدار. في سطر الأوامر ، استخدم الأمر `cd` للتنقل إلى مجلد المستوى الأعلى (أو الجذر) للمشروع الخاص بك. بعد ذلك ، قم بتشغيل الأمر `git init` . يقوم هذا بتثبيت مجلد دليل Git بكافة الملفات والكائنات التي يحتاجها Git لتتبع مشروعك.

من المهم تثبيت دليل Git في مجلد جذر المشروع. يمكن لـ Git تتبع الملفات في المجلدات الفرعية ، ولكنها لن تتعقب الملفات الموجودة في المجلد الرئيسي نسبة إلى دليل Git.

### الحصول على مساعدة في جيت

إذا نسيت كيف يعمل أي أمر في Git ، فيمكنك الوصول إلى مساعدة Git من سطر الأوامر بعدة طرق:

```shell
git help COMMAND
git COMMAND --help
man git-COMMAND
``` 

هذا يعرض الصفحة اليدوية للأمر في إطار shell الخاص بك. للتنقل ، انتقل باستخدام مفاتيح الأسهم لأعلى ولأسفل أو استخدم اختصارات لوحة المفاتيح التالية:

*   `f` أو `spacebar` إلى الصفحة إلى الأمام
*   `b` لصفحة العودة
*   `q` للإقلاع

### مصادر

تستخدم هذه المقالة معلومات من كتاب [برو جيت](https://github.com/progit/progit2) ، كتبها سكوت شاكون وبن شتراوب ونشرتها Apress. يتم عرض الكتاب بالكامل في [وثائق Git](https://git-scm.com/book/en/v2) .

### معلومات اكثر:

*   للتنزيل والتوثيق وبرنامج تعليمي يستند إلى المتصفح: [موقع Git الرسمي](https://git-scm.com/)
*   الأوامر الأكثر فائدة عندما تكون في موقف GIT سيئة: [يا القرف ، بوابة!](http://ohshitgit.com/)