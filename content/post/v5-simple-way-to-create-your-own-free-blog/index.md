---
title: "دليل المبتدئين جدًا: سوّ مدونة عربية بـ Hugo Stack خطوة بخطوة (GitHub Pages + Codespaces)"
description: "شرح عملي للمبتدئ: انسخ القالب لحسابك، فعّل GitHub Pages، شغّل الموقع من Codespaces، اضبط baseurl، عربه RTL، اكتب أول مقال، وانشر."
slug: "hugo-stack-arabic-codespaces-beginners-guide"
date: 2026-02-17T10:00:00+03:00
image: cover-post-v1.png
categories:
  - ابدأ هنا
tags:
  - hugo
  - hugo-theme-stack
  - github-pages
  - github-actions
  - github-codespaces
  - rtl
keywords:
  - شرح Hugo Stack بالعربي
  - GitHub Pages للمبتدئين
  - إنشاء مدونة مجانية
  - GitHub Codespaces Hugo
  - baseurl Hugo GitHub Pages
  - مدونة عربية RTL
---

## 1) المقدمة (المشكلة/الهدف)

تبغى مدونة/موقع شخصي **مجاني** وسريع… بدون استضافة مدفوعة… وبدون ما تدخل في تعقيد سيرفرات؟

تخيل الموضوع ببساطة:

- `GitHub` = مكان نحفظ فيه ملفات موقعك.
- `Codespaces` = كمبيوتر جاهز داخل المتصفح (VS Code).
- `Hugo` = برنامج يبني الموقع من ملفات Markdown بسيطة.

بنهاية الشرح: موقعك يصير **Live** على GitHub Pages + عربي RTL + أول مقال.

> إذا تبغى تشوف أمثلة على “شكل المقالات” عندي في المدونة:
> - [إعداد Raspberry Pi 5 من الصفر](/post/raspberry-pi-5-setup-ssh-docker/)
> - [شرح AdGuard Home (مانع إعلانات للشبكة)](/post/adguard-home-network-wide-adblock/)

## 2) الفيديو

{{< youtube "PUT_VIDEO_ID_HERE" >}}

## 3) المتطلبات (Prerequisites)

- حساب GitHub.
- متصفح.
- اتصال إنترنت.
- (اختياري) صورة بروفايل `avatar.png`.

## 4) التطبيق خطوة بخطوة (لا تنط)

هذا “ترتيب” الشرح عشان تمشي معي بنفس التسلسل:

1. انسخ القالب لحسابك
2. فعّل النشر التلقائي (GitHub Pages)
3. افتح Codespaces
4. شغّل الموقع (معاينة)
5. عرب الموقع + RTL + `baseurl`
6. عدّل صفحات القائمة
7. أضف حسابات السوشيال
8. ارفع صورك من جهازك لـ Codespaces
9. اكتب أول مقال + غلاف
10. ارفع التعديلات (push)
11. (اختياري) خيارات إضافية للي يبغى تحكم أكثر

---

### 4.1) انسخ القالب لحسابك (أول خطوة)

وش تسوي؟
- تخلي القالب يصير عندك في حسابك (عشان تقدر تعدّل عليه).

الخطوات:
1. افتح ريبو القالب على GitHub.
2. اضغط `Use this template`.
3. اختر `Create a new repository`.
4. اكتب اسم للريبو.

معلومة مهمة جدًا عن الاسم (عشان `baseurl`):
- إذا اسم الريبو `YOUR_USERNAME.github.io` → موقعك يكون على: `https://YOUR_USERNAME.github.io/`
- إذا اسم الريبو `my-blog` → موقعك يكون على: `https://YOUR_USERNAME.github.io/my-blog/`

### 4.2) فعّل النشر التلقائي (مرة واحدة فقط)

وش يعني؟
- كل مرة تسوي `push` الموقع يتحدث لوحده.

الخطوات:
1. افتح الريبو حقك في GitHub.
2. ادخل `Settings`.
3. ادخل `Pages`.
4. في `Build and deployment` اختر: `Source = GitHub Actions`.

### 4.3) افتح المشروع في GitHub Codespaces

وش يعني Codespaces؟
- VS Code كامل داخل المتصفح (كمبيوتر جاهز).

