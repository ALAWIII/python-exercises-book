# المهام التكرارية: الحلقات

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. استخدام حلقة `while` لتكرار كود طالما شرط معين صحيح.
2. استخدام حلقة `for` للمرور على تسلسل (قائمة، نطاق، نص).
3. استخدام `range()` لتوليد نطاقات أرقام.
4. التحكم في الحلقات بـ `break` و `continue` و `pass`.
5. بناء حلقات متداخلة لمعالجة بيانات مركبة.

📖 يقابل هذا الفصل: **الفصل 15 «المهام التكرارية: الحلقات»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- الشروط `if/elif/else` تتخذ قرارات (الفصل السابق).
- القوائم تُكتب بأقواس مربعة: `[85, 90, 78]`.
- `len()` تُرجع عدد عناصر القائمة.
- `+=` تجمع وتُسند في خطوة واحدة.
- `range(start, stop, step)` تولد أرقامًا (توقف قبل `stop`).

## إحماء 🔥

توقّع المخرجات على ورقة أولًا، ثم شغّل الكود وقارن.

### إحماء 1

```python
for i in range(3):
    print(i)
```

<details>
<summary>الحل</summary>

```text
0
1
2
```

`range(3)` يولّد الأرقام 0 و 1 و 2 (يتوقف قبل 3). الحلقة تكرر `print` ثلاث مرات.
</details>

### إحماء 2

```python
count = 0
while count < 3:
    print("Count:", count)
    count += 1
```

<details>
<summary>الحل</summary>

```text
Count: 0
Count: 1
Count: 2
```

الحلقة تستمر طالما `count < 3`. في كل تكرار تُطبع القيمة ثم تُزاد بواحد. عند `count = 3` يصبح الشرط خاطئًا وتتوقف الحلقة.
</details>

### إحماء 3

```python
grades = [85, 90, 78]
for g in grades:
    print(g)
```

<details>
<summary>الحل</summary>

```text
85
90
78
```

الحلقة تمر على كل عنصر في القائمة. في كل تكرار، يأخذ `g` قيمة العنصر الحالي.
</details>

### إحماء 4

```python
for i in range(1, 10, 3):
    print(i)
```

<details>
<summary>الحل</summary>

```text
1
4
7
```

`range(1, 10, 3)` يبدأ من 1، يقفز بخطوة 3، ويتوقف قبل 10. إذن: 1، 4، 7.
</details>

---

## التمارين

### تمرين 1 ⭐ — طباعة أرقام

استخدم حلقة `for` مع `range()` لطباعة الأرقام من 1 إلى 5.

المخرجات المتوقعة:

```text
1
2
3
4
5
```

💡 تلميح 1: `range()` يبدأ من 0 افتراضيًا ويتوقف قبل الرقم المعطى.

💡 تلميح 2: للحصول على 1 إلى 5، استخدم `range(1, 6)`.

<details>
<summary>الحل المفصّل</summary>

```python
for i in range(1, 6):
    print(i)
```

لماذا يعمل؟ `range(1, 6)` يولّد: 1, 2, 3, 4, 5. الرقم 6 غير مشمول (التوقف قبل `stop`). هذا سلوك ثابت في بايثون.
</details>

---

### تمرين 2 ⭐ — أكمل الفراغ

أكمل الكود ليعدّ من 0 إلى 4 باستخدام `while`:

```python
count = 0
while count < ____:
    print(count)
    count += ____
```

💡 تلميح 1: نريد التوقف قبل الوصول إلى 5.

💡 تلميح 2: نزيد العداد بواحد في كل تكرار.

<details>
<summary>الحل المفصّل</summary>

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

بدون `count += 1` ستبقى الحلقة إلى الأبد (حلقة لا نهائية) لأن الشرط لن يصبح خاطئًا أبدًا.
</details>

---

### تمرين 3 ⭐⭐ — المرور على قائمة درجات

لديك قائمة درجات. اطبع كل درجة مع كلمة `"Grade:"` قبلها.

```python
grades = [85, 92, 78, 95, 88]
```

المخرجات المتوقعة:

```text
Grade: 85
Grade: 92
Grade: 78
Grade: 95
Grade: 88
```

💡 تلميح 1: استخدم `for g in grades:`.

💡 تلميح 2: اطبع `"Grade:"` متبوعة بالمتغير `g`.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 88]

for g in grades:
    print("Grade:", g)
