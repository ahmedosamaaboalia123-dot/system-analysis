# Codex — تنفيذ موديول الرحلات كاملًا (مهمة واحدة)

أنت Frontend Implementation + QA Engineer لمشروع «رحلة» (RIHLA). نفّذ **نموذجًا وظيفيًا تفاعليًا كاملًا** لموديول الرحلات باستخدام HTML وCSS وVanilla JavaScript في ملف `modules/trips/code/index.html` واحد. النموذج مرجع للتسليم إلى مطور Backend لاحقًا، وليس Backend فعليًا.

## افحص أولًا
1. افحص المستودع والـbranch الحالي وملفات الحزمة، واقرأ `AGENTS.md` و`RIHLA_Design_Handoff_V3_2/README.md` و`RIHLA_Design_Handoff_V3_2/AGENTS.md` وجميع `docs/`, `tokens/`, `checklists/` ومرجع HTML في `reference/`.
2. اقرأ `modules/trips/موديويل الرحلات(1).txt` و`modules/trips/User_Story.txt` و`modules/trips/Codex_Instructions.txt` و`modules/trips/QA_Checklist.txt` و`modules/trips/Module_Report.md` كاملاً. المرجع التجاري هو المواصفات والـUser Stories، والمرجع البصري هو **Graphite V3.2** فقط.
3. أنشئ جدول traceability بأرقام `US-TR-*` و`QA-*` يربط المتطلبات بمواقع الـUI والاختبارات.

## طريقة التشغيل الذاتية
اكتب خطة داخل `Module_Report.md` ثم **واصل التنفيذ فورًا من المرحلة الأولى إلى التسليم، من دون انتظار رسالة أو موافقة بين المراحل**. هذا استثناء محدد من حواجز الموافقة المرحلية في مستندات الـDesign Handoff. لا تتجاوز صلاحيات GitHub أو تدمج في `main`، ولا تغيّر design decisions الثابتة. لو اصطدمت بمعلومة أعمال غير محسومة، اعرض demo-only behavior موثقًا أو BLOCKED واضحًا بدل فرض قاعدة إنتاجية.

## مراحل التنفيذ المتتابعة
- P0: Inventory + User Story/QA coverage map + تأكيد تصميم V3.2.
- P1: Shell/Sidebar/Header/Workspace، صفحة الرحلات، الحالات الست، إنشاء رحلة حقيقية وتجريبية، تفاصيل وتبويبات الرحلة.
- P2: إعدادات الطيران والفنادق والمشرفين والمواصلات والتسعير والمشتريات والهدايا والملاحظات وإعدادات الخدمات الخارجية.
- P3: المتابعة والمؤشرات والتحذيرات والـTimeline والأحداث اليدوية.
- P4: إدارة العملاء/المعتمرين داخل الرحلة، التسجيل، بيانات الأسر والمجموعات، المستندات، التسكين، الطلبات، الفلاتر.
- P5: التحويلات وفروق الأسعار والمحافظة على اتساق السعات؛ تجربة Edge Cases وتدفقات التفاعل.
- P6: QA حقيقي، RTL/Accessibility، responsive، أمان نصوص المستخدم، persistence عبر localStorage، Reset Demo Data، إصلاح العيوب، تحديث التقرير.

## المتطلبات التقنية والجودة
- HTML/CSS/JS في ملف واحد، يفتح مباشرة عبر browser محلي وبدون build tools أو CDN JavaScript. يسمح خط Almarai من Google Fonts مع fallback؛ الواجهة لا تتعطل لو الخط لم يحمل.
- استخدم Design Tokens المعتمدة من حزمة V3.2، وليس الباليت Forest Green القديمة. Header + Sidebar ثابتان؛ Workspace فقط scroll؛ collapsed sidebar افتراضيًا؛ التوسيع عبر toggle؛ radius سلوكي؛ custom dropdowns/calendar والتفاعل بالكيبورد.
- كل عنصر تفاعلي يعمل أو يكون Disabled مع سبب؛ لا تعمل dead buttons أو fake backend calls. استخدم بيانات وهمية فقط.
- State مركزية، IDs ثابتة، بيانات وحسابات مشتقة متسقة، localStorage وReset مع تأكيد. لا duplicate سجلات أو حجز نفس السعة مرتين؛ احرص على فصل external tickets/hotels عن أرصدة الشركة وعلى عدم جمع سعات مكة والمدينة كأنها طاقة إجمالية واحدة.
- لا تجعل مدخلات المستخدم تنفذ HTML/JS غير آمن؛ ضع قواعد تحقق ورسائل عربية.
- نفذ **كل** المعايير المذكورة في `User_Story.txt` حتى لو لم تُذكر أعلاه.

## الاختبار والتسليم
- نفّذ اختبارات متصفح فعلية إن كانت الأدوات متاحة؛ اختبارات JS وحدها لا تُغني عن Browser UI test. تحقّق من Console وNavigation وforms وfilters وcapacity وtransfers وrefresh وresponsive وkeyboard وRTL.
- حدّث QA_Checklist بعلامات PASS/FAIL/BLOCKED/NOT TESTED، واذكر أوامر الاختبار/الخطوات والنتائج والدليل. لا تكتب PASS من غير اختبار فعلًا.
- حدّث `Module_Report.md` بكل مرحلة: المنفّذ فعليًا، محاكاة فقط، القرارات المفتوحة، الاختبارات، المشاكل المتبقية وملاحظات Backend handoff.
- اعمل commit على `feature/trips-ui-prototype` (أنشئ الفرع إذا مسموح)، وافتح Pull Request للمراجعة إذا توفر؛ **لا تدمج في main**.
- لا توقف المهمة بين المراحل، لكن لو انتهت الموارد أو كان هناك مانع حقيقي، احفظ التقدم واذكر المتبقي ولا تدّع تسليمًا مكتملًا.

ابدأ الآن بالقراءة ثم التنفيذ والاختبارات المتتابعة حتى أقصى نطاق ممكن.
