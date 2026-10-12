# القوائم List

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. إنشاء قوائم والوصول إلى عناصرها بالفهرسة الموجبة والسالبة.
2. تعديل العناصر وإضافة عناصر جديدة وحذفها.
3. استخدام التقطيع (Slicing) لاقتطاع أجزاء من القائمة.
4. استخدام دوال القوائم: `append()`, `insert()`, `remove()`, `pop()`, `sort()`, `count()`, `len()`.
5. بناء قوائم باستخدام استيعاب القوائم (List Comprehensions).

📖 يقابل هذا الفصل: **الفصل 11 «القوائم: الخادم إلى نوع List»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- المتغيرات تخزن قيمة واحدة: `grade = 85`.
- الحلقات `for` تمر على تسلسل: `for g in grades:`.
- الشروط `if` تتخذ قرارات بناءً على القيم.
- العمليات الحسابية `+`, `*` تعمل مع النصوص والأرقام.
- دوال مثل `len()` و `round()` و `sum()` جاهزة للاستخدام.

## إحماء 🔥

توقّع المخرجات على ورقة أولًا، ثم شغّل الكود وقارن.

### إحماء 1

```python
grades = [85, 92, 78, 95, 60]
print(grades[0])
print(grades[-1])
```

<details>
<summary>الحل</summary>

```text
85
60
```

الفهرس `0` يجلب أول عنصر، والفهرس `-1` يجلب آخر عنصر من النهاية.
</details>

### إحماء 2

```python
grades = [85, 92, 78, 95, 60]
print(grades[1:4])
```

<details>
<summary>الحل</summary>

```text
[92, 78, 95]
```

التقطيع `[1:4]` يبدأ من الفهرس 1 ويتوقف قبل الفهرس 4، فيأخذ الفهارس 1 و 2 و 3.
</details>

### إحماء 3

```python
grades = [85, 92, 78]
grades.append(90)
print(grades)
print(len(grades))
```

<details>
<summary>الحل</summary>

```text
[85, 92, 78, 90]
4
```

الدالة `append()` تضيف عنصرًا جديدًا إلى نهاية القائمة. الدالة `len()` تُرجع عدد العناصر.
</details>

### إحماء 4

```python
grades = [85, 92, 78]
for g in grades:
    if g >= 80:
        print(g, "- Good")
```

<details>
<summary>الحل</summary>

```text
85 - Good
92 - Good
```

الحلقة تمر على كل عنصر، والشرط يطبع فقط الدرجات التي هي 80 أو أكثر.
</details>

---

## التمارين

### تمرين 1 ⭐ — إنشاء قائمة درجات

أنشئ قائمة باسم `grades` تحتوي على خمس درجات: 85، 92، 78، 95، 60. ثم اطبعها واطبع عدد عناصرها.

المخرجات المتوقعة:

```text
[85, 92, 78, 95, 60]
5
```

💡 تلميح 1: القوائم تُكتب بأقواس مربعة `[]` مفصولة بفواصل.

💡 تلميح 2: استخدم `len()` لعدد العناصر.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 60]
print(grades)
print(len(grades))
```

لماذا يعمل؟ الأقواس المربعة `[]` تُنشئ قائمة جديدة. الدالة `len()` تُرجع عدد العناصر في أي تسلسل.
</details>

---

### تمرين 2 ⭐ — الوصول بالعنصر

لديك قائمة درجات. اطبع أول درجة وآخر درجة وثالث درجة.

```python
grades = [85, 92, 78, 95, 60]
```

المخرجات المتوقعة:

```text
85
60
78
```

💡 تلميح 1: أول عنصر فهرسه `0` وآخر عنصر فهرسه `-1`.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 60]
print(grades[0])   # First grade
print(grades[-1])  # Last grade
print(grades[2])   # Third grade
```
</details>

---

### تمرين 3 ⭐⭐ — تعديل درجة

لديك قائمة درجات واكتشفت أن الدرجة الثالثة سُجّلت خطأً. غيّر `78` إلى `88` ثم اطبع القائمة.

```python
grades = [85, 92, 78, 95, 60]
```