الخطوات:
1. افتح الريبو.
2. اضغط `Code`.
3. افتح تبويب `Codespaces`.
4. اضغط `Create codespace on main`.

### 4.4) شغّل الموقع (عشان تشوف التعديلات)

افتح Terminal داخل Codespaces واكتب:

```bash
hugo server -D
```

وش يسوي هذا الأمر؟
- يشغل الموقع محليًا داخل Codespaces.
- `-D` يعني: يعرض المقالات اللي لسه مخفية (Draft).

بعدها:
1. افتح تبويب `Ports`.
2. افتح المنفذ `1313`.

---

### 4.5) عرب الموقع بالكامل + RTL + `baseurl` (أهم خطوة)

#### 4.5.1) عدّل رابط الموقع + اسم الموقع

افتح: `config/_default/config.toml`

إذا اسم الريبو `YOUR_USERNAME.github.io`:

```toml
baseurl = "https://YOUR_USERNAME.github.io/"
languageCode = "ar"
title = "اسم مدونتك"
defaultContentLanguage = "ar"
hasCJKLanguage = false
```

إذا اسم الريبو `my-blog`:

```toml
baseurl = "https://YOUR_USERNAME.github.io/my-blog/"
```

#### 4.5.2) خلي اتجاه الموقع عربي (RTL)

افتح: `config/_default/languages.toml`

```toml
[ar]
languageName = "العربية"
languagedirection = "rtl"
title = "اسم مدونتك"
weight = 1
```

#### 4.5.3) عدّل نص البروفايل (تحت الصورة) + الفوتر

افتح: `config/_default/params.toml`

```toml
[sidebar]
emoji = "👋"
subtitle = "اكتب وصف مدونتك هنا"
avatar = "img/avatar.png"

[footer]
since = 2026
customText = "اكتب نص الفوتر هنا"
```

---

### 4.6) عدّل صفحات القائمة (الرئيسية/الأرشيف/البحث/الروابط)

فكرة بسيطة:
- هذي صفحات جاهزة.
- أنت بس تغيّر العنوان والكلام.

#### الرئيسية

افتح: `content/_index.md`

```yaml
---
menu:
  main:
    name: الرئيسية
    weight: 1
    params:
      icon: home
---
```

#### الأرشيف

افتح: `content/page/archives/index.md`

```yaml
---
title: "الأرشيف"
layout: "archives"
slug: "archives"
menu:
  main:
    weight: 2
    params:
      icon: archives
---
```

#### البحث

افتح: `content/page/search/index.md`

```yaml
---
title: "بحث"
slug: "search"
layout: "search"
outputs:
  - html
  - json
menu:
  main:
    weight: 3
    params:
      icon: search
---
```

#### الروابط (صفحة روابطك)

افتح: `content/page/links/index.md`

```yaml
---
title: "روابطي"
links:
  - title: "يوتيوب"
    description: "قناتي"
    website: "https://ضع-رابط-قناتك-هنا"
    image: "https://ضع-رابط-شعار-يوتيوب-هنا.png"
  - title: "انستغرام"
    description: "حسابي"
    website: "https://ضع-رابط-حسابك-هنا"
    image: "https://ضع-رابط-شعار-انستغرام-هنا.png"
menu:
  main:
    weight: 4
    params:
      icon: link
comments: false
---
```

وش يسوي `links`؟
- يعرض لك كروت (Cards) بروابطك.

---

### 4.7) أضف حسابات السوشيال تحت الصورة

وش يعني؟
- الأيقونات الصغيرة اللي تظهر تحت صورة البروفايل.

افتح: `config/_default/menu.toml` وحط روابطك:

```toml
[[social]]
    identifier = "youtube"
    name       = "YouTube"
    url        = "https://youtube.com/@YOUR_CHANNEL"

    [social.params]
        icon = "brand-youtube"

[[social]]
    identifier = "instagram"
    name       = "Instagram"
    url        = "https://instagram.com/YOUR_ACCOUNT"

    [social.params]
        icon = "brand-instagram"

[[social]]
    identifier = "github"
    name       = "GitHub"
    url        = "https://github.com/YOUR_USERNAME"

    [social.params]
        icon = "brand-github"
```

