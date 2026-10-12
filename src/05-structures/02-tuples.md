# الصفوف Tuple

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. إنشاء صفوف (Tuples) والوصول إلى عناصرها بالفهرسة.
2. فهم الفرق الجوهري بين الصفوف والقوائم (الثبات مقابل القابلية للتعديل).
3. استخدام التقطيع مع الصفوف.
4. دمج الصفوف وضربها باستخدام `+` و `*`.
5. استخدام دوال الصفوف: `len()`, `max()`, `min()`, `count()`, `index()`.
6. التحويل بين الصفوف والقوائم.

📖 يقابل هذا الفصل: **الفصل 12 «الصفوف: فهم نوع Tuple»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- القوائم تُكتب بأقواس مربعة `[]` وقابلة للتعديل.
- الوصول بالعنصر: `grades[0]`, `grades[-1]`.
- التقطيع: `grades[1:3]`.
- الدالة `len()` تُرجع عدد العناصر.
- القوائم قابلة للتعديل: `grades[0] = 90` يعمل.

## إحماء 🔥

توقّع المخرجات على ورقة أولًا، ثم شغّل الكود وقارن.

### إحماء 1

```python
subjects = ("Math", "Science", "Arabic")
print(subjects[0])
print(subjects[-1])
print(len(subjects))
```

<details>
<summary>الحل</summary>

```text
Math
Arabic
3
```

الصفوف تعمل مثل القوائم في الفهرسة والطول، لكنها تُكتب بأقواس عادية `()`.
</details>

### إحماء 2

```python
subjects = ("Math", "Science", "Arabic")
subjects[0] = "English"
```

<details>
<summary>الحل</summary>

```text
TypeError: 'tuple' object does not support item assignment
```

الصفوف **غير قابلة للتعديل** (immutable). لا يمكنك تغيير عنصر بعد إنشاء الصف.
</details>

### إحماء 3

```python
grades = (85, 92, 78, 95, 60)
print(grades[1:4])
print(max(grades))
print(min(grades))
```

<details>
<summary>الحل</summary>

```text
(92, 78, 95)
95
60
```

التقطيع مع الصفوف يُرجع صفًا جديدًا (بأقواس عادية). الدالتان `max()` و `min()` تعملان مع الصفوف.
</details>

---

## التمارين

### تمرين 1 ⭐ — إنشاء صف

أنشئ صفًا باسم `semester_info` يحتوي على: اسم الفصل `"First Semester"`، السنة `2024`، عدد الأسابيع `16`. اطبعه واطبع طوله.

المخرجات المتوقعة:

```text
('First Semester', 2024, 16)
3
```

💡 تلميح 1: الصفوف تُكتب بأقواس عادية `()`.

💡 تلميح 2: يمكن أن يحتوي الصف على أنواع مختلفة من البيانات.

<details>
<summary>الحل المفصّل</summary>

```python
semester_info = ("First Semester", 2024, 16)
print(semester_info)
print(len(semester_info))
```

لماذا يعمل؟ الصفوف يمكن أن تحتوي على نصوص وأعداد ومنطقية معًا. هي مثالية للبيانات الثابتة التي لا تتغير.
</details>

---

### تمرين 2 ⭐ — الوصول بالعناصر

لديك صف يحتوي على أيام الأسبوع الدراسية. اطبع اليوم الأول والأخير والثالث.

```python
school_days = ("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday")
```

المخرجات المتوقعة:

```text
Sunday
Thursday
Tuesday
```

💡 تلميح 1: الفهرسة تعمل تمامًا كما في القوائم.

💡 تلميح 2: `[-1]` للآخر، `[2]` للثالث.

<details>
<summary>الحل المفصّل</summary>

```python
school_days = ("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday")
print(school_days[0])
print(school_days[-1])
print(school_days[2])
```
</details>

---

### تمرين 3 ⭐⭐ — لماذا صف وليس قائمة؟

لديك بيانات ثابتة عن مدرسة. اشرح في تعليق لماذا استخدمنا صفًا وليس قائمة، ثم حاول تغيير العنصر الأول ولاحظ الخطأ.

```python
school_info = ("Al-Noor School", "Established 2010", "Riyadh")
```

💡 تلميح 1: البيانات الثابتة التي لا يجب أن تتغير تناسب الصفوف.

💡 تلميح 2: جرّب `school_info[0] = "Changed"` وشاهد الخطأ.