```

لماذا يعمل؟ الحلقة `for` تمر على كل عنصر في القائمة بالترتيب. في التكرار الأول `g = 85`، في الثاني `g = 92`، وهكذا حتى نهاية القائمة.
</details>

---

### تمرين 4 ⭐⭐⭐ — مجموع الدرجات بحلقة

احسب مجموع الدرجات في القائمة باستخدام حلقة `for` (بدون `sum()`).

```python
grades = [85, 92, 78, 95, 88]
```

المخرجات المتوقعة:

```text
Total: 438
```

💡 تلميح 1: أنشئ متغير `total = 0` قبل الحلقة.

💡 تلميح 2: في كل تكرار، أضف الدرجة الحالية إلى `total`.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 88]
total = 0

for g in grades:
    total += g

print("Total:", total)
```

لماذا يعمل؟ نبدأ بـ `total = 0`، ثم في كل تكرار نضيف عنصرًا: 0+85=85، ثم 85+92=177، ثم 177+78=255، ثم 255+95=350، ثم 350+88=438. هذا النمط (المُجمِّع) أساسي في البرمجة.
</details>

---

### تمرين 5 ⭐⭐⭐ — عدّ الناجحين

من قائمة الدرجات التالية، احسب كم طالبًا نجح (الدرجة >= 60):

```python
grades = [85, 42, 78, 55, 91, 60, 38]
```

المخرجات المتوقعة:

```text
Passing: 5
```

💡 تلميح 1: أنشئ عدادًا `count = 0`.

💡 تلميح 2: داخل الحلقة، استخدم `if` للتحقق من كل درجة.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 42, 78, 55, 91, 60, 38]
pass_count = 0

for g in grades:
    if g >= 60:
        pass_count += 1

print("Passing:", pass_count)
```

لماذا يعمل؟ نمر على كل درجة، وإذا كانت 60 أو أكثر نزيد العداد. هذا يدمج الحلقة مع الشرط — نمط ستستخدمه باستمرار في دفتر الدرجات.
</details>

---

### تمرين 6 ⭐⭐⭐⭐ — حساب المعدل من قائمة

احسب معدل قائمة درجات باستخدام حلقة (المجموع ÷ عدد المواد)، وقرّب النتيجة لمنزلة واحدة.

```python
grades = [85, 92, 78, 95, 88]
```

المخرجات المتوقعة:

```text
Average: 87.6
```

💡 تلميح 1: استخدم `len(grades)` لمعرفة عدد العناصر.

💡 تلميح 2: اجمع في حلقة، ثم اقسم خارج الحلقة.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 88]
total = 0

for g in grades:
    total += g

average = round(total / len(grades), 1)
print("Average:", average)
```

لماذا يعمل؟ نجمع كل الدرجات (438)، ثم نقسم على عددها (5)، فنحصل على 87.6. لاحظ أن القسمة تتم خارج الحلقة بعد اكتمال الجمع.
</details>

---

### تمرين 7 ⭐⭐⭐⭐ — أعلى درجة وأدناها

اعثر على أعلى درجة وأدنى درجة في القائمة باستخدام حلقة (بدون `max()` أو `min()`).

```python
grades = [85, 92, 78, 95, 88]
```

المخرجات المتوقعة:

```text
Highest: 95
Lowest: 78
```

💡 تلميح 1: ابدأ بافتراض أن أول عنصر هو الأعلى والأدنى.

💡 تلميح 2: في كل تكرار، قارن وحدّث إذا وجدت أعلى أو أدنى.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 78, 95, 88]

highest = grades[0]
lowest = grades[0]

for g in grades:
    if g > highest:
        highest = g
    if g < lowest:
        lowest = g

print("Highest:", highest)
print("Lowest:", lowest)
```

لماذا يعمل؟ نفترض أولًا أن العنصر الأول هو الأعلى والأدنى. ثم نمر على كل عنصر: إذا كان أكبر من `highest` نحدّثه، وإذا كان أصغر من `lowest` نحدّثه. بنهاية الحلقة نكون قد وجدنا القيمتين.
</details>

---

### تمرين 8 ⭐⭐⭐⭐ — حلقة مع شرط: تصنيف الدرجات

مرّ على قائمة درجات واطبع لكل درجة تصنيفها:
- >= 90: `"Excellent"`
- >= 75: `"Good"`
- >= 60: `"Pass"`
- < 60: `"Fail"`

```python
grades = [92, 78, 55, 85, 60]
```

💡 تلميح 1: ادمج `for` مع `if/elif/else` داخل الحلقة.

💡 تلميح 2: اطبع الدرجة والتصنيف معًا في كل تكرار.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [92, 78, 55, 85, 60]

for g in grades:
    if g >= 90:
        label = "Excellent"
    elif g >= 75:
        label = "Good"
    elif g >= 60:
        label = "Pass"
    else:
        label = "Fail"
    print(g, "-", label)
```