إذا ما ظهرت الأيقونات بعد التعديل:
- سو Refresh للصفحة.
- أو وقف `hugo server` وشغله مرة ثانية.

---

### 4.8) كيف ترفع صورك من جهازك إلى Codespaces

هذا مهم لأن الصور تكون في جهازك، وCodespaces شيء ثاني.

<details>
<summary><strong>3 طرق (Drag & Drop / Upload / Copy-Paste)</strong></summary>

#### الطريقة 1: سحب وإفلات (Drag & Drop)

1. افتح File Explorer في Codespaces.
2. افتح مجلد المقال.
3. اسحب الصورة من جهازك.
4. افلتها داخل المجلد.

#### الطريقة 2: Upload

1. كلك يمين على المجلد.
2. اختَر `Upload...`.
3. اختر الصورة.

#### الطريقة 3: Copy / Paste

أحيانًا تقدر تنسخ ملف من جهازك وتلصقه داخل Explorer.

</details>

---

### 4.9) اكتب أول مقال (أسهل طريقة)

#### 4.9.1) أنشئ المقال

```bash
hugo new content/post/my-first-post/index.md
```

#### 4.9.2) بطاقة المقال (Front Matter)

افتح: `content/post/my-first-post/index.md` واكتب:

```yaml
---
title: "هذا أول مقال لي"
description: "وصف بسيط"
date: 2026-02-17T20:00:00+03:00
draft: false
---
```

أهم سطر هنا:
- `draft: false` يعني المقال يظهر (مو مخفي).

#### 4.9.3) (اختياري) صورة غلاف

1. حط صورة داخل نفس مجلد المقال باسم `cover.jpg`:
`content/post/my-first-post/cover.jpg`
2. أضف في بطاقة المقال:

```yaml
image: cover.jpg
```

مهم:
- لا تكتب `image: cover.jpg` إلا إذا الصورة موجودة فعلًا.

---

### 4.10) ارفع التعديلات إلى GitHub (push)

وش يعني push؟
- يعني ترسل تغييراتك من Codespaces إلى GitHub.

من Terminal:

```bash
git status
git add .
git commit -m "setup blog"
git push origin main
```

بعدها افتح `Actions` في GitHub وتأكد أن الـ workflow خلص ✅.

---

## 5) ليش بعض الخيارات تفرق؟ (مختصر مفيد)

- `baseurl`: إذا غلط… الموقع يطلع “مكسّر” (CSS/صور/روابط).
- Page Bundle (مجلد لكل مقال): يخليك تحط الصور داخل نفس مجلد المقال بدل ما تتوه.
- `draft: false`: هو اللي يحدد هل المقال يطلع للعالم أو لا.

## 6) مشاكل شائعة وحلولها

### الموقع يطلع أبيض أو المسارات خربانة
- راجع `baseurl` وخصوصًا إذا اسم الريبو مو `YOUR_USERNAME.github.io`.

### الصور ما تظهر + خطأ `Height`
- هذا غالبًا لأنك كتبت صورة في المقال لكن ملف الصورة غير موجود.
- الحل: حط الصورة داخل نفس مجلد المقال بنفس الاسم، أو احذف سطر الصورة مؤقتًا.

### الأيقونات ما تظهر
- تأكد ملفات SVG داخل `assets/icons/`.
- تأكد اسم الملف يطابق `icon` في `menu.toml`.

### التعديلات ما تبان في المعاينة
- سو Refresh.
- أو أعد تشغيل `hugo server -D`.

## 7) FAQ (أسئلة تتكرر)

### هل لازم أعرف برمجة؟
لا. تقدر تبدأ بمقالات Markdown وتعديلات بسيطة.

### هل لازم Codespaces؟
لا، تقدر تشغل Hugo على جهازك، بس Codespaces أسهل للمبتدئ لأنه يجهز لك البيئة.

### كم ياخذ النشر على GitHub Pages؟
عادةً دقائق. أول مرة ممكن تطول شوي.

### هل أقدر أخلي الموقع عربي RTL بالكامل؟
اي نعم، أهم شيء `languagedirection = "rtl"` + ضبط إعدادات اللغة.

## 8) الخلاصة

الآن عندك مدونة شغالة من الصفر:

