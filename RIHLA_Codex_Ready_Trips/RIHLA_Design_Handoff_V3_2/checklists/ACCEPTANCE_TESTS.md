# Acceptance Checklist — رحلة V3.2

> ضع PASS / FAIL / NOT TESTED أمام كل بند عند التنفيذ. لا تغيّر تعريف الشرط لتنجح الاختبارات.

## A. Identity

- [ ] الاسم الأساسي في الـ UI هو «رحلة» دون ERP.
- [ ] الألوان الثمانية (`primary`, `hover`, `accent`, `soft`, `background`, `border`, `surface`, `shell`) متطابقة مع JSON.
- [ ] خط Almarai مع أوزانه الصحيحة على العناوين والحقول والجداول.
- [ ] واجهات المستخدم RTL، والأكواد المختلطة LTR عند الحاجة.
- [ ] لا وجود للون ذهبي ضمن الـ Branding.
- [ ] أيقونات الموديولات تأتي من Module registry، والشعار قابل للاستبدال.

## B. Desktop Shell

- [ ] الـ Sidebar يبدأ icon-only عند أول فتح.
- [ ] الضغط على Home أو أيقونة أخرى يحدث الـ Active ويغيّر القسم دون فتح Sidebar.
- [ ] Toggle داخل أعلى الـ Sidebar يفتح/يغلق تفاصيل القائمة فقط.
- [ ] الـ Submenu في الوضع الموسع تفتح/تغلق، ومؤشر الـ Chevron يدور بالحالة الصحيحة.
- [ ] الضغط على فراغ Sidebar يغلق الـ Submenu المفتوح دون إغلاق Sidebar نفسه.
- [ ] Header يظل ظاهرًا بعد فتح Overview/Components/Tables/Forms/Alerts والعودة.
- [ ] تمرير Main Workspace لأكثر من 1000px لا يحرك Header أو Sidebar.
- [ ] تمرير Workspace لا يحرك الـ body/window في سطح المكتب.
- [ ] في scrollTop=0 الركنان العلويان يمين وشمال 22px.
- [ ] في scrollTop>2px الركنان العلويان يصبحان 0px.
- [ ] عند الرجوع إلى scrollTop=0 تعود الاستدارة.
- [ ] عند reduced motion يتوقف animation الخاص بالـ radius.
- [ ] Header uses unified shell visual and central search; notifications icon is an obvious bell.

## C. Controls

- [ ] Click / keyboard focus / hover / disabled states مميزة وقابلة للفهم.
- [ ] التبويب Active يظل مميزًا حتى تغيير التبويب؛ Hover وحده لا يغير اختيارًا.
- [ ] زر Secondary / Ghost يعود لطبيعته بعد مغادرة الماوس.
- [ ] الحقل غير الصحيح يظهر علامة خطأ داخله ورسالة تحته.
- [ ] Checkbox وRadio يظهران بلون الهوية (ليس الأزرق الافتراضي).
- [ ] Custom Select يعمل: فتح/إغلاق/اختيار/Arrow/Enter/Escape/outside click.
- [ ] Calendar يعمل: السابق/التالي/اختيار يوم/اليوم/مسح، بدون Popup أصلي غير منسق.

## D. Data patterns and feedback

- [ ] جدول يدعم البحث والفرز والفلترة وتحديد متعدد وعرض حالات فارغة.
- [ ] التصدير لا يدعي النجاح إن لم ينشئ ملفًا حقيقيًا.
- [ ] Alerts الأربع واضحة، بشريط أيمن وألوان منفصلة عن Branding.
- [ ] Toasts لا تحجب إجراءات مهمة ولا تعتمد على اللون وحده.
- [ ] Modals تدير Focus وتدعم Escape/Cancel عند الحاجة.
- [ ] خطوات النموذج تتحقق قبل المتابعة وتعرض Progress مناسبًا.

## E. Engineering delivery

- [ ] تم استخدام مكونات قابلة لإعادة الاستخدام، دون Copy/Paste للـ prototype كله.
- [ ] لا يوجد hardcode لأيقونات العرض على أنها أسماء موديولات حقيقية.
- [ ] استُخدمت Contracts حقيقية فقط بعد مراجعة ملفات أعمال الموديولات.
- [ ] اجتازت الاختبارات البرمجية المعتمدة في المستودع.
- [ ] اجتاز اختبار GUI فعلي على مقاس Desktop الهدف، مع لقطات عند الإمكان.
- [ ] التغييرات والاختبارات والمخاطر موثقة بوضوح.