<details>
<summary>الحل المفصّل</summary>

```python
# School info is fixed data that should never change.
# A tuple guarantees no one can accidentally modify it.
school_info = ("Al-Noor School", "Established 2010", "Riyadh")

# This would cause an error:
# school_info[0] = "Changed"  # TypeError!
```

الصفوف تحمي البيانات الثابتة من التعديل العرضي. لو كانت قائمة، قد يغيّر أحدهم اسم المدرسة بالخطأ في حلقة أو دالة.
</details>

---

### تمرين 4 ⭐⭐ — التقطيع مع الصفوف

لديك صف درجات. اقتطع الدرجات من الفهرس 1 إلى 3، ثم اقتطع آخر عنصرين.

```python
grades = (85, 92, 78, 95, 60)
```

المخرجات المتوقعة:

```text
(92, 78)
(95, 60)
```

💡 تلميح 1: `[1:3]` يبدأ من 1 ويتوقف قبل 3.

💡 تلميح 2: `[-2:]` يأخذ آخر عنصرين.

<details>
<summary>الحل المفصّل</summary>

```python
grades = (85, 92, 78, 95, 60)
middle = grades[1:3]
last_two = grades[-2:]
print(middle)
print(last_two)
```

لاحظ أن النتيجة صف جديد (بأقواس عادية)، وليس قائمة. التقطيع لا يعدّل الصف الأصلي.
</details>

---

### تمرين 5 ⭐⭐⭐ — دمج الصفوف

لديك صفان: درجات الفصل الأول ودرجات الفصل الثاني. ادمجهما في صف واحد واطبعه.

```python
first_semester = (85, 92, 78)
second_semester = (90, 88, 95)
```

المخرجات المتوقعة:

```text
(85, 92, 78, 90, 88, 95)
```

💡 تلميح 1: استخدم العامل `+` لدمج صفين.

💡 تلميح 2: النتيجة صف جديد، والصفان الأصليان لا يتغيران.

<details>
<summary>الحل المفصّل</summary>

```python
first_semester = (85, 92, 78)
second_semester = (90, 88, 95)
full_year = first_semester + second_semester
print(full_year)
```

لماذا يعمل؟ العامل `+` بين صفين يُنشئ صفًا جديدًا يجمعهما. الصفوف غير قابلة للتعديل، لكن يمكن إنشاء صف جديد من صفين موجودين.
</details>

---

### تمرين 6 ⭐⭐⭐ — تكرار صف

اضرب الصف في 3 لإنشاء نسخة مكررة، ثم استخدم `count()` لعدّ كم مرة ظهرت الدرجة `85`.

```python
sample = (85, 92)
```

المخرجات المتوقعة:

```text
(85, 92, 85, 92, 85, 92)
3
```

💡 تلميح 1: العامل `*` يكرر الصف.

💡 تلميح 2: `count(x)` تُرجع عدد مرات ظهور `x`.

<details>
<summary>الحل المفصّل</summary>

```python
sample = (85, 92)
repeated = sample * 3
print(repeated)
print(repeated.count(85))
```
</details>

---

### تمرين 7 ⭐⭐⭐ — التحويل بين صف وقائمة

لديك صف درجات وتريد تعديله (إضافة درجة جديدة). حوّله إلى قائمة، أضف `73`، ثم أعد تحويله إلى صف.

```python
grades = (85, 92, 78)
```

المخرجات المتوقعة:

```text
(85, 92, 78, 73)
```

💡 تلميح 1: `list(tuple)` تحول صفًا إلى قائمة.

💡 تلميح 2: `tuple(list)` تحول قائمة إلى صف.

<details>
<summary>الحل المفصّل</summary>

```python
grades = (85, 92, 78)

# Convert to list, modify, convert back
grades_list = list(grades)
grades_list.append(73)
grades = tuple(grades_list)

print(grades)
```

لماذا يعمل؟ الصفوف لا تُعدّل، لكننا نستطيع تحويلها إلى قائمة مؤقتة، تعديل القائمة، ثم إعادة التحويل إلى صف. هذا النمط شائع عندما تحتاج "تعديل" صف.
</details>

---

### تمرين 8 ⭐⭐⭐⭐ — صف في دفتر الدرجات

استخدم صفًا لتخزين معلومات ثابتة عن مادة دراسية (الاسم، الدرجة القصوى، وزن المادة)، ثم استخدم هذه المعلومات في حساب درجة طالب مرجّحة.

