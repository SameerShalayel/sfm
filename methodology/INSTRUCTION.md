# تعليمات تنفيذ المنهجية المرحلية (Stage-Gate SDLC)

## المدخل

عرض مشكلة من **3-6 أسطر** يصف:
- من هو المتأثر
- ما هي المشكلة الحالية
- ما هو الحل المطلوب بشكل عام

### مثال مدخل:
```
عيادة أسنان صغيرة فيها 3 أطباء. المرضى يتصلون بالتلفون لحجز مواعيد
والموظفة تكتب الحجوزات على ورقة. كل يوم يصير لخبطة: مريضين يجون نفس
الوقت، مواعيد تنكتب غلط، والدكتور يضيع وقته يسأل 'مين الجاي؟'. المرضى
يزعلون والعيادة تخسر زبائن.
```

---

## المرحلة PD — اكتشاف المشكلة (Problem Discovery)

### المطلوب:
من وصف المشكلة، أنتج 8 عقد (nodes):

### 1. Problem Summary (`pd-summary-node`)
```json
{
  "label": "Problem Summary",
  "description": "وصف المشكلة كاملاً بلغة بسيطة",
  "points": [
    "نقطة 1 — ملخص الوضع الحالي",
    "نقطة 2 — ما الذي لا يعمل",
    "نقطة 3 — النتيجة السلبية",
    "نقطة 4 — من يتأثر",
    "نقطة 5 — لماذا الحل مطلوب الآن"
  ]
}
```

### 2. Actors (`pd-actors-node`)
```json
{
  "label": "Actors",
  "description": "الأطراف المتأثرة بالمشكلة",
  "points": [
    "الطرف 1 — دوره وما يريده",
    "الطرف 2 — دوره وما يريده",
    "..."
  ]
}
```

### 3. Goals (`pd-goals-node`)
```json
{
  "label": "Goals",
  "description": "الأهداف المرجوة (غير تقنية)",
  "points": [
    "هدف 1 — قابل للقياس",
    "هدف 2 — قابل للقياس",
    "..."
  ]
}
```

### 4. Pain Points (`pd-pain-points-node`)
```json
{
  "label": "Pain Points",
  "description": "نقاط الألم الحالية — ما الذي يسبب المعاناة",
  "points": [
    "ألم 1 — وصف محدد وليس عام",
    "ألم 2 — مع مثال واقعي إن أمكن",
    "..."
  ]
}
```

### 5. Constraints (`pd-constraints-node`)
```json
{
  "label": "Constraints",
  "description": "القيود والمحددات",
  "points": [
    "ما لا نتعامل معه",
    "القيود التقنية",
    "القيود المالية/الزمنية",
    "..."
  ]
}
```

### 6. Scope (`pd-scope-node`)
```json
{
  "label": "Scope",
  "description": "نطاق العمل",
  "inScope": ["ما سنبنيه"],
  "outScope": ["ما لن نبنيه"]
}
```

### 7. Success Signals (`pd-signals-node`)
```json
{
  "label": "Success Signals",
  "description": "مؤشرات نجاح قابلة للقياس",
  "points": ["مؤشر 1 — قابل للتحقق", "..."]
}
```

### 8. Unknowns (`pd-unknowns-node`)
```json
{
  "label": "Unknowns",
  "description": "أسئلة مفتوحة تحتاج إجابة من صاحب المشكلة",
  "points": ["سؤال 1", "سؤال 2", "..."]
}
```

### البوابة: PD Lock Gate
```json
{
  "type": "gate-problem",
  "gateStatus": "pending",
  "decisionAuthority": "Human Only",
  "gateChecklist": [
    "Summary واضح ومفهوم",
    "الأطراف محددة بأسمائهم",
    "الأهداف غير تقنية وقابلة للقياس",
    "نقاط الألم صريحة ومحددة",
    "النطاق محدد — فيه in و out",
    "مؤشرات النجاح قابلة للتحقق"
  ]
}
```

**⛔ لا تنتقل إلى S0 قبل موافقة الإنسان على هذه البوابة.**

---

## المرحلة S0 — قفل المشكلة (Problem Lock)

### المطلوب:
من مخرجات PD، أنتج 4 عقد:

