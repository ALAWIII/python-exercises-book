# بناء الأصناف واستنساخ الكائنات

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. تعريف صنف (Class) باستخدام الكلمة المفتاحية `class`.
2. إنشاء كائنات (Objects) من الصنف باستخدام الباني `__init__()`.
3. استخدام `self` للإشارة إلى الكائن الحالي داخل الصنف.
4. التمييز بين متغيرات الصنف (Class Variables) ومتغيرات النسخة (Instance Variables).
5. تعريف توابع (Methods) تعمل على الكائنات.

📖 يقابل هذا الفصل: **الفصل 18 «بناء الأصناف واستنساخ الكائنات»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- الدوال تُعرَّف بـ `def` وتُستدعى بأقواس `()`.
- القواميس تخزن بيانات بأزواج مفتاح-قيمة.
- المتغيرات تخزن قيمًا، والحلقات تكرر المهام.
- كل شيء في بايثون هو كائن: الأرقام، النصوص، القوائم، القواميس.
- الصنف (Class) هو مخطط (قالب) لإنشاء كائنات من نفس النوع.

## إحماء 🔥

توقّع المخرجات على ورقة أولًا، ثم شغّل الكود وقارن.

### إحماء 1

```python
class Student:
    def __init__(self, name):
        self.name = name

s = Student("Ahmad")
print(s.name)
```

<details>
<summary>الحل</summary>

```text
Ahmad
```

الصنف `Student` يُعرَّف بباني يأخذ اسمًا. عند إنشاء الكائن `s`، يُستدعى `__init__` تلقائيًا ويُخزن الاسم.
</details>

### إحماء 2

```python
class Student:
    school = "Al-Noor School"
    def __init__(self, name):
        self.name = name

s1 = Student("Ahmad")
s2 = Student("Salma")
print(s1.school)
print(s2.school)
```

<details>
<summary>الحل</summary>

```text
Al-Noor School
Al-Noor School
```

المتغير `school` هو متغير صنف (Class Variable) — مشترك بين كل النسخ. كل كائن يمكنه الوصول إليه.
</details>

### إحماء 3

```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

    def is_passing(self):
        return self.grade >= 60

s = Student("Omar", 55)
print(s.is_passing())
```

<details>
<summary>الحل</summary>

```text
False
```

التابع `is_passing()` يتحقق من درجة الكائن الحالي. بما أن 55 أقل من 60، النتيجة `False`.
</details>

---

## التمارين

### تمرين 1 ⭐ — أول صنف

أنشئ صنفًا باسم `Book` يحتوي على باني `__init__` يأخذ `title` و `author`. ثم أنشئ كائنًا منه واطبع العنوان.

المخرجات المتوقعة:

```text
Python Basics
```

💡 تلميح 1: الصنف يبدأ بـ `class Book:`.

💡 تلميح 2: داخل الباني، خزّن القيم في `self.title` و `self.author`.

<details>
<summary>الحل المفصّل</summary>

```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

my_book = Book("Python Basics", "Hsoub Academy")
print(my_book.title)
```

لماذا يعمل؟ `class` تُعرّف قالبًا. عند استدعاء `Book(...)` تُنشأ نسخة جديدة ويُستدعى `__init__` تلقائيًا. `self` تشير إلى النسخة الجديدة نفسها.
</details>

---

### تمرين 2 ⭐ — صنف بدون باني

أنشئ صنفًا باسم `Marker` بدون باني. أضف له متغير صنف `color = "red"`. أنشئ كائنًا واطبع اللون.

المخرجات المتوقعة:

```text
red
```

💡 تلميح 1: الصنف لا يحتاج `__init__` إذا لم يكن لديك قيم أولية.

💡 تلميح 2: متغير الصنف يُعرَّف مباشرة داخل الصنف.

<details>
<summary>الحل المفصّل</summary>

```python
class Marker:
    color = "red"

m = Marker()
print(m.color)
```

الصنف بدون باني صالح تمامًا. عند استدعاء `Marker()` تُنشأ نسخة فارغة، لكنها ترث متغيرات الصنف.
</details>

---

