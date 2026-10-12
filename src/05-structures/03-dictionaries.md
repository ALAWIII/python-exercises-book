# القواميس Dictionary

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. إنشاء قواميس بأزواج مفتاح-قيمة والوصول إلى القيم بالمفاتيح.
2. إضافة وتعديل وحذف عناصر في القاموس.
3. استخدام دوال القواميس: `keys()`, `values()`, `items()`, `get()`, `update()`.
4. المرور على القواميس بحلقات `for`.
5. بناء قواميس باستخدام استيعاب القواميس (Dict Comprehensions).

📖 يقابل هذا الفصل: **الفصل 13 «القواميس: فهم نوع Dictionary»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- القوائم تُفهرس بالأرقام: `grades[0]`.
- الصفوف غير قابلة للتعديل وتُكتب بأقواس `()`.
- الحلقات `for` تمر على تسلسلات.
- الشروط `if` تتحقق من القيم.
- `in` تتحقق من وجود عنصر: `if x in list:`.

## إحماء 🔥

توقّع المخرجات على ورقة أولًا، ثم شغّل الكود وقارن.

### إحماء 1

```python
student = {"name": "Ahmad", "grade": 85, "passed": True}
print(student["name"])
print(student["grade"])
```

<details>
<summary>الحل</summary>

```text
Ahmad
85
```

القاموس يخزن أزواج مفتاح-قيمة. نصل إلى القيمة بوضع المفتاح بين أقواس مربعة.
</details>

### إحماء 2

```python
student = {"name": "Ahmad", "grade": 85}
student["grade"] = 90
student["age"] = 14
print(student)
```

<details>
<summary>الحل</summary>

```text
{'name': 'Ahmad', 'grade': 90, 'age': 14}
```

القواميس قابلة للتعديل. يمكن تغيير قيمة موجودة أو إضافة زوج جديد بنفس الصيغة.
</details>

### إحماء 3

```python
student = {"name": "Ahmad", "grade": 85, "passed": True}
for key in student:
    print(key, ":", student[key])
```

<details>
<summary>الحل</summary>

```text
name : Ahmad
grade : 85
passed : True
```

المرور على قاموس بحلقة `for` يُرجع المفاتيح. نستخدم المفتاح للوصول إلى القيمة.
</details>

---

## التمارين

### تمرين 1 ⭐ — إنشاء قاموس طالب

أنشئ قاموسًا باسم `student` يحتوي على: الاسم `"Salma"`، العمر `14`، الصف `"8-A"`، المعدل `92.5`. اطبعه.

المخرجات المتوقعة:

```text
{'name': 'Salma', 'age': 14, 'class': '8-A', 'average': 92.5}
```

💡 تلميح 1: القواميس تُكتب بأقواس معقوفة `{}` مع نقطتين بين المفتاح والقيمة.

💡 تلميح 2: المفاتيح نصوص، والقيم يمكن أن تكون أي نوع.

<details>
<summary>الحل المفصّل</summary>

```python
student = {
    "name": "Salma",
    "age": 14,
    "class": "8-A",
    "average": 92.5
}
print(student)
```

لماذا يعمل؟ الأقواس المعقوفة `{}` تُنشئ قاموسًا. كل زوج `مفتاح: قيمة` مفصول بفاصلة. المفاتيح هنا نصوص، لكن القيم متنوعة (نص، عدد صحيح، عدد عشري).
</details>

---

### تمرين 2 ⭐ — الوصول بالقيم

لديك قاموس طالب. اطبع اسمه ومعدله.

```python
student = {"name": "Omar", "grade": 78, "passed": True}
```

المخرجات المتوقعة:

```text
Omar
78
```

💡 تلميح 1: استخدم `student["name"]`.

💡 تلميح 2: لا تستخدم فهرسًا رقميًا — القواميس تُفهرس بالمفاتيح.

<details>
<summary>الحل المفصّل</summary>