المخرجات:
```text
92 - Excellent
78 - Good
55 - Fail
85 - Good
60 - Pass
```

هذا يدمج كل ما تعلمناه: حلقة + شرط + متغيرات. وهو بالضبط ما يفعله دفتر الدرجات.
</details>

---

### تمرين 9 ⭐⭐⭐⭐ — التحكم بالحلقة: break

ابحث عن أول درجة أقل من 60 في القائمة وأوقف البحث فور إيجادها:

```python
grades = [85, 92, 55, 78, 42]
```

المخرجات المتوقعة:

```text
First failing grade: 55
```

💡 تلميح 1: استخدم `if` داخل الحلقة للتحقق.

💡 تلميح 2: استخدم `break` للخروج من الحلقة فورًا.

<details>
<summary>الحل المفصّل</summary>

```python
grades = [85, 92, 55, 78, 42]

for g in grades:
    if g < 60:
        print("First failing grade:", g)
        break
```

لماذا يعمل؟ نمر على الدرجات: 85 ليست أقل من 60، 92 ليست، 55 أقل من 60! نطبعها ونستخدم `break` للخروج فورًا. لا نفحص 78 أو 42. هذا يوفر وقتًا في القوائم الطويلة.
</details>

---

### تمرين 10 ⭐⭐⭐⭐⭐ — مشروع مصغّر: دفتر درجات الصف

لنبني النسخة الأولى من **دفتر الدرجات** 📚. اكتب برنامجًا:

1. يعرف قائمة بأسماء الطلاب وقائمة بدرجاتهم:
```python
names = ["Ahmad", "Salma", "Omar", "Noor", "Layla"]
grades = [85, 92, 55, 78, 60]
```
2. يمر على كل طالب ويطبع اسمه ودرجته وحالته (Pass/Fail).
3. يحسب المعدل العام.
4. يجد أعلى درجة واسم صاحبها.

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
```

💡 تلميح 1: استخدم `range(len(names))` للمرور بالفهارس.

💡 تلميح 2: تتبّع أعلى درجة واسمها أثناء المرور.

<details>
<summary>الحل المفصّل</summary>

```python
names = ["Ahmad", "Salma", "Omar", "Noor", "Layla"]
grades = [85, 92, 55, 78, 60]

print("--- Grade Book ---")

total = 0
highest = grades[0]
top_student = names[0]

for i in range(len(names)):
    name = names[i]
    grade = grades[i]
    total += grade

    if grade >= 60:
        status = "Pass"
    else:
        status = "Fail"

    if grade > highest:
        highest = grade
        top_student = name

    print(name + ":", grade, "-", status)

average = round(total / len(names), 1)

print("-------------------")
print("Class Average:", average)
print("Top Student:", top_student, "(" + str(highest) + ")")
```

لماذا يعمل؟ نستخدم `range(len(names))` للحصول على الفهارس 0, 1, 2, 3, 4. في كل تكرار نستخدم الفهرس `i` للوصول إلى الاسم والدرجة معًا. نتتبع المجموع وأعلى درجة أثناء المرور، ثم نحسب المعدل بعد الحلقة. هذا هو دفتر الدرجات الأولي — في الفصول القادمة سنضيف القواميس والدوال لجعله أقوى.
</details>

---

## مختبر الأخطاء 🧪

في كل خطأ مما يلي: **توقّع نوع الخطأ ورسالته قبل قراءة الحل**، ثم قارن.

### 🧪 خطأ 1 — النقطتان المفقودتان في الحلقة

```python
for i in range(5)
    print(i)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
  File "loops.py", line 1
    for i in range(5)
                     ^
SyntaxError: expected ':'
```

السبب: نفس قاعدة الشروط — كل `for` أو `while` يجب أن تنتهي بنقطتين.

الإصلاح:

```python
for i in range(5):
    print(i)
```
</details>

---

### 🧪 خطأ 2 — المسافة البادئة في الحلقة

```python
for i in range(3):
print(i)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
  File "loops.py", line 2
    print(i)
    ^
IndentationError: expected an indented block after 'for' statement on line 1
```

السبب: جسم الحلقة يجب أن يكون مُزاحًا. بدون مسافة بادئة، لا تعرف بايثون ما الكود الذي يجب تكراره.

الإصلاح:

```python
for i in range(3):
    print(i)
```
</details>

---

### 🧪 خطأ 3 — حلقة لا نهائية

```python
count = 0
while count < 5:
    print(count)