### 1. Problem Lock (`s0-stage`)
```json
{
  "label": "Problem Lock",
  "description": "تأكيد وقفل تعريف المشكلة",
  "points": [
    "المشكلة: [جملة واحدة واضحة]",
    "النتيجة: [ما يحدث بسبب المشكلة]",
    "الحل المطلوب: [وصف عام للحل]",
    "القيد: [ما لا يشمله الحل]"
  ]
}
```

### 2. Problem Insight (`s0-insight-node`)
```json
{
  "label": "Problem Insight",
  "description": "فهم عميق لجذر المشكلة — ليس الأعراض",
  "points": [
    "الجذر الحقيقي: [ليست المشكلة تقنية بل ...]",
    "نقطة الفشل: [أين بالضبط ينكسر النظام]",
    "لماذا يحدث: [السبب الهيكلي]",
    "من الأعمى: [من لا يرى الصورة الكاملة]"
  ]
}
```

### 3. Desired Outcome (`s0-outcome-node`)
```json
{
  "label": "Desired Outcome",
  "description": "النتائج المرجوة — ما سيتغير بعد الحل",
  "points": ["نتيجة 1", "نتيجة 2", "..."]
}
```

### 4. Strategic Direction (`s0-direction-node`)
```json
{
  "label": "Strategic Direction",
  "description": "أين نروح وأين لا نروح",
  "points": [
    "نروح لـ: [اتجاه 1]",
    "نروح لـ: [اتجاه 2]",
    "ما نروح لـ: [ما نتجنبه 1]",
    "ما نروح لـ: [ما نتجنبه 2]"
  ]
}
```

### البوابة: Problem Gate
```json
{
  "type": "gate-problem",
  "gateStatus": "pending",
  "decisionAuthority": "Human Only",
  "gateChecklist": [
    "المشكلة واضحة ومحددة — ليست عامة",
    "جذر المشكلة مفهوم (ليس أعراض فقط)",
    "النتائج المرجوة قابلة للقياس",
    "الاتجاه الاستراتيجي يحدد أين نروح وأين لا",
    "القيود واضحة ومتفق عليها"
  ]
}
```

---

## المرحلة S1 — شكل المنتج (Product Shape)

### المطلوب:
أنتج 6 عقد:

### 1. Product Shape (`s1-stage`)
- رؤية المنتج
- حدود الـ MVP
- الفرق عن الحل الحالي

### 2. Product Insight (`s1-product-insight-node`)
- من المستخدم الأول (إذا لم يستخدمه هو، فشل المنتج)
- ما الأهم: البساطة أم الميزات
- ما الألم الأكبر الذي يجب أن يكون مستحيل تقنياً

### 3. User Personas (`s1-actors-node`)
- كل مستخدم: اسمه → ماذا يفعل → ما يحتاج
- تمييز v1 عن v2 (ما خارج MVP)

### 4. Feature Modules (`s1-modules-node`)
- كل وحدة وظيفية بالاسم والوصف
- مثال: `DoctorSelector — عرض tabs الأطباء`

### 5. User Procedures (`s1-procedures-node`)
- خطوات سير العمل مرقمة
- من فتح الصفحة حتى إتمام المهمة
- القواعد الصارمة (Hard Rules)

### 6. MVP Boundary (`s1-boundary-node`)
- قائمة بـ ✅ (داخل MVP) و ❌ (خارج MVP)

### البوابة: Product Gate

---

## المرحلة S2 — الهيكل المعماري (Architecture)

### المطلوب:
أنتج 6 عقد:

### 1. Architecture Spine (`s2-stage`)
- نوع التطبيق (SPA, SSR, API, etc.)
- التقنيات المختارة (ولماذا)
- Responsive / RTL / etc.

### 2. Domain Model (`s2-domains-node`)
- كل كيان: `{ الاسم, الخصائص, العلاقات }`
- مثال: `Doctor: { index, name, color }`

### 3. System Components (`s2-components-node`)
- كل مكون: اسمه + نوعه (UI/Logic/Data) + مسؤوليته
- مثال: `BookingEngine (Logic): check-then-write atomically`

