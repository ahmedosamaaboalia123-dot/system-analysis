# 02 — Component Catalog & Interaction Contract

> كل مكوّن هنا هو **عقد تصميم وسلوك** ينبغي تنفيذه على شكل عنصر مستقل قابل للاستخدام عبر الموديولات.

## 1. AppShell

**Props/States:** `sidebarExpanded`, `activeModule`, `activeSubPage`, `workspaceScrolled`, `currentBranch` (إذا كان ذلك ضمن أعمال المشروع).

- Desktop: Header أعلى الـ Main، Sidebar يمينًا، Workspace داخله فقط scroll.
- `sidebarExpanded=false` عند التشغيل لأول مرة (أو عند اتباع التفضيل المحفوظ إذا قرر المشروع حفظه).
- Header بارتفاع مرجعي 66px وSidebar مختصر ~76px وموسع ~254px.
- `workspaceScrolled := scrollTop > 2` متغير مشتق من عنصر Workspace نفسه (وليس window scroll).
- top corners 22px عندما false، وصفر عندما true؛ transition 180ms فقط إذا سمحت إعدادات reduced motion.
- التنقل أثناء Collapse لا يوسع تلقائيًا ولا يمسح الاختيار النشط.
- `aria-expanded` على زر التوسيع؛ تسميات accessibility وtooltips للأيقونات عند Collapse.

## 2. Sidebar Navigation

- الأقسام العليا تستمد من module registry حقيقي، وليس أيقونات الـ HTML التجريبية.
- عند Collapse: الأيقونة فقط مع Tooltip وعلامة Active.
- الضغط على رمز القسم = تنفيذ navigation مباشرة إلى الصفحة الافتراضية له، **لا** استدعاء expand.
- الضغط على Toggle أعلى الـ Sidebar = expand/collapse.
- عند Expanded: تسميات + عناصر فرعية؛ indicator Chevron outline صغير يدور بين الحالة المغلقة والمفتوحة.
- الضغط على مساحة sidebar فارغة = collapse لأي submenu مفتوح فقط، وليس collapse للـ Sidebar نفسه.
- تجنب القوائم الفرعية الافتراضية غير المبررة لكل موديول؛ اعتمد البنية الحقيقية من المواصفات.

## 3. Header

- بصريًا جزء من `app-shell`، وليس بطاقة مستقلة بيضاء ذات shadow ثقيل.
- مجموعة واضحة ومختصرة: المسار/الاسم، بحث سريع، إنشاء سريع سياقي، إشعارات بجرس، حساب مستخدم. لا إضافات تسويقية أو أزرار غامضة.
- البحث لا يحتاج الانتقال في المعاينة إلى Backend؛ عند الإنتاج ربطه ببحث حقيقي أو قائمة اختصارات صالحة.
- `Ctrl+K` يصل للبحث إذا لم يتعارض مع إطار التطبيق.
- لا تُحرك الصفحة بالكامل عند عرض dropdown أو notifications.

## 4. Typography and Spacing

| العنصر | حجم مرجعي | الوزن |
|---|---:|---:|
| عنوان الصفحة | 24px | 700 |
| عنوان القسم | 20px | 700 |
| عنوان بطاقة | 16px | 700 |
| النص الأساسي | 14px | 400 |
| نص زر | 14px | 700 |
| خلايا الجدول | 13px | 400 |
| وصف مساعد | 12px | 400 |
| KPI بارز | 28px | 800 |

الـ Scale أعلاه معتمد مبدئيًا ضمن مكتبة الهوية السابقة، ويحتاج مراجعة بصريّة عبر بيانات حقيقية. `4px` spacing unit أساس مرجعي.

## 5. Buttons and Tabs

