# التعليمات الشرطية

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. كتابة جملة `if` لتنفيذ كود فقط عند تحقق شرط معين.
2. استخدام `else` لتنفيذ كود بديل عند عدم تحقق الشرط.
3. استخدام `elif` للتحقق من عدة شروط متتالية.
4. بناء شروط متداخلة (Nested) لقرارات مركبة.
5. ربط الشروط بالعوامل المنطقية `and` و `or` و `not`.

📖 يقابل هذا الفصل: **الفصل 14 «التعليمات الشرطية»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- المقارنات تُرجع `True` أو `False`: `grade >= 65`
- العوامل المنطقية: `and` يتطلب صحّتين، `or` يكتفي بواحدة، `not` يقلب.
- المسافة البادئة (4 مسافات) تحدد الكود التابع للشرط.
- النقطتان `:` في نهاية سطر الشرط إلزاميتان.
- القيم المنطقية تُكتب `True` و `False` بحرف أول كبير.

## إحماء 🔥

توقّع المخرجات على ورقة أولًا، ثم شغّل الكود وقارن.

### إحماء 1

```python
grade = 80
if grade >= 65:
    print("Passing")
```

<details>
<summary>الحل</summary>

```text
Passing
```

الشرط `80 >= 65` صحيح (`True`)، فيُنفَّذ الكود داخل كتلة `if` وتُطبع "Passing".
</details>

### إحماء 2

```python
grade = 50
if grade >= 65:
    print("Passing")
else:
    print("Failing")
```

<details>
<summary>الحل</summary>

```text
Failing
```

الشرط `50 >= 65` خاطئ (`False`)، فيُتخطَّى كود `if` ويُنفَّذ كود `else`.
</details>

### إحماء 3

```python
score = 92
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
else:
    print("F")
```

<details>
<summary>الحل</summary>

```text
A
```

يُفحص الشرط الأول `92 >= 90` فيكون صحيحًا، فتُطبع "A" ويتوقف الفحص. لا تُفحص بقية الشروط.
</details>

### إحماء 4

```python
balance = 0
if balance < 0:
    print("Negative")
elif balance == 0:
    print("Zero")
else:
    print("Positive")
```

<details>
<summary>الحل</summary>

```text
Zero
```

الشرط الأول `0 < 0` خاطئ. الشرط الثاني `0 == 0` صحيح، فتُطبع "Zero".
</details>

---

## التمارين

### تمرين 1 ⭐ — هل نجح الطالب؟

اكتب برنامجًا يتحقق من درجة طالب. إذا كانت الدرجة 60 أو أكثر، اطبع `"Pass"`. استخدم المتغير `grade = 75`.

المخرجات المتوقعة:

```text
Pass
```

💡 تلميح 1: ابدأ بـ `if` ثم الشرط ثم النقطتين.

💡 تلميح 2: لا تنسَ المسافة البادئة (4 مسافات) قبل `print`.

<details>
<summary>الحل المفصّل</summary>

```python
grade = 75

if grade >= 60:
    print("Pass")
```

لماذا يعمل؟ التعبير `75 >= 60` يُقيَّم إلى `True`، فتُنفَّذ الكتلة التابعة لـ `if`. لو كانت الدرجة أقل من 60، لما طُبع شيء (لا يوجد `else` هنا).
</details>

---

### تمرين 2 ⭐ — أكمل الفراغ

أكمل الكود بحيث يطبع `"Failing"` عندما لا يتحقق شرط النجاح:

```python
grade = 45

if grade >= 60:
    print("Pass")
____:
    print("Failing")
```

💡 تلميح 1: نحتاج كلمة تعني "وإلا".

<details>
<summary>الحل المفصّل</summary>

```python
grade = 45

if grade >= 60:
    print("Pass")
else:
    print("Failing")
```

الكلمة `else` تعني "في جميع الحالات الأخرى". لا تحتاج `else` إلى شرط لأنها تغطي كل ما لم يتحقق في `if`.
</details>

---

### تمرين 3 ⭐⭐ — أصلح الكود