### 4. Component Interactions (`s2-interactions-node`)
- كل تفاعل: `المكون A → المكون B: ماذا يرسل`
- مثال: `SlotGrid → BookingForm: يرسل slotIndex + doctorIndex`

### 5. Data Domains (`s2-data-domains-node`)
- نوع التخزين (localStorage, PostgreSQL, etc.)
- الشكل (format): JSON, SQL tables, etc.
- القيود: unique keys, no overwrite, etc.

### 6. Tech Constraints (`s2-constraints-node`)
- ما لا نستخدمه ولماذا
- حدود التقنية (5MB localStorage, no server, etc.)

### البوابة: Architecture Gate

---

## المرحلة S3 — التخطيط للتنفيذ (Development)

### المطلوب:
أنتج 5 عقد:

### 1. Production Slice (`s3-stage`)
- ما هي أول شريحة عمودية (vertical slice)
- لماذا هذه الشريحة أولاً
- **ملاحظة**: إذا النظام كبير، قسّمه لعدة شرائح (مثل: hospital_s3.json فيه 4 شرائح)

### 2. Feature Slice (`s3-slice-node`)
- طبقات الشريحة: UI + Logic + Data + Feedback
- المخرج المتوقع من الشريحة

### 3. API Contract (`s3-contract-node`)
- كل دالة/endpoint: التوقيع + المدخلات + المخرجات
- القواعد: متى يفشل ومتى ينجح
- مثال: `bookSlot(doctor, slot, name) → { success: bool, message: string }`

### 4. Data Model (`s3-data-model-node`)
- المفتاح والقيمة والعلاقات
- القيود (constraints)
- مثال: `Key: 'clinic_bookings', Value: { '0_3': 'محمد أحمد' }`

### 5. Task Breakdown (`s3-task-plan-node`)
- مهام مرقمة ومتسلسلة
- كل مهمة تشير لمكون من S2

### البوابة: Slice Gate [Human + AI]

---

## المرحلة S4 — البناء (Build)

### المطلوب:
أنتج 5 عقد:

### 1. Code Implementation (`s4-stage`)
- الملفات المطلوبة
- حدود الكود (budget بالأسطر)
- لا dependencies خارجية (أو حدد أيها)

### 2. Code Structure (`s4-code-structure-node`)
- شجرة الملفات
- كل ملف ومحتواه

### 3. Frontend/Backend Code (`s4-frontend-node` / `s4-backend-node`)
- تفاصيل التنفيذ لكل طبقة
- HTML/CSS/JS أو API endpoints
- عدد الأسطر التقريبي

### 4. Code Validation (`s4-validation-node`)
- Traceability: كل function ← أي task ← أي component ← أي feature
- لا dead code
- Budget check

### 5. Integration (`s4-integration-node`)
- كيف المكونات تتكامل فعلياً
- كل تكامل: A ↔ B: ماذا يحدث

### البوابة: Code Gate [Human + AI]

---

## المرحلة S5 — الاختبار والجودة (Release)

### المطلوب:
أنتج 6 عقد:

### 1. Quality Assurance (`s5-stage`)
- عدد الاختبارات الإجمالي
- الهدف: 100% pass rate

### 2. Test Plan (`s5-test-plan-node`)
- مجموعات الاختبار (Suites)
- كل اختبار مرتبط بمرجع من S1/S2/S3

### 3. Unit Tests (`s5-unit-test-node`)
- اختبارات Hard Rules
- كل اختبار: المعرّف + الوصف + النتيجة

### 4. Integration Tests (`s5-integration-test-node`)
- اختبارات User Flows
- من فتح الصفحة حتى إكمال المهمة

### 5. Acceptance Tests (`s5-acceptance-node`)
- اختبارات Success Criteria من PD
- سيناريوهات حقيقية من وجهة نظر المستخدم

### 6. Bug Tracking (`s5-bug-node`)
- الأخطاء المكتشفة وحالتها
- Quality Score

### البوابة: Quality Gate [Human]

---

## المرحلة S6 — النشر والتعلم (Learn & Iterate)

### المطلوب:
أنتج 6 عقد:

### 1. Production Release (`s6-stage`)
- رقم النسخة
- حجم الملف
- نتائج الاختبارات

### 2. Release Package (`s6-release-node`)
- الملفات المطلوبة للنشر
- هل فيه build step أو لا