```python
math_info = ("Math", 100, 0.3)
science_info = ("Science", 100, 0.2)
arabic_info = ("Arabic", 100, 0.5)

student_grades = {"Math": 85, "Science": 90, "Arabic": 78}
```

المخرجات المتوقعة:

```text
Weighted Grade: 82.5
```

💡 تلميح 1: `math_info[2]` يعطي الوزن.

💡 تلميح 2: الدرجة المرجّحة = (الدرجة ÷ الدرجة القصوى) × الوزن × 100.

<details>
<summary>الحل المفصّل</summary>

```python
math_info = ("Math", 100, 0.3)
science_info = ("Science", 100, 0.2)
arabic_info = ("Arabic", 100, 0.5)

subjects = [math_info, science_info, arabic_info]
student_grades = {"Math": 85, "Science": 90, "Arabic": 78}

weighted_total = 0
for subject in subjects:
    name = subject[0]
    max_grade = subject[1]
    weight = subject[2]
    student_grade = student_grades[name]
    weighted_total += (student_grade / max_grade) * weight * 100

print("Weighted Grade:", round(weighted_total, 1))
```

لماذا يعمل؟ الصفوف مثالية لتخزين البيانات الثابتة عن كل مادة (الاسم لا يتغير، الدرجة القصوى لا تتغير، الوزن لا يتغير). نمر على كل صف ونستخرج المعلومات بالفهرسة.
</details>

---

### تمرين 9 ⭐⭐⭐⭐⭐ — مشروع مصغّر: جدول الحصص الأسبوعي

لنبني جزءًا من **دفتر الدرجات** 📚. أنشئ جدول حصص أسبوعي باستخدام صفوف متداخلة. كل صف يمثل يومًا دراسيًا ويحتوي على 4 حصص. اطبع الجدول بشكل منسق.

```python
schedule = (
    ("Sunday", "Math", "Science", "Arabic", "English"),
    ("Monday", "Arabic", "Math", "History", "Science"),
    ("Tuesday", "English", "Science", "Math", "Arabic"),
    ("Wednesday", "Science", "Arabic", "English", "Math"),
    ("Thursday", "Math", "English", "Science", "History")
)
```

المخرجات المتوقعة:

```text
--- Weekly Schedule ---
Sunday:    Math | Science | Arabic | English
Monday:    Arabic | Math | History | Science
Tuesday:   English | Science | Math | Arabic
Wednesday: Science | Arabic | English | Math
Thursday:  Math | English | Science | History
```

💡 تلميح 1: كل عنصر في `schedule` هو صف: الأول هو اليوم، والباقي حصص.

💡 تلميح 2: استخدم `day[0]` لليوم و `day[1:]` للحصص.

💡 تلميح 3: استخدم `" | ".join()` لدمج الحصص.

<details>
<summary>الحل المفصّل</summary>

```python
schedule = (
    ("Sunday", "Math", "Science", "Arabic", "English"),
    ("Monday", "Arabic", "Math", "History", "Science"),
    ("Tuesday", "English", "Science", "Math", "Arabic"),
    ("Wednesday", "Science", "Arabic", "English", "Math"),
    ("Thursday", "Math", "English", "Science", "History")
)

print("--- Weekly Schedule ---")

for day in schedule:
    day_name = day[0]
    periods = day[1:]
    line = " | ".join(periods)
    print(day_name + ":", line)
```

لماذا يعمل؟ الصفوف المتداخلة مثالية لجدول الحصص لأن البيانات ثابتة لا تتغير. لا أحد يجب أن يعدّل الجدول أثناء تشغيل البرنامج. `" | ".join()` تدمج عناصر القائمة في نص واحد مفصول بـ ` | `.
</details>

---

## مختبر الأخطاء 🧪

في كل خطأ مما يلي: **توقّع نوع الخطأ ورسالته قبل قراءة الحل**، ثم قارن.

### 🧪 خطأ 1 — تعديل صف

```python
subjects = ("Math", "Science", "Arabic")
subjects[1] = "English"
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "subjects.py", line 2, in <module>
    subjects[1] = "English"
TypeError: 'tuple' object does not support item assignment
```

السبب: الصفوف غير قابلة للتعديل (immutable). هذه ميزة وليست عيبًا — تحمي البيانات الثابتة.