- Repo جاهز
- GitHub Actions ينشر تلقائي
- معاينة في Codespaces
- عربي RTL + أول مقال

إذا تبغى حلقة تكملة: (تخصيص أكثر / صفحات إضافية / تحسين SEO) اكتبها بالكومنت.



## 9) خيارات إضافية (اختياري) — للي يبغى تحكم أكثر

هنا حطّيت الأشياء “اللي مو أساسية” داخل Dropdown عشان ما تتشتت كبداية.

<details>
<summary><strong>إضافة أيقونات SVG بنفسك (إذا تبغى أيقونة مو موجودة)</strong></summary>

الفكرة:
- نسوي مجلد: `assets/icons/`
- نحط فيه ملفات `.svg`
- ونستخدم اسم الملف في `menu.toml`

مثال (Instagram):

1) احفظ ملف:
`assets/icons/brand-instagram.svg`

2) الصق هذا الـ SVG:

```xml
<svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-brand-instagram" width="24" height="24" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round">
  <path stroke="none" d="M0 0h24v24H0z" fill="none"/>
  <path d="M4 8a4 4 0 0 1 4 -4h8a4 4 0 0 1 4 4v8a4 4 0 0 1 -4 4h-8a4 4 0 0 1 -4 -4z" />
  <path d="M9 12a3 3 0 1 0 6 0a3 3 0 0 0 -6 0" />
  <path d="M16.5 7.5v.01" />
</svg>
```

قاعدة سهلة:
- اسم الملف (بدون `.svg`) لازم يطابق `icon`.

</details>

<details>
<summary><strong>تفعيل التعليقات (Disqus) — للمبتدئ</strong></summary>

أبسط خيار للمبتدئ: Disqus.

1) سو حساب في Disqus واختر `Shortname`.

2) افتح: `config/_default/config.toml` وحط:

```toml
disqusShortname = "PUT_YOUR_DISQUS_SHORTNAME"
```

3) افتح: `config/_default/params.toml` وتأكد:

```toml
[comments]
enabled  = true
provider = "disqus"
```

ملاحظة:
- أحيانًا صندوق التعليقات ما يبان في المعاينة المحلية، أفضل اختبار بعد النشر.

</details>

<details>
<summary><strong>ثيمي المستخدم هنا</strong></summary>

افتح: `assets/scss/custom.scss`

هذا الي انا استخدمه في هذي المدونه هنا:

```scss
/* Arabic localization and RTL refinements */
/* تحسينات للغة العربية + دعم اتجاه RTL (من اليمين لليسار) */

:root { /* الجذر: هنا نعرّف متغيرات CSS الافتراضية (للثيم الفاتح) */

    /* Theme colors (light) */
    /* ألوان الثيم في الوضع الفاتح */
    --body-background: #f6f7fb;      /* لون خلفية الصفحة */
    --body-text-color: #1f2937;      /* لون النص الأساسي */
    --card-background: #ffffff;      /* لون خلفية الكروت/الصناديق */
    --accent-color: #0ea5e9;         /* لون التمييز (روابط/عناصر بارزة) */

    /* Code */
    /* إعدادات ألوان الكود (Code blocks / Inline code) */
    --code-block-bg: #0f172a;                 /* لون خلفية بلوك الكود */
    --code-block-border: rgba(15, 23, 42, 0.18); /* لون/شفافية إطار بلوك الكود */
    --code-block-fg: rgba(255, 255, 255, 0.9);   /* لون نص الكود داخل البلوك */
    --inline-code-bg: rgba(14, 165, 233, 0.12);  /* خلفية الكود داخل السطر (inline) */
    --inline-code-border: rgba(14, 165, 233, 0.25); /* إطار inline code */
    --inline-code-fg: #0b1220;                /* لون نص inline code */

    /* Map Stack theme vars to our palette (fixes the brown wrapper around code blocks) */
    /* ربط متغيرات ثيم Stack بمتغيراتنا (يحل مشكلة الإطار/الغلاف البني حول بلوكات الكود) */
    --pre-background-color: var(--code-block-bg); /* يجعل خلفية <pre> مثل خلفية بلوك الكود */
    --pre-text-color: var(--code-block-fg);       /* يجعل لون نص <pre> مثل لون نص الكود */
    --code-background-color: var(--inline-code-bg); /* يجعل خلفية <code> داخل النص مثل inline */
    --code-text-color: var(--inline-code-fg);       /* يجعل لون نص <code> داخل النص مثل inline */

    /* Syntax colors */
    /* ألوان تلوين الشفرة (Syntax Highlighting) */
    --code-syntax-keyword: #60a5fa;             /* لون الكلمات المحجوزة مثل: if / for */
    --code-syntax-string: #34d399;              /* لون النصوص داخل علامات الاقتباس */
    --code-syntax-number: #a78bfa;              /* لون الأرقام */
    --code-syntax-function: #fbbf24;            /* لون أسماء الدوال/الوظائف */
    --code-syntax-operator: #f472b6;            /* لون العمليات مثل + - = */
    --code-syntax-comment: rgba(148, 163, 184, 0.75); /* لون التعليقات داخل الكود */
    --code-syntax-punctuation: rgba(226, 232, 240, 0.88); /* لون الأقواس والفواصل ... */
    --code-syntax-line-highlight: rgba(56, 189, 248, 0.16); /* لون تظليل سطر محدد */
}

:root[data-scheme="dark"] { /* الجذر في الوضع الداكن فقط */

    /* Theme colors (dark) */
    /* ألوان الثيم في الوضع الداكن */
    --body-background: #0b1220;                 /* خلفية الصفحة بالداكن */
    --body-text-color: rgba(255, 255, 255, 0.78); /* لون النص الأساسي بالداكن */
    --card-background: #111a2e;                 /* خلفية الكروت بالداكن */
    --accent-color: #38bdf8;                    /* لون التمييز بالداكن */

    /* Code */
    /* إعدادات الكود بالداكن */
    --code-block-bg: #0a1222;                   /* خلفية بلوك الكود بالداكن */
    --code-block-border: rgba(148, 163, 184, 0.18); /* إطار بلوك الكود بالداكن */
    --code-block-fg: rgba(255, 255, 255, 0.92); /* لون نص الكود بالداكن */
    --inline-code-bg: rgba(56, 189, 248, 0.16); /* خلفية inline code بالداكن */
    --inline-code-border: rgba(56, 189, 248, 0.28); /* إطار inline code بالداكن */
    --inline-code-fg: rgba(255, 255, 255, 0.9); /* لون نص inline code بالداكن */

    /* Syntax colors */
    /* ألوان التلوين بالداكن */
    --code-syntax-keyword: #7dd3fc;             /* keywords */
    --code-syntax-string: #34d399;              /* strings */
    --code-syntax-number: #c4b5fd;              /* numbers */
    --code-syntax-function: #fbbf24;            /* functions */
    --code-syntax-operator: #fb7185;            /* operators */
    --code-syntax-comment: rgba(148, 163, 184, 0.75); /* comments */
    --code-syntax-punctuation: rgba(226, 232, 240, 0.88); /* punctuation */
    --code-syntax-line-highlight: rgba(56, 189, 248, 0.16); /* line highlight */
}

/* Code blocks + inline code (override Chroma defaults) */
/* تنسيق بلوكات الكود + كود داخل السطر (تجاوز إعدادات Chroma الافتراضية) */
.article-content .highlight {                       /* صندوق/حاوية الكود */
    background: var(--code-block-bg) !important;    /* خلفية بلوك الكود (إجباري) */
    border: 1px solid var(--code-block-border);     /* إطار بلوك الكود */
    border-radius: 12px;                            /* زوايا دائرية */
}

.article-content .highlight pre,
.article-content pre,
.article-content .chroma,
.article-content .chroma pre {                      /* عناصر <pre> وchroma داخل المقال */
    background: var(--code-block-bg) !important;    /* نفس الخلفية */
    color: var(--code-block-fg);                    /* لون نص الكود */
    border: 1px solid var(--code-block-border);     /* نفس الإطار */
    border-radius: 12px;                            /* نفس الزوايا */
}

.article-content .highlight pre,
.article-content .highlight .chroma,
.article-content .highlight .chroma pre {           /* داخل highlight بالذات */
    border: 0 !important;                           /* يلغي الإطار الداخلي لتجنب تكرار الإطار */
    border-radius: 0;                               /* يلغي الزوايا الداخلية */
}

.article-content .chroma table,
.article-content .chroma td,
.article-content .chroma .lntable,
.article-content .chroma .lntd {                    /* جداول line numbers داخل chroma */
    background: transparent !important;             /* يجعل الخلفية شفافة (بدون مربعات غريبة) */
}

.article-content pre code {                         /* <code> داخل <pre> */
    background: transparent !important;             /* يلغي أي خلفية داخلية */
    color: inherit;                                 /* يأخذ لون النص من الأب */
}

.article-content :not(pre) > code,
.article-content p > code,
.article-content li > code,
.article-content td > code {                        /* inline code داخل النص (وليس داخل pre) */
    background: var(--inline-code-bg);              /* خلفية inline code */
    color: var(--inline-code-fg);                   /* لون نص inline code */
    border: 1px solid var(--inline-code-border);    /* إطار خفيف */
    padding: 0.12em 0.38em;                         /* مسافة داخلية حول النص */
    border-radius: 0.5em;                           /* تدوير الحواف */
}

/* Line numbers */
/* لون أرقام الأسطر داخل بلوك الكود */
.article-content .chroma .lnt,
.article-content .chroma .ln {
    color: rgba(148, 163, 184, 0.85);               /* لون أرقام الأسطر */
}

/* Syntax highlighting: replace the theme's brown/yellow palette */
/* تلوين الشفرة: استبدال ألوان الثيم الافتراضية (البني/الأصفر) */

.article-content .chroma .k,
.article-content .chroma .kc,
.article-content .chroma .kd,
.article-content .chroma .kp,
.article-content .chroma .kr,
.article-content .chroma .kt,
.article-content .chroma .kn,
.article-content .chroma .nt {                      /* فئات الكلمات المحجوزة/أنواع/و... */
    color: var(--code-syntax-keyword) !important;   /* لون keywords */
}

.article-content .chroma .s,
.article-content .chroma .sa,
.article-content .chroma .sb,
.article-content .chroma .sc,
.article-content .chroma .dl,
.article-content .chroma .sd,
.article-content .chroma .s2,
.article-content .chroma .sh,
.article-content .chroma .si,
.article-content .chroma .sx,
.article-content .chroma .sr,
.article-content .chroma .s1,
.article-content .chroma .ss,
.article-content .chroma .ld {                      /* فئات الـ strings */
    color: var(--code-syntax-string) !important;    /* لون strings */
}

.article-content .chroma .m,
.article-content .chroma .mb,
.article-content .chroma .mf,
.article-content .chroma .mh,
.article-content .chroma .mi,
.article-content .chroma .il,
.article-content .chroma .mo {                      /* فئات الأرقام */
    color: var(--code-syntax-number) !important;    /* لون numbers */
}

.article-content .chroma .nf,
.article-content .chroma .na,
.article-content .chroma .nc,
.article-content .chroma .nd,
.article-content .chroma .ne,
.article-content .chroma .nx {                      /* فئات أسماء الدوال/الأنواع */
    color: var(--code-syntax-function) !important;  /* لون functions/identifiers */
}

.article-content .chroma .o,
.article-content .chroma .ow {                      /* فئات العمليات */
    color: var(--code-syntax-operator) !important;  /* لون operators */
}

.article-content .chroma .p {                       /* فئات علامات الترقيم */
    color: var(--code-syntax-punctuation) !important; /* لون الأقواس والفواصل */
}

.article-content .chroma .c,
.article-content .chroma .ch,
.article-content .chroma .cm,
.article-content .chroma .c1,
.article-content .chroma .cs,
.article-content .chroma .cp,
.article-content .chroma .cpf,
.article-content .chroma .gu {                      /* فئات التعليقات */
    color: var(--code-syntax-comment) !important;   /* لون comments */
}

.article-content .chroma .hl {                      /* سطر مميز (highlight line) */
    background: var(--code-syntax-line-highlight) !important; /* خلفية تظليل السطر */
}

/* Headings: increase contrast + navigation clarity */
/* العناوين: وضوح أعلى + تحسين التنقل (خصوصاً عند الضغط على رابط عنوان) */
.article-content h2,
.article-content h3,
.article-content h4 {
    scroll-margin-top: 110px;                       /* يترك مسافة أعلى العنوان عند الانتقال إليه (حتى لا يختفي تحت الهيدر) */
}

.article-content h2 {                               /* عنوان مستوى 2 */
    color: var(--accent-color);                     /* لون العنوان */
    border-inline-start: 4px solid var(--accent-color); /* خط جانبي (يكون يسار في LTR ويمين في RTL) */
    padding-inline-start: 12px;                     /* مسافة داخلية بعد الخط الجانبي */
    padding-block: 4px;                             /* مسافة داخلية أعلى/أسفل */
    margin-top: 2.2em;                              /* مسافة فوق العنوان */
}

.article-content h2::after {                        /* خط فاصل بعد h2 */
    content: "";                                    /* عنصر وهمي */
    display: block;                                 /* يعرض كسطر */
    height: 1px;                                    /* سماكة الخط */
    margin-top: 0.65em;                             /* مسافة فوق الخط */
    background: var(--card-separator-color);        /* لون الخط الفاصل (من متغير الثيم) */
}

.article-content h3 {                               /* عنوان مستوى 3 */
    color: var(--card-text-color-main);             /* لون النص الأساسي للعناوين (من الثيم) */
    border-inline-start: 3px solid rgba(56, 189, 248, 0.35); /* خط جانبي خفيف */
    padding-inline-start: 10px;                     /* مسافة بعد الخط */
    margin-top: 1.8em;                              /* مسافة فوق العنوان */
}

html[lang="ar"] { /* عندما لغة الصفحة عربية */
    --base-font-family: "Noto Sans Arabic", "Tajawal", "Cairo", var(--sys-font-family), sans-serif; /* خط عام لكل الموقع */
    --article-font-family: "Noto Sans Arabic", "Tajawal", "Cairo", var(--sys-font-family), sans-serif; /* خط المقالات */
}

html[dir="rtl"] { /* عندما اتجاه الصفحة RTL */
    body {
        text-align: right;                          /* محاذاة نص الصفحة لليمين */
    }

    input,
    textarea {
        text-align: right;                          /* محاذاة النص داخل الحقول لليمين */
    }

    .article-content ul,
    .article-content ol {
        padding-right: 2rem;                        /* مسافة يمين للقوائم (بدل اليسار) */
        padding-left: 0;                            /* إلغاء مسافة اليسار */
    }

    /* Keep technical snippets and structured data readable in mixed-direction pages */
    /* نخلي الأشياء التقنية تقرأ طبيعي حتى لو الصفحة RTL */
    .article-content pre,
    .article-content code,
    .article-content table,
    .article-content kbd {
        direction: ltr;                             /* اتجاه يسار-ليمين داخل الكود/الجداول */
        text-align: left;                           /* محاذاة لليسار داخلها */
    }
}

```