### تمرين 3 ⭐⭐ — متغيرات الصنف والنسخة

أنشئ صنف `Student` يحتوي على:
- متغير صنف: `school = "Al-Noor School"`
- متغيرات نسخة: `name` و `grade` (يُمرران في الباني)

أنشئ كائنين واطبع اسم كل طالب والمدرسة.

المخرجات المتوقعة:

```text
Ahmad - Al-Noor School
Salma - Al-Noor School
```

💡 تلميح 1: متغير الصنف يُكتب خارج الباني.

💡 تلميح 2: متغيرات النسخة تُكتب داخل الباني بـ `self.variable = value`.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    school = "Al-Noor School"

    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

s1 = Student("Ahmad", 85)
s2 = Student("Salma", 92)

print(s1.name, "-", s1.school)
print(s2.name, "-", s2.school)
```

لماذا يعمل؟ `school` مشترك بين كل النسخ (متغير صنف). أما `name` و `grade` فخاصة بكل نسخة على حدة (متغيرات نسخة).
</details>

---

### تمرين 4 ⭐⭐⭐ — تابع بسيط

أضف للصنف `Student` تابعًا باسم `get_status()` يُرجع `"Pass"` إذا كانت الدرجة >= 60، وإلا `"Fail"`.

```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade
    # أضف التابع هنا
```

المخرجات المتوقعة:

```text
Ahmad: Pass
Omar: Fail
```

💡 تلميح 1: التابع يحتاج `self` كمعامل أول دائمًا.

💡 تلميح 2: استخدم `self.grade` للوصول لدرجة الكائن.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

    def get_status(self):
        if self.grade >= 60:
            return "Pass"
        else:
            return "Fail"

s1 = Student("Ahmad", 85)
s2 = Student("Omar", 45)

print(s1.name + ":", s1.get_status())
print(s2.name + ":", s2.get_status())
```

لماذا يعمل؟ `self.grade` تشير إلى درجة الكائن الذي استدعى التابع. عند استدعاء `s1.get_status()` تكون `self` هي `s1`، وعند `s2.get_status()` تكون `self` هي `s2`.
</details>

---

### تمرين 5 ⭐⭐⭐ — تابع لتعديل البيانات

أضف تابع `update_grade(new_grade)` للصنف `Student` يغيّر درجة الطالب ثم يطبع رسالة تأكيد.

المخرجات المتوقعة:

```text
Grade updated from 55 to 70
New status: Pass
```

💡 تلميح 1: `self.grade = new_grade` يغيّر القيمة.

💡 تلميح 2: أعد استخدام `get_status()` بعد التعديل.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

    def get_status(self):
        if self.grade >= 60:
            return "Pass"
        return "Fail"

    def update_grade(self, new_grade):
        old = self.grade
        self.grade = new_grade
        print("Grade updated from", old, "to", new_grade)

s = Student("Layla", 55)
s.update_grade(70)
print("New status:", s.get_status())
```
</details>

---

### تمرين 6 ⭐⭐⭐⭐ — صنف بقائمة درجات

أنشئ صنف `Student` يخزن اسم الطالب و**قائمة** درجات. أضف توابع:
- `add_grade(grade)` لإضافة درجة.
- `get_average()` لحساب المعدل.
- `get_highest()` لإيجاد أعلى درجة.

المخرجات المتوقعة:

```text
Average: 85.0
Highest: 92
```

💡 تلميح 1: خزّن القائمة في `self.grades = []`.

💡 تلميح 2: استخدم `sum()` و `len()` و `max()` داخل التوابع.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.grades = []

    def add_grade(self, grade):
        self.grades.append(grade)

    def get_average(self):
        if len(self.grades) == 0:
            return 0
        return round(sum(self.grades) / len(self.grades), 1)

    def get_highest(self):
        if len(self.grades) == 0:
            return 0
        return max(self.grades)

s = Student("Noor")
s.add_grade(85)
s.add_grade(92)
s.add_grade(78)

print("Average:", s.get_average())
print("Highest:", s.get_highest())
```