الإصلاح: إذا كنت تحتاج التعديل، استخدم قائمة. أو حوّل الصف إلى قائمة، عدّل، ثم أعد التحويل:

```python
subjects = ("Math", "Science", "Arabic")
subjects_list = list(subjects)
subjects_list[1] = "English"
subjects = tuple(subjects_list)
```
</details>

---

### 🧪 خطأ 2 — إضافة عنصر إلى صف

```python
grades = (85, 92, 78)
grades.append(90)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "grades.py", line 2, in <module>
    grades.append(90)
AttributeError: 'tuple' object has no attribute 'append'
```

السبب: الدالة `append()` خاصة بالقوائم فقط. الصفوف ليس لديها هذه الدالة لأنها غير قابلة للتعديل.

الإصلاح: استخدم الدمج لإنشاء صف جديد:

```python
grades = (85, 92, 78)
grades = grades + (90,)
print(grades)  # (85, 92, 78, 90)
```

لاحظ الفاصلة بعد `90` — بدونها `(90)` هو مجرد عدد بين أقواس، وليس صفًا.
</details>

---

### 🧪 خطأ 3 — صف بعنصر واحد بدون فاصلة

```python
single = (85)
print(type(single))
print(len(single))
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
<class 'int'>
```

ثم خطأ عند `len()`:

```text
TypeError: object of type 'int' has no len()
```

السبب: `(85)` بدون فاصلة ليس صفًا، بل هو مجرد عدد بين أقواس. بايثون تتجاهل الأقواس.

الإصلاح: أضف فاصلة بعد العنصر:

```python
single = (85,)
print(type(single))  # <class 'tuple'>
print(len(single))   # 1
```

الفاصلة هي ما يجعل بايثون تفهم أن هذا صف وليس مجرد تعبير بين أقواس.
</details>

---

## تحدي المتعة 🎮 — إحداثيات الخريطة

استخدم صفوفًا لتمثيل إحداثيات مواقع على خريطة مدرسية. كل موقع هو صف `(name, x, y)`. احسب المسافة بين موقعين.

```python
library = ("Library", 2, 5)
cafeteria = ("Cafeteria", 8, 1)
```

<details>
<summary>الحل</summary>

```python
library = ("Library", 2, 5)
cafeteria = ("Cafeteria", 8, 1)

dx = cafeteria[1] - library[1]
dy = cafeteria[2] - library[2]
distance = (dx ** 2 + dy ** 2) ** 0.5

print("Distance from", library[0], "to", cafeteria[0], "is", round(distance, 2))
```

المخرجات: `Distance from Library to Cafeteria is 7.21`
</details>

---

## أخطاء شائعة عند المبتدئين

1. **محاولة تعديل صف**: الصفوف غير قابلة للتعديل. استخدم قائمة إذا كنت تحتاج التعديل.
2. **نسيان الفاصلة في صف بعنصر واحد**: `(85)` ليس صفًا، `(85,)` هو صف.
3. **استخدام `append()` على صف**: هذه الدالة للقوائم فقط. استخدم الدمج `+` بدلًا منها.
4. **الخلط بين الأقواس**: `[]` للقوائم، `()` للصفوف.
5. **استخدام صف عندما تحتاج التعديل**: اختر البنية المناسبة. بيانات ثابتة → صف، بيانات متغيرة → قائمة.

## قائمة تحقق ✅

قبل الانتقال إلى الفصل التالي، تأكد أنك تستطيع:

- [ ] إنشاء صف والوصول لعناصره.
- [ ] شرح الفرق بين الصف والقائمة.
- [ ] استخدام التقطيع مع الصفوف.
- [ ] دمج الصفوف بـ `+` وتكرارها بـ `*`.
- [ ] استخدام `len()`, `max()`, `min()`, `count()`.
- [ ] التحويل بين صف وقائمة بـ `tuple()` و `list()`.
- [ ] قراءة أخطاء `TypeError` و `AttributeError` المتعلقة بالصفوف.

**ماذا سيعتمد عليه الفصل القادم؟** فصل «القواميس (Dictionaries)»: سنتعلم بنية بيانات مختلفة تمامًا — بدلًا من الفهرسة بالأرقام، سنستخدم **مفاتيح** (مثل أسماء الطلاب) للوصول إلى القيم (مثل درجاتهم). هذا سيغيّر طريقة بناء دفتر الدرجات كليًا.