المخرجات المتوقعة:

```text
[85, 92, 88, 95, 60]
```

💡 تلميح 1: الدرجات قابلة للتعديل (mutable).

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 60]
grades[2] = 88
print(grades)
```

لماذا يعمل؟ القوائم قابلة للتعديل (mutable)، فيمكن تغيير أي عنصر باستخدام فهرسه. هذا مختلف عن الصفوف (tuples) التي سنتعلمها لاحقًا.
</details>

---

### تمرين 4 ⭐⭐ — إضافة وحذف درجات

لديك قائمة درجات طالب. أضف درجة جديدة `73` إلى النهاية، ثم احذف أول درجة باستخدام `del`. اطبع القائمة بعد كل خطوة.

```python
grades = [85, 92, 78, 95, 60]
```

المخرجات المتوقعة:

```text
[85, 92, 78, 95, 60, 73]
[92, 78, 95, 60, 73]
```

💡 تلميح 1: `append()` تضيف إلى النهاية.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 60]

# Add new grade
grades.append(73)
print(grades)

# Remove first grade
del grades[0]
print(grades)
```
</details>

---

### تمرين 5 ⭐⭐⭐ — حساب المتوسط بحلقة

لديك قائمة درجات. استخدم حلقة `for` لحساب المجموع، ثم احسب المتوسط واطبعه مقرّبًا لمنزلة واحدة.

```python
grades = [85, 92, 78, 95, 60]
```

المخرجات المتوقعة:

```text
Total: 410
Average: 82.0
```

💡 تلميح 1: أنشئ متغير `total = 0` ثم أضف كل درجة بـ `+=`.

💡 تلميح 2: المتوسط = المجموع ÷ عدد العناصر.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 60]
total = 0

for g in grades:
    total += g

average = round(total / len(grades), 1)
print("Total:", total)
print("Average:", average)
```

لماذا يعمل؟ نمر على كل درجة ونضيفها إلى `total`. بعد الحلقة، نقسم على عدد العناصر. هذا هو الجزء الحسابي الأساسي من **دفتر الدرجات** 📚.
</details>

---

### تمرين 6 ⭐⭐⭐ — أعلى وأدنى درجة

اعثر على أعلى درجة وأدنى درجة في القائمة باستخدام حلقة (بدون `max()` أو `min()`). اطبعهما مع اسم المادة.

```python
subjects = ["Math", "Science", "Arabic", "English", "History"]
grades = [85, 92, 78, 95, 60]
```

المخرجات المتوقعة:

```text
Highest: English (95)
Lowest: History (60)
```

💡 تلميح 1: افترض أول عنصر هو الأعلى والأدنى، ثم حدّث أثناء المرور.

💡 تلميح 2: استخدم `range(len(grades))` للمرور بالفهارس.

<details>
<summary>الحل المفصّل</summary>

```python
subjects = ["Math", "Science", "Arabic", "English", "History"]
grades = [85, 92, 78, 95, 60]

highest_idx = 0
lowest_idx = 0

for i in range(len(grades)):
    if grades[i] > grades[highest_idx]:
        highest_idx = i
    if grades[i] < grades[lowest_idx]:
        lowest_idx = i

print("Highest:", subjects[highest_idx], "(" + str(grades[highest_idx]) + ")")
print("Lowest:", subjects[lowest_idx], "(" + str(grades[lowest_idx]) + ")")
```

لماذا يعمل؟ نبدأ بافتراض أن العنصر الأول هو الأعلى والأدنى. ثم نمر على كل عنصر: إذا كان أكبر من الأعلى الحالي، نحدّث الفهرس. بنهاية الحلقة نكون قد وجدنا القيمتين.
</details>

---

### تمرين 7 ⭐⭐⭐ — عدّ الناجحين والراسبين

من قائمة الدرجات التالية، احسب كم درجة ناجحة (>= 60) وكم درجة راسبة (< 60).

```python
grades = [85, 42, 78, 55, 91, 38, 60, 72]
```

المخرجات المتوقعة:

```text
Passing: 5
Failing: 3
```

💡 تلميح 1: أنشئ عدادين: `pass_count = 0` و `fail_count = 0`.

💡 تلميح 2: استخدم `if/else` داخل الحلقة.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 42, 78, 55, 91, 38, 60, 72]
pass_count = 0
fail_count = 0

for g in grades:
    if g >= 60:
        pass_count += 1
    else:
        fail_count += 1

print("Passing:", pass_count)
print("Failing:", fail_count)
```
</details>