```python
student = {"name": "Omar", "grade": 78, "passed": True}
print(student["name"])
print(student["grade"])
```
</details>

---

### تمرين 3 ⭐⭐ — تعديل وإضافة

لديك قاموس طالب. غيّر درجته من `78` إلى `85`، وأضف مفتاحًا جديدًا `"attendance"` بقيمة `95`.

```python
student = {"name": "Omar", "grade": 78}
```

المخرجات المتوقعة:

```text
{'name': 'Omar', 'grade': 85, 'attendance': 95}
```

💡 تلميح 1: `student["grade"] = 85` يغيّر القيمة.

💡 تلميح 2: `student["attendance"] = 95` يضيف زوجًا جديدًا.

<details>
<summary>الحل المفصّل</summary>

```python
student = {"name": "Omar", "grade": 78}

# Modify existing value
student["grade"] = 85

# Add new key-value pair
student["attendance"] = 95

print(student)
```

القواميس مرنة جدًا — يمكن إضافة أزواج جديدة في أي وقت دون إعادة إنشاء القاموس.
</details>

---

### تمرين 4 ⭐⭐ — حذف مفتاح

لديك قاموس طالب يحتوي على مفتاح `"temp_note"` مؤقت. احذفه باستخدام `del` ثم اطبع القاموس.

```python
student = {"name": "Ahmad", "grade": 90, "temp_note": "Remove later"}
```

المخرجات المتوقعة:

```text
{'name': 'Ahmad', 'grade': 90}
```

💡 تلميح 1: `del student["temp_note"]` يحذف الزوج.

💡 تلميح 2: تأكد أن المفتاح موجود قبل الحذف.

<details>
<summary>الحل المفصّل</summary>

```python
student = {"name": "Ahmad", "grade": 90, "temp_note": "Remove later"}
del student["temp_note"]
print(student)
```
</details>

---

### تمرين 5 ⭐⭐⭐ — دفتر درجات كقاموس

أنشئ قاموسًا يربط أسماء الطلاب بدرجاتهم. ثم اطبع كل طالب ودرجته وحالته (Pass إذا >= 60).

```python
gradebook = {
    "Ahmad": 85,
    "Salma": 92,
    "Omar": 55,
    "Noor": 78,
    "Layla": 60
}
```

المخرجات المتوقعة:

```text
Ahmad: 85 - Pass
Salma: 92 - Pass
Omar: 55 - Fail
Noor: 78 - Pass
Layla: 60 - Pass
```

💡 تلميح 1: مرّ على القاموس بـ `for name in gradebook:`.

💡 تلميح 2: الدرجة هي `gradebook[name]`.

<details>
<summary>الحل المفصّل</summary>

```python
gradebook = {
    "Ahmad": 85,
    "Salma": 92,
    "Omar": 55,
    "Noor": 78,
    "Layla": 60
}

for name in gradebook:
    grade = gradebook[name]
    if grade >= 60:
        status = "Pass"
    else:
        status = "Fail"
    print(name + ":", grade, "-", status)
```

لماذا يعمل؟ هذا هو **دفتر الدرجات** 📚 بصيغته القاموسية. المفتاح هو اسم الطالب، والقيمة هي درجته. الوصول مباشر بالاسم دون الحاجة لفهرس رقمي.
</details>

---

### تمرين 6 ⭐⭐⭐ — حساب المعدل من قاموس

من قاموس الدرجات السابق، احسب المعدل العام وأعلى درجة واسم صاحبها.

```python
gradebook = {
    "Ahmad": 85,
    "Salma": 92,
    "Omar": 55,
    "Noor": 78,
    "Layla": 60
}
```

المخرجات المتوقعة:

```text
Class Average: 74.0
Top Student: Salma (92)
```

💡 تلميح 1: استخدم `gradebook.values()` للحصول على كل الدرجات.

💡 تلميح 2: أو مرّ بـ `for name, grade in gradebook.items():`.

<details>
<summary>الحل المفصّل</summary>

