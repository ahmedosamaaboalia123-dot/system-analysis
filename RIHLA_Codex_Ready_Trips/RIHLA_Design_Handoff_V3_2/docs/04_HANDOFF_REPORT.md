# 04 — Design Handoff Report | تقرير التسليم

## 1. ملخص القرار

تم اعتماد **اتجاه التصميم العام** لواجهة رحلة Desktop حتى V3.2. القرار يشمل: الباليت، الخط، App Shell، تبويبات ومكونات الإدخال، التفاعلات والحالات، نماذج العمل، Alerts، وجزء من سلوك الـ Navigation. **الشعار وأيقونات الموديولات استثناء مقصود:** يمكن استبدالهما لاحقًا.

## 2. النطاق

**داخل النطاق:** نظام بصري وشكل مكونات قابل لإعادة البناء، حالات تفاعلية، مرجع HTML، Tokens، وخطة تنفيذ.

**خارج النطاق:** backend/database/business workflows، الصلاحيات الحقيقية، عمليات الحجز، حفظ مستندات فعلية، إنتاج تطبيق Windows قابل للتثبيت، أو إصدار نهائي للشعار.

## 3. أهم المعالم من V3.2

- App Shell موحد باللون `#E4E9E6`؛ خلفية سطح العمل الرئيسية بيضاء.
- Sidebar يبدأ مختصرًا، والضغط على الأيقونة لا يوسعه.
- Header وSidebar ثابتان أثناء التنقل؛ Main Workspace فقط scroll.
- Adaptive Corner: 22px عند قمة التمرير؛ 0px بعد بدء Scroll؛ 16px في العرض الصغير حسب المرجع.
- لون Checkboxes/Radio ليس browser default blue.
- Alerts أكثر تباينًا، مع شريط رأسي أيمن واضح.
- RTL وAlmarai ولوحة الألوان Graphite المحددة في ملف Tokens.

## 4. توصيات للمطور

- **لا تنسخ صفحة HTML داخل المنتج النهائي:** الصفحة تعرض نسخ CSS متراكبة وبيانات للتجريب، وليست component architecture.
- أنشئ Storybook/Component Gallery إن كان ضمن stack المشروع، واختبر الحالات التفاعلية والـ visual regression.
- وثّق Navigation tree من قائمة الموديولات وPermissions الحقيقية عندما تُربط.
- استخدم semantic colors للرسائل الوظيفية، ولا تحول `warning` إلى اللون الذهبي في هوية العلامة.

## 5. مخاطر ينبغي الانتباه لها

1. **اختلاف العرض بين المتصفحات:** Custom Select/Calendar/scrollbar تتطلب اختبارًا فعليًا على بيئة Windows target.
2. **Font source:** معاينة HTML تحمل Google Font من الإنترنت؛ بناء Windows Desktop النهائي يحتاج استراتيجية Bundling أو Fallback مناسبة.
3. **بيانات تجريبية:** كل أرقام الرحلات والعمليات في Demo ليست مواصفات أعمال.
4. **Icon mismatch:** أيقونات الـ Sidebar الحالية أمثلة؛ لا تستخدمها لتخمين أسماء/وظائف الموديولات.
5. **Legacy CSS:** ملف HTML يحتوي على Override history؛ استخدم ملفات tokens والمواصفات لبناء clean UI.
6. **Visual QA:** ZIP مكتمل كحزمة توثيق، لكن نجاح جميع تفاعلاتها على بيئة المستخدم النهائية يحتاج اختبارات المشروع نفسها.

## 6. تعريف الاعتماد

**Approved:** Direction/design tokens/interactions.  
**Replaceable:** Logo + icons + actual module nav details.  
**To validate during build:** Desktop framework behavior, browser/GUI integration, accessibility audits and module-specific data rules.