---

### تمرين 8 ⭐⭐⭐⭐ — ترتيب الدرجات

استخدم الدالة `sort()` لترتيب قائمة الدرجات تصاعديًا، ثم اطبعها. بعد ذلك، اعكس الترتيب باستخدام `reverse()` واطبعها مرة أخرى.

```python
grades = [85, 92, 78, 95, 60]
```

المخرجات المتوقعة:

```text
Ascending: [60, 78, 85, 92, 95]
Descending: [95, 92, 85, 78, 60]
```

💡 تلميح 1: `sort()` ترتّب القائمة نفسها (لا تُرجع قائمة جديدة).

💡 تلميح 2: `reverse()` تعكس ترتيب العناصر.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 60]

grades.sort()
print("Ascending:", grades)

grades.reverse()
print("Descending:", grades)
```

لماذا يعمل؟ `sort()` تعدّل القائمة الأصلية مباشرة وتعيد ترتيبها من الأصغر إلى الأكبر. ثم `reverse()` تقلب الترتيب. لاحظ أن هاتين الدالتين لا تُرجعان قائمة جديدة بل تعدّلان القائمة نفسها.
</details>

---

### تمرين 9 ⭐⭐⭐⭐ — استيعاب القوائم (تصفية الدرجات)

استخدم استيعاب القوائم (List Comprehension) لإنشاء قائمة جديدة تحتوي فقط على الدرجات الناجحة (>= 60) من القائمة الأصلية.

```python
grades = [85, 42, 78, 55, 91, 38, 60, 72]
```

المخرجات المتوقعة:

```text
Passing grades: [85, 78, 91, 60, 72]
```

💡 تلميح 1: الصيغة: `[x for x in list if condition]`.

💡 تلميح 2: الشرط هنا هو `g >= 60`.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 42, 78, 55, 91, 38, 60, 72]
passing = [g for g in grades if g >= 60]
print("Passing grades:", passing)
```

لماذا يعمل؟ استيعاب القوائم يمر على كل عنصر `g` في `grades`، ويضيفه إلى القائمة الجديدة فقط إذا تحقق الشرط `g >= 60`. هذا يختصر حلقة `for` مع `if` في سطر واحد.
</details>

---

### تمرين 10 ⭐⭐⭐⭐ — قوائم متداخلة: درجات عدة طلاب

لديك قائمة متداخلة تحتوي على درجات ثلاثة طلاب. مرّ على كل طالب واطبع اسمه ومعدله.

```python
students = [
    ["Ahmad", 85, 92, 78],
    ["Salma", 90, 88, 95],
    ["Omar", 70, 65, 80]
]
```

المخرجات المتوقعة:

```text
Ahmad: Average = 85.0
Salma: Average = 91.0
Omar: Average = 71.7
```

💡 تلميح 1: `students[0]` يعطي قائمة الطالب الأول، و `students[0][0]` يعطي اسمه.

💡 تلميح 2: الدرجات تبدأ من الفهرس 1: `student[1:]`.

<details>
<summary>الحل المفصّل</summary>

```python
students = [
    ["Ahmad", 85, 92, 78],
    ["Salma", 90, 88, 95],
    ["Omar", 70, 65, 80]
]

for student in students:
    name = student[0]
    grades = student[1:]
    total = 0
    for g in grades:
        total += g
    average = round(total / len(grades), 1)
    print(name + ": Average =", average)
```

لماذا يعمل؟ كل عنصر في `students` هو قائمة. العنصر الأول فيها هو الاسم، والباقي درجات. نستخدم التقطيع `[1:]` للحصول على الدرجات فقط. هذا هو **دفتر الدرجات** 📚 بأبسط صوره.
</details>