```python
gradebook = {
    "Ahmad": 85,
    "Salma": 92,
    "Omar": 55,
    "Noor": 78,
    "Layla": 60
}

total = 0
highest = 0
top_student = ""

for name, grade in gradebook.items():
    total += grade
    if grade > highest:
        highest = grade
        top_student = name

average = round(total / len(gradebook), 1)
print("Class Average:", average)
print("Top Student:", top_student, "(" + str(highest) + ")")
```

لماذا يعمل؟ الدالة `items()` تُرجع أزواج `(مفتاح، قيمة)` في كل تكرار. هذا يسمح لنا بالوصول إلى الاسم والدرجة معًا.
</details>

---

### تمرين 7 ⭐⭐⭐ — البحث عن طالب

اكتب برنامجًا يبحث عن طالب في قاموس الدرجات. إذا وُجد، اطبع درجته. إذا لم يوجد، اطبع رسالة.

```python
gradebook = {"Ahmad": 85, "Salma": 92, "Omar": 55}
search_name = "Layla"
```

المخرجات المتوقعة:

```text
Student 'Layla' not found.
```

💡 تلميح 1: استخدم `if search_name in gradebook:`.

💡 تلميح 2: أو استخدم الدالة `get()` التي تُرجع قيمة افتراضية.

<details>
<summary>الحل المفصّل</summary>

```python
gradebook = {"Ahmad": 85, "Salma": 92, "Omar": 55}
search_name = "Layla"

if search_name in gradebook:
    print(search_name, "scored", gradebook[search_name])
else:
    print("Student '" + search_name + "' not found.")
```

أو باستخدام `get()`:

```python
result = gradebook.get(search_name, None)
if result is not None:
    print(search_name, "scored", result)
else:
    print("Student '" + search_name + "' not found.")
```

الدالة `get()` أفضل من الوصول المباشر `[key]` لأنها لا تُطلق خطأ إذا لم يوجد المفتاح.
</details>

---

### تمرين 8 ⭐⭐⭐⭐ — قاموس متداخل: معلومات كاملة

أنشئ قاموسًا لكل طالب يحتوي على معلومات مفصلة (الدرجة، الحضور، الحالة). ثم اطبع تقريرًا لكل طالب.

```python
students = {
    "Ahmad": {"grade": 85, "attendance": 95, "passed": True},
    "Salma": {"grade": 92, "attendance": 100, "passed": True},
    "Omar": {"grade": 55, "attendance": 70, "passed": False}
}
```

المخرجات المتوقعة:

```text
--- Student Report ---
Ahmad: Grade=85, Attendance=95%, Status=Pass
Salma: Grade=92, Attendance=100%, Status=Pass
Omar: Grade=55, Attendance=70%, Status=Fail
```

💡 تلميح 1: `students["Ahmad"]["grade"]` تصل إلى درجة أحمد.

💡 تلميح 2: مرّ على القاموس الخارجي، ثم ادخل القاموس الداخلي.

<details>
<summary>الحل المفصّل</summary>

```python
students = {
    "Ahmad": {"grade": 85, "attendance": 95, "passed": True},
    "Salma": {"grade": 92, "attendance": 100, "passed": True},
    "Omar": {"grade": 55, "attendance": 70, "passed": False}
}

print("--- Student Report ---")

for name, info in students.items():
    grade = info["grade"]
    attendance = info["attendance"]
    status = "Pass" if info["passed"] else "Fail"
    print(name + ": Grade=" + str(grade) + ", Attendance=" + str(attendance) + "%, Status=" + status)
```

لماذا يعمل؟ القواميس المتداخلة تسمح بتخزين معلومات معقدة لكل طالب. هذا هو الشكل النهائي لدفتر الدرجات — كل طالب له قاموس خاص بمعلوماته.
</details>

---

### تمرين 9 ⭐⭐⭐⭐ — استيعاب القواميس

استخدم استيعاب القواميس (Dict Comprehension) لإنشاء قاموس جديد يحتوي فقط على الطلاب الناجحين من القاموس الأصلي.