الكود التالي يحتوي على خطأين. أصلحهما:

```python
grade = 85
if grade >= 60
print("Pass")
```

💡 تلميح 1: ما الذي ينقص نهاية سطر `if`؟

💡 تلميح 2: هل `print` داخل كتلة `if` أم خارجها؟

<details>
<summary>الحل المفصّل</summary>

```python
grade = 85
if grade >= 60:
    print("Pass")
```

الخطآن:
1. النقطتان `:` مفقودتان بعد الشرط.
2. `print` ليست مُزاحة (لا توجد مسافة بادئة)، فيظن بايثون أنها خارج كتلة `if`.
</details>

---

### تمرين 4 ⭐⭐⭐ — تقييم النجاح والرسوب

اكتب برنامجًا كاملًا:
- يخزن درجة طالب في `grade`.
- إذا كانت 60 أو أكثر: يطبع `"Result: Pass"`.
- وإلا: يطبع `"Result: Fail"`.
- في الحالتين، اطبع الدرجة نفسها: `"Grade: X"`.

المخرجات المتوقعة (عندما تكون الدرجة 72):

```text
Result: Pass
Grade: 72
```

💡 تلميح 1: طباعة الدرجة مشتركة بين الحالتين، فأين تضعها؟

💡 تلميح 2: السطر المشترك يُكتب خارج كتلة `if/else` (بدون مسافة بادئة إضافية).

<details>
<summary>الحل المفصّل</summary>

```python
grade = 72

if grade >= 60:
    print("Result: Pass")
else:
    print("Result: Fail")

print("Grade:", grade)
```

لماذا يعمل؟ السطر الأخير خارج كتلة الشرط (لا مسافة بادئة إضافية)، فيُنفَّذ دائمًا بغض النظر عن النتيجة. هذا نمط شائع: قرار ثم معلومة مشتركة.
</details>

---

### تمرين 5 ⭐⭐⭐ — التقدير الحرفي المبسط

اكتب برنامجًا يحوّل الدرجة العددية إلى تقدير حرفي:
- 90 فأكثر: `"A"`
- 75 إلى 89: `"B"`
- 60 إلى 74: `"C"`
- أقل من 60: `"F"`

استخدم `grade = 82`.

المخرجات المتوقعة:

```text
B
```

💡 تلميح 1: ابدأ بالشرط الأعلى (90) ثم انزل تدريجيًا.

<details>
<summary>الحل المفصّل</summary>

```python
grade = 82

if grade >= 90:
    print("A")
elif grade >= 75:
    print("B")
elif grade >= 60:
    print("C")
else:
    print("F")
```

لماذا يعمل؟ بايثون تفحص الشروط من الأعلى للأسفل. `82 >= 90` خاطئ، ثم `82 >= 75` صحيح فتُطبع "B" ويتوقف الفحص. لا حاجة لكتابة `grade >= 75 and grade < 90` لأن الوصول إلى `elif` الثاني يعني تلقائيًا أن الشرط الأول لم يتحقق.
</details>

---

### تمرين 6 ⭐⭐⭐ — رصيد الحساب المصرفي

محاكاة من الكتاب: اكتب برنامجًا يفحص رصيد حساب:
- إذا كان أقل من 0: اطبع `"Balance negative. Add funds or pay penalty."`
- إذا كان يساوي 0: اطبع `"Balance is zero. Add funds soon."`
- إذا كان أكبر من 0: اطبع `"Balance is above zero."`

استخدم `balance = -15`.

💡 تلميح 1: ثلاث حالات تتطلب `if` و `elif` و `else`.

💡 تلميح 2: تحقق من الصفر بـ `== 0`.

<details>
<summary>الحل المفصّل</summary>

```python
balance = -15

if balance < 0:
    print("Balance negative. Add funds or pay penalty.")
elif balance == 0:
    print("Balance is zero. Add funds soon.")
else:
    print("Balance is above zero.")
```

المخرجات:
```text
Balance negative. Add funds or pay penalty.
```