هذا هو الجزء الأول من **دفتر الدرجات** 📚 الكائني. كل طالب كائن مستقل بقائمة درجاته الخاصة.
</details>

---

### تمرين 7 ⭐⭐⭐⭐ — تمثيل نصي للكائن

أضف تابعًا خاصًا `__str__()` للصنف `Student` يُرجع نصًا يصف الكائن. عند طباعة الكائن مباشرة، سيُستدعى هذا التابع.

المخرجات المتوقعة:

```text
Student: Ahmad | Grade: 85 | Status: Pass
```

💡 تلميح 1: التابع الخاص يبدأ وينتهي بشرطتين سفليتين: `__str__`.

💡 تلميح 2: يجب أن يُرجع سلسلة نصية بـ `return`.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

    def __str__(self):
        status = "Pass" if self.grade >= 60 else "Fail"
        return "Student: " + self.name + " | Grade: " + str(self.grade) + " | Status: " + status

s = Student("Ahmad", 85)
print(s)
```

لماذا يعمل؟ عندما تكتب `print(s)`، تبحث بايثون عن `__str__()` في كائن `s` وتستدعيه للحصول على النص. بدون هذا التابع، ستطبع بايثون عنوان الذاكرة الافتراضي.
</details>

---

### تمرين 8 ⭐⭐⭐⭐⭐ — مشروع مصغّر: دفتر الدرجات الكائني 📚

لنبني النسخة الكائنية النهائية من **دفتر الدرجات**! أنشئ صنفين:

1. `Student`: يخزن الاسم وقائمة الدرجات، مع توابع `add_grade()`, `get_average()`, `get_status()`.
2. `Gradebook`: يخزن قائمة طلاب، مع توابع `add_student()`, `get_class_average()`, `print_report()`.

المخرجات المتوقعة:

```text
=== Grade Book Report ===
Ahmad: Average=85.0 (Pass)
Salma: Average=92.0 (Pass)
Omar: Average=55.0 (Fail)
---------------------------
Class Average: 77.3
Pass Rate: 66.7%
```

💡 تلميح 1: `Gradebook` يحتوي على قائمة من كائنات `Student`.

💡 تلميح 2: `get_class_average()` تمر على كل طالب وتحسب معدله.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.grades = []

    def add_grade(self, grade):
        self.grades.append(grade)

    def get_average(self):
        if not self.grades:
            return 0
        return round(sum(self.grades) / len(self.grades), 1)

    def get_status(self):
        return "Pass" if self.get_average() >= 60 else "Fail"


class Gradebook:
    def __init__(self):
        self.students = []

    def add_student(self, student):
        self.students.append(student)

    def get_class_average(self):
        if not self.students:
            return 0
        total = sum(s.get_average() for s in self.students)
        return round(total / len(self.students), 1)

    def print_report(self):
        print("=== Grade Book Report ===")
        pass_count = 0
        for s in self.students:
            print(s.name + ": Average=" + str(s.get_average()) + " (" + s.get_status() + ")")
            if s.get_status() == "Pass":
                pass_count += 1

        print("---------------------------")
        print("Class Average:", self.get_class_average())
        pass_rate = round((pass_count / len(self.students)) * 100, 1)
        print("Pass Rate:", str(pass_rate) + "%")


# Building the gradebook
gb = Gradebook()

ahmad = Student("Ahmad")
ahmad.add_grade(85)
ahmad.add_grade(90)
ahmad.add_grade(80)

salma = Student("Salma")
salma.add_grade(95)
salma.add_grade(92)
salma.add_grade(89)

omar = Student("Omar")
omar.add_grade(50)
omar.add_grade(55)
omar.add_grade(60)

gb.add_student(ahmad)
gb.add_student(salma)
gb.add_student(omar)

gb.print_report()
```

تهانينا! 🎉 لقد بنيت برنامجًا كائني التوجه كاملًا. كل طالب كائن مستقل، ودفتر الدرجات كائن يدير مجموعة طلاب. هذا هو جوهر البرمجة الكائنية.
</details>

---

## مختبر الأخطاء 🧪

### 🧪 خطأ 1 — نسيان self