- `Primary`, `Secondary/Soft`, `Ghost`, `Danger`, `Disabled`, `Loading`.
- Hover مؤقت، وFocus واضح. `Danger` فقط للإجراءات الخطيرة.
- الفرق مهم: Tabs تمنح حالة `active` دائمة؛ Action buttons لا تصبح Tabs عند الضغط.
- أبعاد مرجعية: Button 42px، صغير 34px، كبير 48px؛ Radius نحو 9px.

## 6. Fields and Validation

- Input height ~44px. Labels فوق الحقل.
- State: default/hover/focus/invalid/disabled/readonly.
- Invalid: border ملوّن، indicator **داخل الحقل**، رسالة أسفله؛ احتفظ أيضًا بنص الخطأ في DOM لبرامج القراءة.
- RTL للحقول العربية؛ أكواد مثل `TR-2026-001` يمكن أن تكون LTR.

## 7. Custom Dropdown

- عند الفتح: surface بيضاء، border رقيق، radius وshadow هادئ.
- Hover للخيار واضح، selected soft background / primary text؛ لا browser default blue list.
- اغلق عند اختيار عنصر، Escape، أو الضغط خارجه؛ دعم Arrow keys/Enter/Space؛ `aria-expanded` و`role=listbox` وفق التنفيذ المستخدم.

## 8. Calendar / DatePicker

- تقويم مخصص بألوان التصميم، RTL، تنقل بين الشهور، اختيار اليوم، زر اليوم ومسح.
- التاريخ المختار يظهر داخل الحقل؛ دعم invalid date وقيود المغادرة/العودة عند ربط منطق الموديول.
- لا استخدام للشكل الافتراضي للـ browser calendar في الواجهة المعتمدة.

## 9. Tables & Filters

- بحث، فرز، فلاتر، إظهار/إخفاء أعمدة، كثافة العرض، Pagination، تحديد متعدد، actions جماعية، Export.
- صفوف hover قابلة للقراءة؛ Checkboxes بلون `--primary` بدل الأزرق الافتراضي.
- لا تنفذ Bulk delete حقيقي اعتمادًا على عرض HTML التجريبي؛ يحتاج صلاحيات وتأكيدًا من مواصفات الموديول.
- في الجداول الكبيرة: وثق loading/empty/error states وتعامل مع wide tables دون كسر RTL.

## 10. Alerts & Toasts

| الحالة | الخلفية | حد جانبي على اليمين |
|---|---|---|
| Success | `#DCEFE2` | `#27734B` |
| Info | `#E1EEF8` | `#3479AC` |
| Warning | `#FFF0CF` | `#AF741B` |
| Error | `#FBE1E3` | `#C13F50` |

- الشرائط الملونة يجب أن تكون مرئية بوضوح، والتباين مقروء. الـ Alert يصف المشكلة أو النتيجة، ليس مجرد لون.
- Toast feedback مؤقت، ولا يغني عن Alert المستمر أو رسالة validation الملاصقة للحقول.

## 11. Modals and Multi-step Forms

- Modal لغرض محدد: معلومات/تأكيد/إجراء خطر. التحذيرات المصيرية توضح أثر الإجراء بوضوح.
- Stepper يوضح الحالي والمكتمل والقادم؛ تحقق قبل الانتقال وأرسل التركيز لأول حقل خطأ.
- Autosave ودعم draft/file upload في المرجع **محاكاة**؛ في الإنتاج قرر التخزين الفعلي والصلاحيات وحدود الملفات من مواصفات الموديولات.
- Modal: إغلاق via Escape عند السماح، Focus trap، استعادة Focus للعنصر الذي فتحه.

## 12. Assets and Iconography

- استخدم مكتبة Outline متسقة الحجم/السماكة (مثل Lucide إن كانت مناسبة للمشروع)، وأضف mapping في ملف مخصص.
- أيقونات المعاينة مستعارة للاتجاه البصري **وليست** أسماء موديولات معتمدة.
- الشعار الحالي SVG مؤقت ويجب أن يمكن تبديله بملف نهائي بسهولة.