هذا المثال مأخوذ مباشرة من الكتاب المرجعي ويوضح كيف تُستخدم الشروط في التطبيقات المالية.
</details>

---

### تمرين 7 ⭐⭐⭐⭐ — جدول التقديرات الكامل

وسّع تمرين التقدير ليطابق جدول الكتاب:
- 90 فأكثر: `"A"`
- 80 إلى 89: `"B+"`
- 70 إلى 79: `"B"`
- 65 إلى 69: `"B-"`
- أقل من 65: `"F"`

اطبع أيضًا رسالة: `"Grade: X - Letter: Y"` حيث X الدرجة و Y التقدير.

استخدم `grade = 67`.

المخرجات المتوقعة:

```text
Grade: 67 - Letter: B-
```

💡 تلميح 1: خزّن التقدير في متغير `letter` داخل كل فرع.

💡 تلميح 2: اطبع الرسالة النهائية خارج كتلة الشرط.

<details>
<summary>الحل المفصّل</summary>

```python
grade = 67

if grade >= 90:
    letter = "A"
elif grade >= 80:
    letter = "B+"
elif grade >= 70:
    letter = "B"
elif grade >= 65:
    letter = "B-"
else:
    letter = "F"

print("Grade:", grade, "- Letter:", letter)
```

لماذا يعمل؟ نخزّن النتيجة في متغير بدلًا من طباعتها مباشرة داخل كل فرع. هذا يسمح لنا باستخدام المتغير لاحقًا (في الطباعة النهائية، أو في حسابات أخرى). هذا النمط يسمى "فصل المنطق عن العرض".
</details>

---

### تمرين 8 ⭐⭐⭐⭐ — شروط متداخلة: النجاح مع مرتبة الشرف

اكتب برنامجًا:
- أولًا يتحقق: هل الطالب ناجح؟ (الدرجة >= 60)
- إذا كان ناجحًا، يتحقق من شرط داخلي: هل يستحق مرتبة الشرف؟ (الدرجة >= 90)
- إذا كان راسبًا: اطبع `"Failing grade"`.

استخدم `grade = 95`.

المخرجات المتوقعة:

```text
Passing grade: A
```

💡 تلميح 1: ضع `if` ثانية داخل كتلة `if` الأولى.

💡 تلميح 2: المستوى الثاني من المسافة البادئة = 8 مسافات.

<details>
<summary>الحل المفصّل</summary>

```python
grade = 95

if grade >= 60:
    if grade >= 90:
        print("Passing grade: A")
    elif grade >= 80:
        print("Passing grade: B")
    else:
        print("Passing grade: C")
else:
    print("Failing grade")
```

لماذا يعمل؟ الشرط الخارجي `95 >= 60` صحيح، فندخل الكتلة الأولى. ثم الشرط الداخلي `95 >= 90` صحيح أيضًا، فتُطبع "Passing grade: A". الشروط المتداخلة مفيدة عندما يكون القرار الثاني مرتبطًا بتحقيق القرار الأول.
</details>

---

### تمرين 9 ⭐⭐⭐⭐ — شروط مركبة مع and/or

مدرسة تمنح منحة دراسية إذا تحقق شرطان معًا:
- المعدل >= 90
- عدد أيام الغياب <= 3

اكتب برنامجًا يتحقق ويخزن النتيجة في متغير منطقي ثم يطبع رسالة.

```python
average = 92
absences = 2
```

المخرجات المتوقعة:

```text
Scholarship: Eligible
```

💡 تلميح 1: ادمج الشرطين بـ `and` في متغير منطقي أولًا.

💡 تلميح 2: استخدم المتغير المنطقي في `if`.

<details>
<summary>الحل المفصّل</summary>

```python
average = 92
absences = 2

is_eligible = (average >= 90) and (absences <= 3)

if is_eligible:
    print("Scholarship: Eligible")
else:
    print("Scholarship: Not eligible")
```