### 3. Deploy Checklist (`s6-deploy-checklist-node`)
- قائمة تحقق شاملة (8+ بنود)
- كل بند: ✅ أو ❌

### 4. Rollback Plan (`s6-rollback-node`)
- السيناريو: ماذا لو فشل
- الخطة: كيف نرجع
- الوقت المتوقع

### 5. Documentation (`s6-docs-node`)
- دليل المستخدم
- دليل فني
- الدروس المستفادة

### 6. Handoff (`s6-handoff-node`)
- لمن نسلم
- ماذا يشمل التسليم
- خطة الدعم والتدريب
- التطوير القادم (v2)

### البوابة: Release Gate [Human Only]

---

## بنية ملف JSON المخرج

كل ملف JSON يتبع هذا الشكل:

```json
{
  "nodes": [
    {
      "id": "unique-id",
      "type": "node-type",
      "data": {
        "label": "اسم العقدة",
        "description": "وصف العقدة",
        "points": ["نقطة 1", "نقطة 2"]
      },
      "position": { "x": 0, "y": 0 },
      "width": 360,
      "height": 260,
      "parentId": "group-id",
      "extent": "parent"
    }
  ],
  "edges": [
    {
      "id": "edge-id",
      "type": "custom",
      "source": "node-id-1",
      "target": "node-id-2"
    }
  ],
  "evidence": [],
  "exportedAt": "ISO-date"
}
```

## تسمية المعرّفات

| المرحلة | Group ID | Node ID Pattern |
|---------|----------|-----------------|
| PD | `group-pd-{date}-{project}` | `pd-{type}-{index}` |
| S0 | `group-s0-{date}-{project}` | `s0-{type}-{index}` |
| S1 | `group-s1-{date}-{project}` | `s1-{type}-{index}` |
| S2 | `group-s2-{date}-{project}` | `s2-{type}-{index}` |
| S3 | `group-s3-{date}-{project}` | `s3-{type}-{index}` |
| S4 | `group-s4-{date}-{project}` | `s4-{type}-{index}` |
| S5 | `group-s5-{date}-{project}` | `s5-{type}-{index}` |
| S6 | `group-s6-{date}-{project}` | `s6-{type}-{index}` |

## أنواع العقد (Node Types)

### PD
`pd-summary-node`, `pd-actors-node`, `pd-goals-node`, `pd-pain-points-node`, `pd-constraints-node`, `pd-scope-node`, `pd-signals-node`, `pd-unknowns-node`, `gate-problem`

### S0
`s0-stage`, `s0-insight-node`, `s0-outcome-node`, `s0-direction-node`, `gate-problem`

### S1
`s1-stage`, `s1-product-insight-node`, `s1-actors-node`, `s1-modules-node`, `s1-procedures-node`, `s1-boundary-node`, `gate-product`

### S2
`s2-stage`, `s2-domains-node`, `s2-components-node`, `s2-interactions-node`, `s2-data-domains-node`, `s2-constraints-node`, `gate-architecture`

### S3
`s3-stage`, `s3-slice-node`, `s3-contract-node`, `s3-data-model-node`, `s3-task-plan-node`, `gate-slice`

### S4
`s4-stage`, `s4-code-structure-node`, `s4-frontend-node`, `s4-backend-node`, `s4-validation-node`, `s4-integration-node`, `gate-code`

### S5
`s5-stage`, `s5-test-plan-node`, `s5-unit-test-node`, `s5-integration-test-node`, `s5-acceptance-node`, `s5-bug-node`, `gate-quality`

### S6
`s6-stage`, `s6-release-node`, `s6-deploy-checklist-node`, `s6-rollback-node`, `s6-docs-node`, `s6-handoff-node`, `gate-release`

## التكيف حسب حجم المشروع

### مشروع صغير (مثل: عيادة حجوزات)
- شريحة واحدة في S3
- ملف واحد في S4
- ~22 اختبار في S5

### مشروع كبير (مثل: نظام مستشفى)
- عدة شرائح في S3 (مثلاً 4 شرائح)
- كل شريحة لها S4 + S5 مستقل
- ~85 اختبار في S5
- Integration tests بين الشرائح