```python
gradebook = {"Ahmad": 85, "Salma": 92, "Omar": 55, "Noor": 78, "Layla": 45}
```

المخرجات المتوقعة:

```text
Passing students: {'Ahmad': 85, 'Salma': 92, 'Noor': 78}
```

💡 تلميح 1: الصيغة: `{k: v for k, v in dict.items() if condition}`.

💡 تلميح 2: الشرط هو `v >= 60`.

<details>
<summary>الحل المفصّل</summary>

```python
gradebook = {"Ahmad": 85, "Salma": 92, "Omar": 55, "Noor": 78, "Layla": 45}
passing = {name: grade for name, grade in gradebook.items() if grade >= 60}
print("Passing students:", passing)
```

لماذا يعمل؟ استيعاب القواميس يمر على كل زوج `(name, grade)` ويضيفه إلى القاموس الجديد فقط إذا كانت الدرجة >= 60. هذا يختصر حلقة مع شرط في سطر واحد.
</details>

---

### تمرين 10 ⭐⭐⭐⭐⭐ — مشروع مصغّر: دفتر الدرجات الكامل

لنبني النسخة النهائية من **دفتر الدرجات** 📚 باستخدام القواميس. اكتب برنامجًا:

1. يعرف قاموسًا متداخلًا لخمسة طلاب (الدرجة، الحضور).
2. يطبع تقريرًا لكل طالب: الاسم، الدرجة، الحالة.
3. يحسب المعدل العام ونسبة النجاح.
4. يجد أعلى وأدنى درجة.
5. يسمح "بتصحيح" درجة طالب (تغيير قيمة في القاموس).

```python
gradebook = {
    "Ahmad": {"grade": 85, "attendance": 95},
    "Salma": {"grade": 92, "attendance": 100},
    "Omar": {"grade": 55, "attendance": 70},
    "Noor": {"grade": 78, "attendance": 88},
    "Layla": {"grade": 60, "attendance": 92}
}
```

المخرجات المتوقعة:

```text
=== Grade Book System ===
Ahmad: 85 (Attendance: 95%) - Pass
Salma: 92 (Attendance: 100%) - Pass
Omar: 55 (Attendance: 70%) - Fail
Noor: 78 (Attendance: 88%) - Pass
Layla: 60 (Attendance: 92%) - Pass
---------------------------
Class Average: 74.0
Pass Rate: 80.0%
Highest: Salma (92)
Lowest: Omar (55)
---------------------------
Updating Omar's grade to 62...
Omar: 62 (Attendance: 70%) - Pass
New Class Average: 75.4
```

💡 تلميح 1: مرّ بـ `for name, info in gradebook.items():`.

💡 تلميح 2: لتصحيح درجة: `gradebook["Omar"]["grade"] = 62`.

💡 تلميح 3: أعد حساب المتوسط بعد التصحيح.

<details>
<summary>الحل المفصّل</summary>

```python
gradebook = {
    "Ahmad": {"grade": 85, "attendance": 95},
    "Salma": {"grade": 92, "attendance": 100},
    "Omar": {"grade": 55, "attendance": 70},
    "Noor": {"grade": 78, "attendance": 88},
    "Layla": {"grade": 60, "attendance": 92}
}

def print_report():
    total = 0
    pass_count = 0
    highest_grade = 0
    lowest_grade = 100
    highest_name = ""
    lowest_name = ""

    for name, info in gradebook.items():
        grade = info["grade"]
        attendance = info["attendance"]
        total += grade

        if grade >= 60:
            status = "Pass"
            pass_count += 1
        else:
            status = "Fail"

        if grade > highest_grade:
            highest_grade = grade
            highest_name = name
        if grade < lowest_grade:
            lowest_grade = grade
            lowest_name = name

        print(name + ":", grade, "(Attendance: " + str(attendance) + "%) -", status)

    average = round(total / len(gradebook), 1)
    pass_rate = round((pass_count / len(gradebook)) * 100, 1)

    print("---------------------------")
    print("Class Average:", average)
    print("Pass Rate:", str(pass_rate) + "%")
    print("Highest:", highest_name, "(" + str(highest_grade) + ")")
    print("Lowest:", lowest_name, "(" + str(lowest_grade) + ")")

print("=== Grade Book System ===")
print_report()

# Correct Omar's grade
print("---------------------------")
print("Updating Omar's grade to 62...")
gradebook["Omar"]["grade"] = 62
print_report()
```