لماذا يعمل؟ نخزّن نتيجة الشرط المركب في متغير `is_eligible` (قيمة `True`)، ثم نستخدمه مباشرة في `if`. هذا النمط يجعل الكود أوضح وأسهل في التصحيح، لأنك تستطيع طباعة `is_eligible` وحدها لمعرفة أين المشكلة.
</details>

---

### تمرين 10 ⭐⭐⭐⭐⭐ — مشروع مصغّر: تقرير الطالب

لنبني الجزء الشرطي من **دفتر الدرجات** 📚. اكتب برنامجًا:

1. يعرف المتغيرات: `name = "Ahmad"`, `math = 85`, `science = 42`, `arabic = 78`.
2. يحسب المعدل.
3. يحدد هل الطالب ناجح (المعدل >= 60) أم راسب.
4. يحدد هل فشل في أي مادة (أي درجة < 50).
5. يطبع تقريرًا منسقًا:

```text
--- Student Report ---
Name: Ahmad
Average: 68.3
Status: Pass
Warning: Failed in Science
```

💡 تلميح 1: استخدم `or` للتحقق من الرسوب في أي مادة.

💡 تلميح 2: استخدم شروطًا متداخلة: إذا كان ناجحًا، تحقق من المواد الفردية.

<details>
<summary>الحل المفصّل</summary>

```python
name = "Ahmad"
math = 85
science = 42
arabic = 78

average = round((math + science + arabic) / 3, 1)

print("--- Student Report ---")
print("Name:", name)
print("Average:", average)

if average >= 60:
    print("Status: Pass")
    # Check individual subjects
    if math < 50:
        print("Warning: Failed in Math")
    if science < 50:
        print("Warning: Failed in Science")
    if arabic < 50:
        print("Warning: Failed in Arabic")
else:
    print("Status: Fail")
    print("Please retake all subjects.")
```

لماذا يعمل؟ البرنامج يتخذ قرارًا رئيسيًا (ناجح/راسب)، ثم داخل حالة النجاح يتخذ قرارات فرعية (هل فشل في مادة معينة؟). هذا هو الجزء الأول من دفتر الدرجات، وفي فصل الحلقات سنجعله يعمل مع عدة طلاب.
</details>

---

## مختبر الأخطاء 🧪

في كل خطأ مما يلي: **توقّع نوع الخطأ ورسالته قبل قراءة الحل**، ثم قارن.

### 🧪 خطأ 1 — النقطتان المفقودتان

```python
grade = 85
if grade >= 60
    print("Pass")
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
  File "grades.py", line 2
    if grade >= 60
                  ^
SyntaxError: expected ':'
```

السبب: كل جملة شرطية أو حلقة في بايثون يجب أن تنتهي بنقطتين `:`. هذه قاعدة تركيبة صارمة.

الإصلاح:

```python
grade = 85
if grade >= 60:
    print("Pass")
```
</details>

---

### 🧪 خطأ 2 — المسافة البادئة المفقودة

```python
grade = 85
if grade >= 60:
print("Pass")
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
  File "grades.py", line 3
    print("Pass")
    ^
IndentationError: expected an indented block after 'if' statement on line 2
```

السبب: بايثون تستخدم المسافة البادئة لتحديد الكود التابع للشرط. بدونها، لا تعرف بايثون أي كود يجب تنفيذه عند تحقق الشرط.

الإصلاح: أضف 4 مسافات قبل `print`:

```python
grade = 85
if grade >= 60:
    print("Pass")
```
</details>

---

### 🧪 خطأ 3 — الإسناد بدل المقارنة

```python
grade = 85
if grade = 60:
    print("Equal to 60")
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
  File "grades.py", line 2
    if grade = 60:
       ^^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```

السبب: علامة `=` تعني الإسناد (ضع القيمة هنا)، ولا يصح استخدامها داخل شرط. المقارنة تحتاج `==`. في Python 3.12+ قد تقترح الرسالة الحل مباشرة.

الإصلاح:

```python
grade = 85
if grade == 60:
    print("Equal to 60")
```
</details>

---

### 🧪 خطأ 4 — متغير غير معرّف في الشرط