---

### تمرين 11 ⭐⭐⭐⭐⭐ — مشروع مصغّر: دفتر الدرجات التفاعلي

لنبني النسخة الثانية من **دفتر الدرجات** 📚. اكتب برنامجًا:

1. يعرف قائمتين: `names` و `grades` لخمسة طلاب.
2. يمر على كل طالب ويطبع: الاسم، الدرجة، الحالة (Pass/Fail).
3. يحسب المعدل العام للصف.
4. يجد أعلى درجة واسم صاحبها.
5. يطبع ملخصًا نهائيًا.

```python
names = ["Ahmad", "Salma", "Omar", "Noor", "Layla"]
grades = [85, 92, 55, 78, 60]
```

المخرجات المتوقعة:

```text
--- Grade Book ---
Ahmad: 85 - Pass
Salma: 92 - Pass
Omar: 55 - Fail
Noor: 78 - Pass
Layla: 60 - Pass
-------------------
Class Average: 74.0
Top Student: Salma (92)
Pass Rate: 80.0%
```

💡 تلميح 1: استخدم `range(len(names))` للمرور بالفهارس.

💡 تلميح 2: تتبّع `highest` و `top_name` أثناء المرور.

💡 تلميح 3: نسبة النجاح = (عدد الناجحين ÷ العدد الكلي) × 100.

<details>
<summary>الحل المفصّل</summary>

```python
names = ["Ahmad", "Salma", "Omar", "Noor", "Layla"]
grades = [85, 92, 55, 78, 60]

print("--- Grade Book ---")

total = 0
pass_count = 0
highest = grades[0]
top_name = names[0]

for i in range(len(names)):
    name = names[i]
    grade = grades[i]
    total += grade

    if grade >= 60:
        status = "Pass"
        pass_count += 1
    else:
        status = "Fail"

    if grade > highest:
        highest = grade
        top_name = name

    print(name + ":", grade, "-", status)

average = round(total / len(names), 1)
pass_rate = round((pass_count / len(names)) * 100, 1)

print("-------------------")
print("Class Average:", average)
print("Top Student:", top_name, "(" + str(highest) + ")")
print("Pass Rate:", str(pass_rate) + "%")
```

لماذا يعمل؟ نمر على كل طالب مرة واحدة، وفي كل مرور نجمع الدرجة ونعدّ الناجحين ونتتبع الأعلى. بعد الحلقة نحسب المتوسط والنسبة. هذا هو جوهر دفتر الدرجات، وفي الفصول القادمة سنضيف القواميس والدوال لجعله أقوى.
</details>

---

## مختبر الأخطاء 🧪

في كل خطأ مما يلي: **توقّع نوع الخطأ ورسالته قبل قراءة الحل**، ثم قارن.

### 🧪 خطأ 1 — فهرس خارج النطاق

```python
grades = [85, 92, 78]
print(grades[5])
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "grades.py", line 2, in <module>
    print(grades[5])
IndexError: list index out of range
```

السبب: القائمة فيها 3 عناصر فقط (فهارس 0، 1، 2). طلب الفهرس 5 يتجاوز طولها.

الإصلاح: تأكد أن الفهرس أصغر من `len(grades)`، أو استخدم الفهرسة السالبة `-1` للوصول من النهاية.
</details>

---

### 🧪 خطأ 2 — حذف عنصر غير موجود

```python
grades = [85, 92, 78]
grades.remove(100)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "grades.py", line 2, in <module>
    grades.remove(100)
ValueError: list.remove(x): x not in list
```

السبب: الدالة `remove()` تبحث عن القيمة `100` في القائمة ولا تجدها.

الإصلاح: تأكد أن القيمة موجودة قبل حذفها، أو استخدم `if`:

```python
if 100 in grades:
    grades.remove(100)
```
</details>

---

### 🧪 خطأ 3 — تمرير عدد إلى range() كنص

```python
for i in range("5"):
    print(i)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "loop.py", line 1, in <module>
    for i in range("5"):
TypeError: 'str' object cannot be interpreted as an integer
```