```

<details>
<summary>التحليل والإصلاح</summary>

هذا لا يُنتج خطأ، بل **حلقة لا نهائية**! البرنامج سيطبع 0 إلى الأبد لأن `count` لا تتغير أبدًا.

لإيقافه: اضغط `Ctrl+C` في الطرفية.

السبب: نسينا زيادة العداد. الشرط `count < 5` يبقى صحيحًا دائمًا.

الإصلاح:

```python
count = 0
while count < 5:
    print(count)
    count += 1  # Don't forget this!
```

قاعدة ذهبية: في كل حلقة `while`، تأكد أن شيئًا ما يتغير ليجعل الشرط خاطئًا في النهاية.
</details>

---

### 🧪 خطأ 4 — المرور على غير قابل للتكرار

```python
number = 5
for i in number:
    print(i)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "loops.py", line 2, in <module>
    for i in number:
TypeError: 'int' object is not iterable
```

السبب: حلقة `for` تحتاج شيئًا قابلًا للتكرار (قائمة، نص، نطاق). العدد `5` ليس كذلك.

الإصلاح: استخدم `range()` لتحويل العدد إلى نطاق:

```python
number = 5
for i in range(number):
    print(i)
```
</details>

---

### 🧪 خطأ 5 — فهرس خارج النطاق في حلقة

```python
grades = [85, 92, 78]
for i in range(4):
    print(grades[i])
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
85
92
78
Traceback (most recent call last):
  File "loops.py", line 3, in <module>
    print(grades[i])
IndexError: list index out of range
```

السبب: القائمة فيها 3 عناصر (فهارس 0, 1, 2)، لكن `range(4)` يحاول الوصول إلى الفهرس 3.

الإصلاح: استخدم `len()` لضمان التوافق:

```python
grades = [85, 92, 78]
for i in range(len(grades)):
    print(grades[i])
```

أو الأفضل — مرّ مباشرة على العناصر:

```python
for g in grades:
    print(g)
```
</details>

---

## تحدي المتعة 🎮 — لعبة تخمين الرقم

محاكاة للعبة من الكتاب: خزّن رقمًا سريًا و"خمّن" عدة مرات باستخدام حلقة `while` وعداد محاولات.

```python
secret = 7
guess = 0
attempts = 0
guesses = [3, 5, 7]  # Simulated guesses
```

مرّ على التخمينات وأوقف الحلقة عند الإصابة.

<details>
<summary>الحل</summary>

```python
secret = 7
guesses = [3, 5, 7]
attempts = 0
found = False

for guess in guesses:
    attempts += 1
    if guess == secret:
        found = True
        print("Correct! Guessed in", attempts, "attempts.")
        break
    elif guess < secret:
        print("Too low:", guess)
    else:
        print("Too high:", guess)

if not found:
    print("Out of guesses. The number was", secret)
```

المخرجات:
```text
Too low: 3
Too low: 5
Correct! Guessed in 3 attempts.
```
</details>

---

## أخطاء شائعة عند المبتدئين

1. **حلقة لا نهائية في `while`**: نسيان تحديث العداد أو الشرط. تأكد دائمًا أن شيئًا يتغير.
2. **الخلط بين `range(5)` و `range(1, 5)`**: الأولى تعطي 0-4، الثانية تعطي 1-4.
3. **نسيان أن `range` لا يشمل الرقم الأخير**: `range(1, 5)` يعطي 1, 2, 3, 4 وليس 5.
4. **تعديل القائمة أثناء المرور عليها**: لا تحذف أو تضف عناصر لقائمة تمر عليها.
5. **استخدام `break` خارج حلقة**: `break` تعمل فقط داخل `for` أو `while`.
6. **الخلط بين `for` و `while`**: استخدم `for` عندما تعرف عدد التكرارات أو تمر على تسلسل، و `while` عندما تعتمد على شرط.

## قائمة تحقق ✅

قبل الانتقال إلى الوحدة التالية، تأكد أنك تستطيع:

- [ ] كتابة حلقة `for` مع `range()` والمرور على قوائم.
- [ ] كتابة حلقة `while` مع شرط توقف صحيح.
- [ ] استخدام `break` و `continue` للتحكم في الحلقة.
- [ ] دمج الحلقات مع الشروط (`if` داخل `for`).
- [ ] حساب مجموع ومتوسط وأعلى/أدنى قيمة بحلقة.
- [ ] قراءة أخطاء `IndentationError` و `TypeError` و `IndexError`.

**ماذا سيعتمد عليه الفصل القادم؟** وحدة «هياكل البيانات»: سنتعلم القوائم بالتفصيل (إضافة، حذف، تعديل، استيعاب)، ثم الصفوف والقواميس. كل ما تعلمناه في الحلقات سيُستخدم لتمرير ومعالجة هذه الهياكل.