```python
if score >= 60:
    print("Pass")
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "grades.py", line 1, in <module>
    if score >= 60:
       ^^^^^
NameError: name 'score' is not defined
```

السبب: استخدمنا متغير `score` في الشرط لكننا لم نعرفه أبدًا. بايثون تبحث عن الاسم ولا تجده.

الإصلاح: عرّف المتغير قبل استخدامه:

```python
score = 75
if score >= 60:
    print("Pass")
```
</details>

---

### 🧪 خطأ 5 — مقارنة نص بعدد في الشرط

```python
grade = "85"
if grade >= 60:
    print("Pass")
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:

```text
Traceback (most recent call last):
  File "grades.py", line 2, in <module>
    if grade >= 60:
       ^^^^^^^^^^^
TypeError: '>=' not supported between instances of 'str' and 'int'
```

السبب: المتغير `grade` نص `"85"` (بين اقتباس)، ولا يمكن مقارنة نص بعدد. هذا خطأ شائع عند قراءة بيانات من ملفات أو مدخلات المستخدم.

الإصلاح:

```python
grade = "85"
grade = int(grade)  # Convert string to integer
if grade >= 60:
    print("Pass")
```
</details>

---

## تحدي المتعة 🎮 — حارس البوابة

اكتب برنامج "حارس بوابة" يسأل (بمتغيرات فقط، بدون `input` بعد):
- هل معك تذكرة؟ (`has_ticket = True`)
- هل عمرك >= 12؟ (`age = 14`)
- هل الطول >= 140 سم؟ (`height = 155`)

ادخل إذا تحققت الشروط الثلاثة. اطبع قرار الدخول.

ثم جرّب تغيير القيم لترى حالات الرفض المختلفة.

<details>
<summary>الحل</summary>

```python
has_ticket = True
age = 14
height = 155

if has_ticket and age >= 12 and height >= 140:
    print("Welcome! You may enter.")
elif not has_ticket:
    print("Denied: No ticket.")
elif age < 12:
    print("Denied: Too young.")
else:
    print("Denied: Not tall enough.")
```

جرّب: ماذا يحدث لو `has_ticket = False`؟ أو `age = 10`؟
</details>

---

## أخطاء شائعة عند المبتدئين

1. **نسيان النقطتين `:`** بعد `if` أو `elif` أو `else`. هذا أكثر خطأ شيوعًا.
2. **عدم المسافة البادئة**: الكود داخل `if` يجب أن يكون مُزاحًا بـ 4 مسافات.
3. **الخلط بين `=` و `==`**: الأولى إسناد، الثانية مقارنة.
4. **كتابة `else if` بدل `elif`**: في بايثون الكلمة هي `elif` فقط.
5. **وضع شرط بعد `else`**: مثل `else grade < 60:` — هذا خطأ، `else` لا تأخذ شرطًا.
6. **مقارنة نص بعدد**: تأكد من تحويل المدخلات النصية إلى أرقام قبل المقارنة.
7. **نسيان أن `elif` يُفحص فقط إذا فشل ما قبله**: لا تحتاج لكتابة `grade >= 75 and grade < 90` في `elif` الثاني إذا كان الأول `grade >= 90`.

## قائمة تحقق ✅

قبل الانتقال إلى الفصل التالي، تأكد أنك تستطيع:

- [ ] كتابة `if` مع شرط وملاحظة النقطتين والمسافة البادئة.
- [ ] إضافة `else` للحالة البديلة.
- [ ] استخدام `elif` لعدة شروط متتالية.
- [ ] بناء شروط متداخلة (شرط داخل شرط).
- [ ] دمج الشروط بـ `and` و `or` و `not`.
- [ ] قراءة أخطاء `SyntaxError` و `IndentationError` وإصلاحها.

**ماذا سيعتمد عليه الفصل القادم؟** فصل «الحلقات»: سنتعلم تكرار الكود. ستُدمج الحلقات مع الشروط لإنشاء برامج تتكرر وتتخذ قرارات في كل تكرار — مثل فحص درجات كل طالب في قائمة واحدة تلو الأخر.