السبب: الدالة `range()` تتوقع عددًا صحيحًا، لكنك مرّرت نصًا `"5"`.

الإصلاح: مرّر عددًا صحيحًا بدون اقتباس:

```python
for i in range(5):
    print(i)
```

هذا خطأ شائع عند قراءة مدخلات من المستخدم، حيث تأتي دائمًا كنص وتحتاج تحويلًا بـ `int()`.
</details>

---

### 🧪 خطأ 4 — تعديل عنصر خارج الحلقة أثناء المرور

```python
grades = [85, 92, 78, 95, 60]
for g in grades:
    if g < 60:
        grades.remove(g)
print(grades)
```

<details>
<summary>التحليل والإصلاح</summary>

هذا الكود لا يُطلق خطأ، لكنه يعطي **نتيجة خاطئة**! القائمة الناتجة قد لا تكون كما تتوقع لأن تعديل القائمة أثناء المرور عليها يغيّر الفهارس.

الإصلاح: استخدم استيعاب القوائم لإنشاء قائمة جديدة:

```python
grades = [85, 92, 78, 95, 60]
passing = [g for g in grades if g >= 60]
print(passing)
```

قاعدة ذهبية: لا تعدّل قائمة أثناء المرور عليها بحلقة `for`. أنشئ قائمة جديدة بدلًا من ذلك.
</details>

---

## تحدي المتعة 🎮 — لعبة البحث عن الكنز

لديك خريطة مخفية (قائمة). اكتب برنامجًا يطلب من "اللاعب" (متغيرات فقط، بدون `input`) تخمين مواقع الكنوز. اطبع ما وجده.

```python
map_row = ["empty", "empty", "treasure", "empty", "trap", "empty"]
positions_to_check = [0, 2, 4]
```

<details>
<summary>الحل</summary>

```python
map_row = ["empty", "empty", "treasure", "empty", "trap", "empty"]
positions_to_check = [0, 2, 4]

for pos in positions_to_check:
    if map_row[pos] == "treasure":
        print("Found treasure at position", pos, "!")
    elif map_row[pos] == "trap":
        print("Watch out! Trap at position", pos, "!")
    else:
        print("Position", pos, "is empty.")
```

المخرجات:
```text
Position 0 is empty.
Found treasure at position 2 !
Watch out! Trap at position 4 !
```
</details>

---

## أخطاء شائعة عند المبتدئين

1. **نسيان أن الفهرسة تبدأ من 0**: أول عنصر فهرسه `0` وليس `1`.
2. **الخلط بين `append()` و `insert()`**: الأولى تضيف للنهاية، الثانية تضيف في موقع محدد.
3. **تعديل القائمة أثناء المرور عليها**: لا تحذف أو تضف عناصر داخل حلقة `for` على نفس القائمة.
4. **الاعتقاد أن `sort()` تُرجع قائمة جديدة**: هي تعدّل القائمة الأصلية وتُرجع `None`.
5. **استخدام `=` بدل `==` في الشروط داخل الحلقة**.
6. **نسيان الأقواس المربعة**: `grades = 85, 92, 78` تُنشئ صفًا (tuple) وليس قائمة.

## قائمة تحقق ✅

قبل الانتقال إلى الفصل التالي، تأكد أنك تستطيع:

- [ ] إنشاء قائمة والوصول لعناصرها بالفهرسة الموجبة والسالبة.
- [ ] تعديل عناصر وإضافة وحذف.
- [ ] استخدام التقطيع `[start:end]`.
- [ ] استخدام `append()`, `insert()`, `remove()`, `pop()`, `sort()`, `count()`.
- [ ] المرور على قائمة بحلقة `for` مع شروط.
- [ ] استخدام استيعاب القوائم لتصفية البيانات.
- [ ] قراءة أخطاء `IndexError` و `ValueError` وإصلاحها.

**ماذا سيعتمد عليه الفصل القادم؟** فصل «الصفوف (Tuples)»: سنتعلم بنية بيانات مشابهة للقوائم لكنها **غير قابلة للتعديل**. ستفهم متى تستخدم قائمة ومتى تستخدم صفًا، وكيف تحول بينهما.