# الدوال (Functions)

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. تعريف الدوال باستخدام الكلمة المفتاحية `def` واستدعاؤها.
2. استخدام المعاملات (Parameters) والوسائط (Arguments) لتمرير البيانات.
3. إرجاع القيم من الدوال باستخدام `return`.
4. استخدام المعاملات الافتراضية والوسائط المسماة (Keyword Arguments).
5. استخدام `*args` و `**kwargs` لتمرير عدد متغير من الوسائط.
6. فهم نطاق المتغيرات (Scope) داخل وخارج الدوال.

📖 يقابل هذا الفصل: **الفصل 16 «الدوال: تعريفها واستعمالها»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- المتغيرات تخزن البيانات، والشروط (`if`) تتخذ القرارات، والحلقات (`for`/`while`) تكرر المهام.
- القواميس (`dict`) تخزن البيانات بأزواج مفتاح-قيمة، وهي مثالية لتمثيل بيانات الطلاب.
- الدوال هي كتل من الكود تُنفذ فقط عندما يتم استدعاؤها، وتساعد على تجنب تكرار الكود (مبدأ DRY: Don't Repeat Yourself).

## إحماء 🔥

توقّع المخرجات على ورقة أولًا، ثم شغّل الكود وقارن.

### إحماء 1

```python
def greet():
    print("Welcome to the Gradebook!")

greet()
```

<details>
<summary>الحل</summary>

```text
Welcome to the Gradebook!
```

الدالة `greet()` تُعرّف أولاً، ثم تُستدعى في السطر الأخير لتطبع الرسالة.
</details>

### إحماء 2

```python
def print_grade(student, grade):
    print(student, "scored", grade)

print_grade("Ahmad", 85)
```

<details>
<summary>الحل</summary>

```text
Ahmad scored 85
```

الدالة تأخذ معاملين (`student` و `grade`) وتستخدمهما داخل كتلة الدالة.
</details>

### إحماء 3

```python
def add_bonus(grade):
    return grade + 5

final = add_bonus(90)
print(final)
```

<details>
<summary>الحل</summary>

```text
95
```

الكلمة `return` تُرجع القيمة `95` إلى المتغير `final`، ثم تتم طباعتها.
</details>

---

## التمارين

### تمرين 1 ⭐ — أول دالة

اكتب دالة باسم `print_header()` تطبع عنوانًا لدفتر الدرجات مثل `"--- Student Grades ---"`، ثم استدعِها مرتين.

💡 تلميح 1: استخدم `def` متبوعة باسم الدالة وأقواس فارغة `()`.

💡 تلميح 2: لا تنسَ النقطتين `:` والمسافة البادئة.

<details>
<summary>الحل المفصّل</summary>

```python
def print_header():
    print("--- Student Grades ---")

print_header()
print_header()
```
</details>

---

### تمرين 2 ⭐ — دالة بمعامل واحد

اكتب دالة `check_pass(grade)` تتحقق من الدرجة. إذا كانت 60 أو أكثر تطبع `"Pass"`، وإلا تطبع `"Fail"`. استدعِها بدرجتين مختلفتين.

💡 تلميح 1: ضع جملة `if/else` داخل الدالة.

💡 تلميح 2: مرّر الأرقام مباشرة عند الاستدعاء: `check_pass(75)`.

<details>
<summary>الحل المفصّل</summary>

```python
def check_pass(grade):
    if grade >= 60:
        print("Pass")
    else:
        print("Fail")

check_pass(75) # Pass
check_pass(45) # Fail
```
</details>

---

### تمرين 3 ⭐⭐ — إرجاع القيم (Return)

اكتب دالة `calculate_average(g1, g2, g3)` تحسب متوسط ثلاث درجات وتُرجع الناتج. خزّن الناتج في متغير واطبعه.

💡 تلميح 1: استخدم `return` بدلاً من `print` داخل الدالة.

💡 تلميح 2: المتوسط = `(g1 + g2 + g3) / 3`.

<details>
<summary>الحل المفصّل</summary>

```python
def calculate_average(g1, g2, g3):
    total = g1 + g2 + g3
    return total / 3

avg = calculate_average(80, 90, 100)
print("Average:", avg) # Average: 90.0
```

لماذا `return` وليس `print`؟ لأن `return` تجعل الدالة تُنتج قيمة يمكن تخزينها أو استخدامها في حسابات أخرى، بينما `print` تعرضها على الشاشة فقط وتُرجع `None`.
</details>

---

### تمرين 4 ⭐⭐⭐ — المعاملات الافتراضية

اكتب دالة `print_report(name, grade, status="Pass")` تطبع تقرير طالب. اجعل `"Pass"` هي القيمة الافتراضية للمعامل `status`. استدعِها مرة بمعاملين فقط، ومرة بثلاثة.

💡 تلميح 1: المعاملات الافتراضية توضع في نهاية قائمة المعاملات: `def func(a, b="default")`.

💡 تلميح 2: إذا لم تمرر قيمة لـ `status`، ستأخذ القيمة الافتراضية تلقائيًا.

<details>
<summary>الحل المفصّل</summary>

```python
def print_report(name, grade, status="Pass"):
    print(f"Name: {name}, Grade: {grade}, Status: {status}")

print_report("Salma", 92)             # Uses default status
print_report("Omar", 45, "Fail")      # Overrides default status
```
</details>

---

### تمرين 5 ⭐⭐⭐ — الوسائط المسماة (Keyword Arguments)

لديك دالة `create_student(name, age, grade)`. استدعِها باستخدام الوسائط المسماة بترتيب مختلف عن تعريف الدالة.

💡 تلميح 1: الصيغة: `func(arg_name=value)`.

💡 تلميح 2: هذا يسمح لك بتمرير الوسائط بأي ترتيب تريده.

<details>
<summary>الحل المفصّل</summary>

```python
def create_student(name, age, grade):
    print(f"{name} is {age} years old, grade: {grade}")

# Calling with keyword arguments in different order
create_student(grade=85, name="Ahmad", age=14)
```
</details>

---

### تمرين 6 ⭐⭐⭐⭐ — عدد متغير من الوسائط (`*args`)

اكتب دالة `sum_grades(*grades)` تأخذ أي عدد من الدرجات وتُرجع مجموعها.

💡 تلميح 1: العلامة `*` قبل اسم المعامل تجعله يستقبل أي عدد من الوسائط كـ "صف" (Tuple).

💡 تلميح 2: استخدم حلقة `for` لجمع الأرقام، أو استخدم الدالة المدمجة `sum()`.

<details>
<summary>الحل المفصّل</summary>

```python
def sum_grades(*grades):
    return sum(grades)

print(sum_grades(80, 90))          # 170
print(sum_grades(80, 90, 75, 100)) # 345
```
</details>

---

### تمرين 7 ⭐⭐⭐⭐ — قاموس الوسائط (`**kwargs`)

اكتب دالة `print_details(**kwargs)` تستقبل أي عدد من أزواج المفتاح-القيمة وتطبعها.

💡 تلميح 1: العلامة `**` تجعل المعامل يستقبل الوسائط كقاموس (Dictionary).

💡 تلميح 2: استخدم حلقة `for key, value in kwargs.items():`.

<details>
<summary>الحل المفصّل</summary>

```python
def print_details(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_details(Name="Layla", Math=95, Science=88)
```
</details>

---

### تمرين 8 ⭐⭐⭐⭐ — نطاق المتغيرات (Scope)

توقع المخرجات، ثم شغّل الكود لفهم الفرق بين المتغير المحلي (Local) والعالمي (Global).

```python
school_name = "Al-Noor" # Global

def change_school():
    school_name = "Al-Najah" # Local
    print("Inside:", school_name)

change_school()
print("Outside:", school_name)
```

💡 تلميح 1: المتغير المحلي يختفي بانتهاء الدالة.

💡 تلميح 2: المتغير العالمي لا يتأثر بما يحدث داخل الدالة إلا إذا استخدمنا `global`.

<details>
<summary>الحل المفصّل</summary>

```text
Inside: Al-Najah
Outside: Al-Noor
```

لماذا يعمل؟ المتغير `school_name` داخل الدالة هو متغير **محلي** جديد تمامًا، ولا يمس المتغير **العالمي** الخارجي. لتعديل العالمي من الداخل، نحتاج لكتابة `global school_name` في أول سطر بالدالة (لكن يُنصح بتجنب ذلك والاعتماد على `return`).
</details>

---

### تمرين 9 ⭐⭐⭐⭐⭐ — مشروع مصغّر: دوال دفتر الدرجات 📚

لنبني النواة المنطقية لـ **دفتر الدرجات** باستخدام الدوال. 
اكتب برنامجًا يحتوي على:
1. قاموس عالمي `gradebook` لتخزين الطلاب.
2. دالة `add_student(name, grade)` تضيف طالبًا للقاموس.
3. دالة `get_average()` تحسب وتُرجع متوسط درجات كل الطلاب في القاموس.
4. دالة `print_all()` تطبع كل الطلاب وحالاتهم.

💡 تلميح 1: استخدم `gradebook.update({name: grade})` أو `gradebook[name] = grade`.

💡 تلميح 2: في `get_average()`، استخدم `gradebook.values()` للحصول على الدرجات.

<details>
<summary>الحل المفصّل</summary>

```python
gradebook = {}

def add_student(name, grade):
    gradebook[name] = grade
    print(f"Added {name}.")

def get_average():
    if not gradebook:
        return 0
    total = sum(gradebook.values())
    return round(total / len(gradebook), 1)

def print_all():
    print("--- Gradebook ---")
    for name, grade in gradebook.items():
        status = "Pass" if grade >= 60 else "Fail"
        print(f"{name}: {grade} ({status})")
    print(f"Class Average: {get_average()}")

# Testing the system
add_student("Ahmad", 85)
add_student("Salma", 92)
add_student("Omar", 55)
print_all()
```

هذا هو جوهر البرمجة الهيكلية! لقد فصلنا المنطق (logic) عن التنفيذ (execution).
</details>

---

## مختبر الأخطاء 🧪

### 🧪 خطأ 1 — نسيان النقطتين في تعريف الدالة

```python
def greet()
    print("Hello")
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
SyntaxError: expected ':'
```
السبب: كل تعريف لدالة أو حلقة أو شرط في بايثون يجب أن ينتهي بنقطتين `:`.
الإصلاح: أضف النقطتين `def greet():`.
</details>

---

### 🧪 خطأ 2 — نسيان إرجاع القيمة

```python
def multiply(a, b):
    result = a * b

x = multiply(5, 4)
print(x + 10)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
TypeError: unsupported operand type(s) for +: 'NoneType' and 'int'
```
السبب: الدالة التي لا تحتوي على `return` تُرجع `None` افتراضيًا. عند محاولة جمع `None + 10` يحدث خطأ.
الإصلاح: أضف `return result` في نهاية الدالة.
</details>

---

### 🧪 خطأ 3 — عدد وسائط غير مطابق

```python
def add(a, b):
    return a + b

print(add(5))
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
TypeError: add() missing 1 required positional argument: 'b'
```
السبب: الدالة تتوقع معاملين، لكننا مررنا واحدًا فقط.
الإصلاح: مرّر الوسائط المطلوبة `add(5, 10)`، أو اجعل المعامل الثاني افتراضيًا `def add(a, b=0):`.
</details>

---

## أخطاء شائعة عند المبتدئين

1. **الخلط بين `print` و `return`**: `print` تعرض النص للمستخدم، `return` تعيد القيمة للبرنامج ليستخدمها.
2. **استدعاء الدالة قبل تعريفها**: بايثون يقرأ الكود من الأعلى للأسفل. يجب تعريف الدالة قبل استدعائها.
3. **نسيان الأقواس عند الاستدعاء**: كتابة `my_func` تشير إلى كائن الدالة نفسه، بينما `my_func()` تنفذها.
4. **تعديل المتغيرات العالمية مباشرة**: يُفضل تمرير البيانات كوسائط وإرجاع النتائج بـ `return` بدلاً من استخدام `global`.

## قائمة تحقق ✅

- [ ] تعريف واستدعاء الدوال.
- [ ] استخدام المعاملات والوسائط.
- [ ] إرجاع القيم باستخدام `return`.
- [ ] استخدام `*args` و `**kwargs`.
- [ ] فهم النطاق (Scope) المحلي والعالمي.

**ماذا سيعتمد عليه الفصل القادم؟** الآن لدينا دوال رائعة، لكن وضعها كلها في ملف واحد يجعل البرنامج فوضويًا. في فصل «الوحدات»، سنتعلم كيف نقسم هذه الدوال إلى ملفات منفصلة ونستوردها!