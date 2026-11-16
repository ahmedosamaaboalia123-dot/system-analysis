# 03 — خطة التنفيذ المُلزمة: من المرجع إلى التطبيق

## المرحلة 0 — لا تبدأ بالكود قبل الفحص

**المخرجات:** Inventory لبنية المشروع الحالية: framework، routing، styling، component library، الاختبارات، وحدات العمل، الموجود من ملفات UI. **ممنوع** افتراض Electron أو Tauri أو React أو أي Stack بدون مراجعة المستودع.

## المرحلة 1 — تثبيت قرارات التصميم

- اعتمد `tokens/rihla-tokens.json` وملف CSS كمرجع واحد.
- أنشئ mapping بين Design Tokens ونظام الـ styling الفعلي بالمستودع.
- أضف Almarai بالأوزان الصحيحة. في الإنتاج يُفضل إدارة خط التطبيق محليًا وفق ترخيص التوزيع المناسب، لا الاعتماد القسري على إنترنت المتصفح.
- وثق النصوص والأرقام RTL/LTR.
- **Gate:** اختبار الباليت والخط والتحقق الذاتي من النتائج داخل مهمة Codex؛ لا توقف لطلب اعتماد وسيط في مهمة Trips Prototype.

## المرحلة 2 — App Shell أولًا (الأولوية القصوى)

- مكوّنات منطقية قابلة لإعادة الاستخدام لـ `AppShell`, `Header`, `Sidebar`, `WorkspaceScroll`؛ في النموذج المستقل يمكن تنظيمها بدوال render داخل HTML واحد.
- Header وSidebar خارج العنصر الذي يعمل scroll.
- CSS Grid/Flex مع `min-height:0` لعناصر Scroll الداخلية كي لا يبدأ Window scroll عن طريق الخطأ.
- Sidebar مختصر افتراضيًا، Toggle أعلى الـ Sidebar، collapsed click navigates only.
- Header بحث فعلي أو بحث demo واضح، إشعارات، حساب، إضافة سياقية.
- Adaptive Radius based on **workspace.scrollTop**, not window scroll.
- **Gate:** تحقق عمليًا من 4 أقسام مختلفة مع scroll طويل؛ وثّق النتيجة وواصل دون انتظار موافقة وسيطة.

## المرحلة 3 — المكونات الأساسية

1. Buttons: Primary, Secondary, Ghost, Danger, Disabled.
2. Tabs: persistent Active; Hover transient.
3. Inputs: focus/invalid, inline error icon + message.
4. Checkbox/Radio/Switch: brand color and keyboard support.
5. Custom Select and DatePicker.
6. Alerts and Toasts.

**Gate:** تحقق من حالات Component والـkeyboard والـdisabled ووثّق النتيجة وواصل.

## المرحلة 4 — Data-heavy patterns

- DataTable موحد، Filters toolbar، Search، Sort، Column selector، Density، Selection، Pagination، CSV export (منطقيًا).
- وجود bulk actions في UI لا يعني تشغيل إجراءات Backend قبل تكامل API والصلاحيات.
- **Gate:** اختبارات نتائج فارغة، نتائج كثيرة، نص عربي طويل، scroll وعرض شاشة ضيق؛ استمر بعد توثيقها.

## المرحلة 5 — Workflows

- Modal/Confirm، Stepper Forms، Validation، File Upload UI، Draft UI.
- حدد فواصل مسؤولية المكون والـ Module service.
- **Gate:** تحقّق من استعادة التركيز والـEscape ورسائل الخطأ وربط الحقول؛ استمر بعد توثيقها.

## المرحلة 6 — ربط الواجهات بالموديولات الحقيقية

- استخرج تسميات وأيقونات وروابط الموديولات من ملفات مواصفات الأعمال المعتمدة، **لا** من نموذج V3.2.
- كل Module يعلن navigation metadata؛ الـ Sidebar يعرضها من config بدل hardcoding.
- اللوغو modular وقابل للاستبدال بلا تغيير style tokens أو layout.
- **Gate:** لا صفحة موديول تحتوي على عنصر يبدو تفاعليًا دون سلوك؛ أبقِ المحاكاة معلّمة بوضوح.

## المرحلة 7 — ضمان الجودة والتسليم

- اختبارات وحدة للتوابع المتعلقة بالـ navigation/state/validation.
- اختبارات متصفح أو GUI فعلية للـ Shell وResponsive وRTL، لا تكتفِ بفحص Syntax فقط.
- اختبار بصري baseline للـ screenshot المعتمد ومع حالات Collapse/Expand/Scroll.
- اجتز `checklists/ACCEPTANCE_TESTS.md`؛ وثق الاستثناءات.
- سلم changelog يشمل files touched وtests run والقيود المعروفة.

## قواعد إدارة التغيير

- لا تغيّر الباليت أو التايبوغرافي أو Shell geometry إلا بطلب صريح.
- إذا اقتُرح تحسين جديد، اعرض مقارنة ومبررًا وحدد أثره على باقي الموديولات أولًا.
- حافظ على backward compatibility لمكونات الواجهات قدر الإمكان؛ ممنوع إدخال CSS overrides متناثرة بدلاً من إصلاح tokens/components.

## استثناء مهمة Trips Prototype (2026-11-16)

هذه الخطة أصلًا خطة تطبيق نظام التصميم على مشروع إنتاجي، لكن عند تنفيذ موديول الرحلات كـ **Standalone HTML Functional Prototype**: كل Gate هو تحقق/اختبار داخلي وليس طلب موافقة بشرية، ويُستكمل التنفيذ والـQA تلقائيًا داخل المهمة الواحدة. لا تُفسَّر هذه الفقرة كتغيير في الـDesign Decisions أو استثناء لمراجعة الدمج في `main`.