```python
class Student:
    def __init__(name, grade):
        self.name = name

s = Student("Ahmad", 85)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
TypeError: Student.__init__() takes 2 positional arguments but 3 were given
```

السبب: كل تابع داخل صنف يأخذ `self` كمعامل أول تلقائيًا. عندما نسيته، ظنت بايثون أنك مرّرت 3 وسائط (الكائن نفسه + "Ahmad" + 85) لدالة تتوقع 2 فقط.

الإصلاح:
```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade
```
</details>

---

### 🧪 خطأ 2 — استدعاء تابع بدون أقواس

```python
class Student:
    def __init__(self, name):
        self.name = name

    def greet(self):
        return "Hello, " + self.name

s = Student("Ahmad")
print(s.greet)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
<bound method Student.greet of <__main__.Student object at 0x...>>
```

لا خطأ فعلي، لكن الناتج ليس ما تتوقعه! `s.greet` بدون أقواس يُرجع **كائن التابع نفسه** (مرجع للدالة)، وليس **نتيجة** استدعائها.

الإصلاح: أضف الأقواس لاستدعاء التابع:
```python
print(s.greet())  # Hello, Ahmad
```
</details>

---

### 🧪 خطأ 3 — الوصول لمتغير غير معرّف

```python
class Student:
    def __init__(self, name):
        self.name = name

s = Student("Ahmad")
print(s.grade)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
AttributeError: 'Student' object has no attribute 'grade'
```

السبب: حاولت الوصول لمتغير `grade` لكنه لم يُعرَّف في الباني. الكائن لا يحتوي إلا على `name`.

الإصلاح: عرّف المتغير في الباني:
```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade
```
</details>

---

## تحدي المتعة 🎮 — صنف الحساب المصرفي

أنشئ صنف `BankAccount` يحتوي على:
- `__init__(owner, balance=0)`
- `deposit(amount)` لإيداع مبلغ.
- `withdraw(amount)` لسحب مبلغ (مع التحقق من كفاية الرصيد).
- `__str__()` لطباعة الرصيد بشكل جميل.

جرّب إيداعًا وسحبًا وتجاوز الرصيد.

<details>
<summary>الحل</summary>

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        self.balance += amount
        print("Deposited:", amount, "| New balance:", self.balance)

    def withdraw(self, amount):
        if amount > self.balance:
            print("Insufficient funds!")
        else:
            self.balance -= amount
            print("Withdrawn:", amount, "| New balance:", self.balance)

    def __str__(self):
        return "Account: " + self.owner + " | Balance: " + str(self.balance)

acc = BankAccount("Ahmad", 100)
acc.deposit(50)
acc.withdraw(30)
acc.withdraw(200)
print(acc)
```
</details>

---

## أخطاء شائعة عند المبتدئين

1. **نسيان `self`** في تعريف التابع أو عند الوصول للمتغيرات.
2. **الخلط بين متغيرات الصنف والنسخة**: متغير الصنف مشترك، ومتغير النسخة خاص.
3. **استدعاء الصنف بدون أقواس**: `Student` يشير للصنف نفسه، `Student()` يُنشئ نسخة.
4. **نسيان الأقواس عند استدعاء تابع**: `s.greet` لا يستدعي التابع، `s.greet()` يستدعيه.
5. **الخلط بين `__init__` و `init`**: الباني يبدأ وينتهي بشرطتين سفليتين مزدوجتين.

## قائمة تحقق ✅

- [ ] تعريف صنف وإنشاء كائنات منه.
- [ ] استخدام الباني `__init__` و `self`.
- [ ] التمييز بين متغيرات الصنف ومتغيرات النسخة.
- [ ] تعريف توابع تعمل على الكائنات.
- [ ] فهم `__str__` وطباعة الكائنات.
- [ ] بناء برنامج كائني كامل (دفتر الدرجات).

**ماذا سيعتمد عليه الفصل القادم؟** فصل «الوراثة»: سنتعلم كيف نُنشئ أصنافًا جديدة ترث من أصناف موجودة، مما يوفر علينا إعادة كتابة الكود المشترك.