لماذا يعمل؟ القاموس المتداخل يسمح لنا بتخزين معلومات معقدة لكل طالب. تعديل درجة طالب بسيط: نصل إلى المفتاح ونغيّر القيمة. الدالة `print_report()` تُعيد استخدام الكود. في الوحدة القادمة سنتعلم الدوال والوحدات لجعل هذا أكثر احترافية.
</details>

---

## مختبر الأخطاء 🧪

في كل خطأ مما يلي: **توقّع نوع الخطأ ورسالته قبل قراءة الحل**، ثم قارن.

### 🧪 خطأ 1 — مفتاح غير موجود

```python
student = {"name": "Ahmad", "grade": 85}
print(student["age"])
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "student.py", line 2, in <module>
    print(student["age"])
KeyError: 'age'
```

السبب: المفتاح `"age"` غير موجود في القاموس. الوصول المباشر `[key]` يُطلق `KeyError` إذا لم يوجد المفتاح.

الإصلاح: استخدم `get()` أو تحقق أولًا:

```python
# Option 1: get() with default
age = student.get("age", "Unknown")
print(age)

# Option 2: Check first
if "age" in student:
    print(student["age"])
else:
    print("Age not recorded")
```
</details>

---

### 🧪 خطأ 2 — استخدام فهرس رقمي مع قاموس

```python
student = {"name": "Ahmad", "grade": 85}
print(student[0])
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "student.py", line 2, in <module>
    print(student[0])
KeyError: 0
```

السبب: القواميس لا تُفهرس بالأرقام. المفتاح `0` غير موجود في القاموس.

الإصلاح: استخدم المفتاح الصحيح:

```python
print(student["name"])  # Ahmad
```

القواميس تُفهرس بالمفاتيح (نصوص عادةً)، وليس بالفهارس الرقمية. هذا هو الفرق الجوهري بينها وبين القوائم.
</details>

---

### 🧪 خطأ 3 — مفتاح غير صالح (قائمة كمفتاح)

```python
data = {["Ahmad", "Math"]: 85}
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "data.py", line 1, in <module>
    data = {["Ahmad", "Math"]: 85}
TypeError: cannot use 'list' as a dict key (unhashable type: 'list')
```

السبب: مفاتيح القواميس يجب أن تكون **غير قابلة للتعديل** (immutable). القوائم قابلة للتعديل، فلا تصلح كمفاتيح.

الإصلاح: استخدم صفًا (tuple) بدلًا من قائمة:

```python
data = {("Ahmad", "Math"): 85}
print(data[("Ahmad", "Math")])  # 85
```

الصفوف غير قابلة للتعديل، فتصلح كمفاتيح. هذا مفيد عندما تريد مفتاحًا مركبًا (اسم + مادة).
</details>

---

### 🧪 خطأ 4 — المرور على القاموس وتعديله

```python
grades = {"Ahmad": 85, "Salma": 92, "Omar": 55}
for name in grades:
    if grades[name] < 60:
        del grades[name]
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
RuntimeError: dictionary changed size during iteration
```

السبب: لا يمكنك تعديل حجم القاموس (إضافة أو حذف مفاتيح) أثناء المرور عليه.

الإصلاح: أنشئ قائمة بالمفاتيح المطلوب حذفها أولًا، ثم احذفها بعد الحلقة:

```python
grades = {"Ahmad": 85, "Salma": 92, "Omar": 55}
to_remove = []

for name in grades:
    if grades[name] < 60:
        to_remove.append(name)

for name in to_remove:
    del grades[name]

print(grades)  # {'Ahmad': 85, 'Salma': 92}
```

أو استخدم استيعاب القواميس:

```python
grades = {"Ahmad": 85, "Salma": 92, "Omar": 55}
passing = {name: grade for name, grade in grades.items() if grade >= 60}
```
</details>

---

## تحدي المتعة 🎮 — نظام النقاط المدرسي

أنشئ قاموسًا لنظام نقاط: كل نشاط له نقاط. اكتب برنامجًا يحسب مجموع نقاط طالب ويحدد مستواه.

```python
activities = {
    "homework": 30,
    "quiz": 20,
    "project": 25,
    "participation": 15,
    "final_exam": 10
}

student_scores = {
    "homework": 28,
    "quiz": 18,
    "project": 22,
    "participation": 14,
    "final_exam": 9
}
```

المستويات: >= 90 "Gold", >= 75 "Silver", >= 60 "Bronze", أقل "Needs Improvement".

<details>
<summary>الحل</summary>

```python
activities = {
    "homework": 30,
    "quiz": 20,
    "project": 25,
    "participation": 15,
    "final_exam": 10
}

student_scores = {
    "homework": 28,
    "quiz": 18,
    "project": 22,
    "participation": 14,
    "final_exam": 9
}

total_earned = 0
total_possible = 0

for activity in activities:
    total_earned += student_scores[activity]
    total_possible += activities[activity]

percentage = round((total_earned / total_possible) * 100, 1)

if percentage >= 90:
    level = "Gold"
elif percentage >= 75:
    level = "Silver"
elif percentage >= 60:
    level = "Bronze"
else:
    level = "Needs Improvement"

print("Total:", total_earned, "/", total_possible)
print("Percentage:", str(percentage) + "%")
print("Level:", level)
```

المخرجات:
```text
Total: 91 / 100
Percentage: 91.0%
Level: Gold
```
</details>

---

## أخطاء شائعة عند المبتدئين

1. **استخدام فهرس رقمي مع قاموس**: القواميس تُفهرس بالمفاتيح، ليس بالأرقام.
2. **الوصول لمفتاح غير موجود بدون تحقق**: استخدم `get()` أو `if key in dict:`.
3. **استخدام قائمة كمفتاح**: المفاتيح يجب أن تكون غير قابلة للتعديل (نص، عدد، صف).
4. **تعديل القاموس أثناء المرور عليه**: لا تحذف أو تضف مفاتيح داخل حلقة `for` على نفس القاموس.
5. **نسيان النقطتين بين المفتاح والقيمة**: `{"name", "Ahmad"}` خطأ، الصحيح `{"name": "Ahmad"}`.
6. **الخلط بين الأقواس**: `{}` للقواميس، `[]` للقوائم، `()` للصفوف.

## قائمة تحقق ✅

قبل الانتقال إلى الوحدة التالية، تأكد أنك تستطيع:

- [ ] إنشاء قاموس بأزواج مفتاح-قيمة.
- [ ] الوصول للقيم بالمفاتيح وتعديلها وإضافة وحذف.
- [ ] استخدام `keys()`, `values()`, `items()`, `get()`.
- [ ] المرور على قاموس بحلقة `for`.
- [ ] استخدام استيعاب القواميس.
- [ ] بناء قواميس متداخلة لبيانات معقدة.
- [ ] قراءة أخطاء `KeyError` و `TypeError` و `RuntimeError`.

**ماذا سيعتمد عليه الفصل القادم؟** وحدة «الدوال والوحدات»: سنتعلم كيف نغلّف كل هذا المنطق في دوال قابلة لإعادة الاستخدام، ثم نقسم البرنامج إلى وحدات (ملفات) منفصلة. دفتر الدرجات سيصبح برنامجًا حقيقيًا متعدد الملفات.