إذا ما ظهر التغيير:
- Hard Refresh (CTRL + SHIFT + R)
- أو أعد تشغيل `hugo server -D`.

</details>

<details>
<summary><strong>تحديث الثيم بأمان (بدون ما تخسر شغلك)</strong></summary>

قبل التحديث: سو “Backup” سريع:

```bash
git status
git add .
git commit -m "backup before update"
```

تحديث الثيم:

```bash
hugo mod get -u github.com/CaiJimmy/hugo-theme-stack/v4
hugo mod tidy
```

تأكد إن كل شيء شغال:

```bash
hugo server -D
```

إذا تمام:

```bash
git add .
git commit -m "update theme"
git push origin main
```

</details>

<details>
<summary><strong>قالب مقال جاهز للنسخ</strong></summary>

````md
---
title: "عنوان المقال"
description: "وصف بسيط"
slug: "my-post-slug"
date: 2026-02-17T20:00:00+03:00
# image: cover.jpg
categories:
  - ابدأ هنا
tags:
  - hugo
draft: false
---

## مقدمة

اكتب مقدمة بسيطة.

## فيديو (اختياري)

{{< youtube "PUT_VIDEO_ID_HERE" >}}

## كود

```bash
echo "hello"
```

## الخلاصة

- نقطة 1
- نقطة 2
- نقطة 3
````

</details>
