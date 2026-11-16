# رحلة | RIHLA Design System — Approved UI Handoff V3.2

**حالة الحزمة:** مرجع تصميم معتمد (Design Reference)، **وليس** تطبيقًا جاهزًا للإنتاج.

**تاريخ الحزمة:** 2026-11-16  
**المنتج:** «رحلة» — نظام إدارة شركات الحج والعمرة، تطبيق Desktop بواجهات عربية RTL.  
**خط الواجهات المعتمد:** Almarai  
**باليت الألوان المعتمدة:** Graphite/Green Neutral حسب `tokens/rihla-tokens.css`.

## ابدأ من هنا

1. افتح `reference/RIHLA_Design_System_V3_2_REFERENCE.html` في المتصفح، وراجع الشكل والتفاعلات. الاتصال بالإنترنت مطلوب لتحميل خط Almarai من Google Fonts في المرجع الحالي.
2. اقرأ `docs/01_DESIGN_DECISIONS.md` لفهم القرارات التي **لا يجوز تغييرها**.
3. اقرأ `docs/02_COMPONENTS_AND_BEHAVIOR.md` لفهم سلوك كل مكون وحالاته.
4. اقرأ `docs/03_IMPLEMENTATION_PLAN.md` لتسلسل تنفيذ صارم وآمن.
5. شغّل تنفيذ المهام في المستودع الأصلي بعد قراءة `AGENTS.md`، ثم استخدم `checklists/ACCEPTANCE_TESTS.md` للمراجعة.
6. استعمل `tokens/rihla-tokens.css` أو `tokens/rihla-tokens.json` كمصدر موحد للألوان؛ لا تنسخ القيم من أماكن متعددة.

## هيكل الحزمة

```text
RIHLA_Design_Handoff_V3_2/
├── README.md
├── AGENTS.md
├── manifest.json
├── reference/
│   └── RIHLA_Design_System_V3_2_REFERENCE.html
├── tokens/
│   ├── rihla-tokens.css
│   └── rihla-tokens.json
├── docs/
│   ├── 01_DESIGN_DECISIONS.md
│   ├── 02_COMPONENTS_AND_BEHAVIOR.md
│   ├── 03_IMPLEMENTATION_PLAN.md
│   ├── 04_HANDOFF_REPORT.md
│   └── 05_CODEX_START_PROMPT.md
└── checklists/
    └── ACCEPTANCE_TESTS.md
```

## قاعدة مهمة

**الـ HTML مرجع للمظهر والسلوك وليس ملفًا يجب نسخه إلى التطبيق.** يحتوي على بيانات محاكاة وتجارب، وعلى CSS أُضيف عبر عدة إصدارات. المطلوب تنفيذ **مكونات نظيفة وقابلة لإعادة الاستخدام** داخل تقنية المشروع الفعلية، وليس تغليف الصفحة القديمة أو لصق الـ CSS/JavaScript كما هو.

## ما هو ثابت، وما هو غير ثابت؟

| العنصر | الحالة |
|---|---|
| اتجاه التصميم، App Shell، تخطيط Header/Sidebar/Workspace | **معتمد** |
| Graphite palette، خط Almarai، RTL، الحالات والتفاعلات | **معتمد** |
| شريط أيقونات مختصر افتراضيًا + فتح يدوي من الزر | **معتمد** |
| Header وSidebar ثابتان؛ التمرير داخل Workspace فقط | **معتمد** |
| Adaptive top radius لمساحة العمل (عند الأعلى فقط) | **معتمد** |
| رمز/شعار «رحلة» الحالي | **مؤقت وقابل للاستبدال** |
| أيقونات الأقسام في صفحة المعاينة | **أمثلة مؤقتة**؛ تُستبدل حسب الموديولات الفعلية |
| بيانات رحلات، مستخدمين، فروع، تنبيهات في HTML | **تجريبية وغير ملزمة** |
| البنية الخلفية وقاعدة البيانات واختيار Desktop framework | **غير محددة في هذا المرجع**؛ لا تفترضها |

## لطلب التنفيذ من Codex

لمهمة الرحلات استخدم `START_CODEX_HERE.md` الموجود في جذر حزمة التسليم المجمعة؛ `docs/05_CODEX_START_PROMPT.md` يحيل إليه. تعليمات `AGENTS.md` هنا مخصصة لتصميم V3.2 مع استثناء واضح لاستمرار مراحل Trips Prototype دون انتظار موافقات مرحلية.

## حدود التسليم

هذه الحزمة توثق واجهة التصميم وتجربتها؛ **لا** تعتمد وحدها مواصفات أعمال الموديولات أو الصلاحيات أو قاعدة البيانات أو قواعد الحجوزات المالية. هذه تؤخذ من ملفات مواصفات الموديولات المعتمدة، كل على حدة.
