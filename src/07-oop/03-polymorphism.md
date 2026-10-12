# التعددية الشكلية وتطبيقاتها

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. فهم مفهوم التعددية الشكلية (Polymorphism): واجهة موحدة لأشكال متعددة.
2. استخدام «التبط» (Duck Typing): إذا سار كالبطة وصاح كالبطة، فهو بطة.
3. كتابة دوال تعمل مع كائنات من أصناف مختلفة بنفس الطريقة.
4. استخدام التجاوز (Overriding) لتحقيق التعددية الشكلية.

📖 يقابل هذا الفصل: **الفصل 20 «التعددية الشكلية وتطبيقاتها»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- الصنف الفرعي يرث توابع الصنف الأساس.
- يمكن إعادة تعريف التوابع في الصنف الفرعي.
- `super()` تستدعي توابع الصنف الأساس.
- `isinstance(obj, Class)` تتحقق من نوع الكائن.

## إحماء 🔥

### إحماء 1

```python
class Dog:
    def speak(self):
        return "Woof!"

class Cat:
    def speak(self):
        return "Meow!"

def make_sound(animal):
    print(animal.speak())

make_sound(Dog())
make_sound(Cat())
```

<details>
<summary>الحل</summary>

```text
Woof!
Meow!
```

الدالة `make_sound` لا تعرف نوع الكائن، لكنها تستدعي `speak()` الموجود في كليهما. هذا هو جوهر التعددية الشكلية.
</details>

### إحماء 2

```python
class Shape:
    def area(self):
        return 0

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def area(self):
        return 3.14 * self.radius ** 2

class Square(Shape):
    def __init__(self, side):
        self.side = side
    def area(self):
        return self.side ** 2

shapes = [Circle(5), Square(4)]
for s in shapes:
    print(s.area())
```

<details>
<summary>الحل</summary>

```text
78.5
16
```

الحلقة تمر على كائنات مختلفة، لكن كل كائن يستجيب لـ `area()` بطريقته الخاصة.
</details>

---

## التمارين

### تمرين 1 ⭐⭐ — دالة متعددة الأشكال

اكتب دالة `print_info(obj)` تستدعي `__str__()` على أي كائن. أنشئ صنفين مختلفين بتابع `__str__` مختلف لكل منهما.

💡 تلميح 1: لا تحتاج للتحقق من نوع الكائن.

💡 تلميح 2: كل صنف يعرّف `__str__` خاص به.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name):
        self.name = name
    def __str__(self):
        return "Student: " + self.name

class Teacher:
    def __init__(self, name, subject):
        self.name = name
        self.subject = subject
    def __str__(self):
        return "Teacher: " + self.name + " (" + self.subject + ")"

def print_info(obj):
    print(obj)

print_info(Student("Ahmad"))
print_info(Teacher("Mr. Ali", "Math"))
```
</details>

---

### تمرين 2 ⭐⭐⭐ — دفتر الدرجات المتعدد الأشكال 📚

أنشئ صنفين: `RegularStudent` و `ScholarshipStudent`. كلاهما لديه تابع `get_report()`. اكتب دالة `print_reports(students)` تمر على قائمة طلاب وتطبع تقرير كل منهم.

💡 تلميح 1: لا تستخدم `isinstance()` — اعتمد على التعددية الشكلية.

💡 تلميح 2: كل صنف يعرّف `get_report()` بطريقته.

<details>
<summary>الحل المفصّل</summary>

```python
class RegularStudent:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

    def get_report(self):
        status = "Pass" if self.grade >= 60 else "Fail"
        return self.name + ": " + str(self.grade) + " (" + status + ")"

class ScholarshipStudent:
    def __init__(self, name, grade, discount):
        self.name = name
        self.grade = grade
        self.discount = discount

    def get_report(self):
        return self.name + ": " + str(self.grade) + " (Scholarship, " + str(self.discount) + "% discount)"

def print_reports(students):
    print("=== Student Reports ===")
    for s in students:
        print(s.get_report())

students = [
    RegularStudent("Ahmad", 85),
    ScholarshipStudent("Salma", 95, 20),
    RegularStudent("Omar", 55),
    ScholarshipStudent("Noor", 92, 15),
]

print_reports(students)
```

لاحظ أن الدالة `print_reports` لا تعرف شيئًا عن أنواع الطلاب. تستدعي `get_report()` فقط، وكل كائن يستجيب بطريقته. هذا هو جمال التعددية الشكلية.
</details>

---

### تمرين 3 ⭐⭐⭐⭐ — التبط (Duck Typing)

أنشئ ثلاثة أصناف: `FileReport`, `EmailReport`, `ConsoleReport`. كل منها لديه تابع `send()`. اكتب دالة `notify(report)` تستدعي `send()` على أي كائن.

💡 تلميح 1: لا تحتاج لصنف أساس مشترك.

💡 تلميح 2: طالما الكائن لديه `send()`، فهو يعمل.

<details>
<summary>الحل المفصّل</summary>

```python
class FileReport:
    def send(self):
        return "Saving report to file..."

class EmailReport:
    def send(self):
        return "Sending report via email..."

class ConsoleReport:
    def send(self):
        return "Printing report to console..."

def notify(report):
    print(report.send())

notify(FileReport())
notify(EmailReport())
notify(ConsoleReport())
```

هذا هو مبدأ «التبط»: لا يهم ما نوع الكائن، طالما لديه التابع المطلوب، سيعمل. بايثون لا تتحقق من النوع — تتحقق من السلوك.
</details>

---

### تمرين 4 ⭐⭐⭐⭐⭐ — المشروع النهائي: نظام إدارة الطلاب الكامل 📚

لنبني **النسخة النهائية الكاملة** من دفتر الدرجات، تجمع كل ما تعلمناه:

1. صنف `Person` (أساس).
2. صنف `Student(Person)` مع `grades`, `get_average()`, `get_report()`.
3. صنف `ScholarshipStudent(Student)` مع `discount`, `get_report()` مختلف.
4. صنف `Gradebook` يدير الطلاب.
5. دالة `generate_report(students)` تستخدم التعددية الشكلية.

💡 تلميح 1: استخدم الوراثة والتعددية معًا.

💡 تلميح 2: `Gradebook` لا يحتاج لمعرفة نوع كل طالب.

<details>
<summary>الحل المفصّل</summary>

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

class Student(Person):
    def __init__(self, name, age):
        super().__init__(name, age)
        self.grades = []

    def add_grade(self, grade):
        self.grades.append(grade)

    def get_average(self):
        if not self.grades:
            return 0
        return round(sum(self.grades) / len(self.grades), 1)

    def get_report(self):
        status = "Pass" if self.get_average() >= 60 else "Fail"
        return self.name + " | Avg: " + str(self.get_average()) + " | " + status

class ScholarshipStudent(Student):
    def __init__(self, name, age, discount):
        super().__init__(name, age)
        self.discount = discount

    def get_report(self):
        return self.name + " | Avg: " + str(self.get_average()) + " | Scholarship (" + str(self.discount) + "% off)"

class Gradebook:
    def __init__(self):
        self.students = []

    def add_student(self, student):
        self.students.append(student)

    def generate_report(self):
        print("=" * 40)
        print("FINAL GRADEBOOK REPORT")
        print("=" * 40)
        for s in self.students:
            print(s.get_report())
        print("=" * 40)

# Build the system
gb = Gradebook()

ahmad = Student("Ahmad", 14)
ahmad.add_grade(80)
ahmad.add_grade(85)

salma = ScholarshipStudent("Salma", 15, 20)
salma.add_grade(95)
salma.add_grade(92)

omar = Student("Omar", 14)
omar.add_grade(50)
omar.add_grade(55)

gb.add_student(ahmad)
gb.add_student(salma)
gb.add_student(omar)
gb.generate_report()
```

المخرجات:
```text
========================================
FINAL GRADEBOOK REPORT
========================================
Ahmad | Avg: 82.5 | Pass
Salma | Avg: 93.5 | Scholarship (20% off)
Omar | Avg: 52.5 | Fail
========================================
```

تهانينا! 🎉🎉🎉 لقد أكملت المشروع التراكمي من الصفر إلى نظام كائني متكامل. من `print("Hello")` في الفصل الأول إلى نظام إدارة طلاب كامل بالوراثة والتعددية الشكلية.
</details>

---

## مختبر الأخطاء 🧪

### 🧪 خطأ 1 — استدعاء تابع غير موجود

```python
class Dog:
    def bark(self):
        return "Woof!"

class Cat:
    def meow(self):
        return "Meow!"

def make_sound(animal):
    print(animal.speak())  # 'speak' doesn't exist!

make_sound(Dog())
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
AttributeError: 'Dog' object has no attribute 'speak'
```

السبب: التعددية الشكلية تتطلب أن يكون التابع موجودًا في كل الأصناف التي ستُمرر. هنا `Dog` لديه `bark` وليس `speak`.

الإصلاح: تأكد أن كل الأصناف لديها نفس اسم التابع، أو استخدم صنف أساس مشترك.
</details>

---

### 🧪 خطأ 2 — تجاوز خاطئ للتابع

```python
class Student:
    def get_status(self):
        return "Active"

class Graduate(Student):
    def get_status(self):
        # Forgot to return!
        print("Graduated")

g = Graduate()
result = g.get_status()
print(result)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
Graduated
None
```

السبب: التابع المطبوع يُرجع `None` افتراضيًا لأننا استخدمنا `print` بدل `return`.

الإصلاح: استخدم `return` بدل `print` إذا كنت تريد إرجاع قيمة.
</details>

---

## تحدي المتعة 🎮 — نظام الأشكال الهندسية

أنشئ صنف أساس `Shape` بتابع `area()` يُرجع 0. ثم أنشئ `Circle`, `Rectangle`, `Triangle`. اكتب دالة `total_area(shapes)` تجمع مساحات قائمة أشكال مختلفة.

<details>
<summary>الحل</summary>

```python
class Shape:
    def area(self):
        return 0

class Circle(Shape):
    def __init__(self, r):
        self.r = r
    def area(self):
        return 3.14 * self.r ** 2

class Rectangle(Shape):
    def __init__(self, w, h):
        self.w = w
        self.h = h
    def area(self):
        return self.w * self.h

class Triangle(Shape):
    def __init__(self, b, h):
        self.b = b
        self.h = h
    def area(self):
        return 0.5 * self.b * self.h

def total_area(shapes):
    return sum(s.area() for s in shapes)

shapes = [Circle(5), Rectangle(4, 6), Triangle(3, 8)]
print("Total area:", total_area(shapes))
```
</details>

---

## أخطاء شائعة عند المبتدئين

1. **التحقق من النوع بدل الاعتماد على السلوك**: لا تستخدم `isinstance()` كثيرًا. اعتمد على أن الكائن لديه التابع المطلوب.
2. **نسيان أن كل الأصناف تحتاج نفس اسم التابع**: التعددية تتطلب واجهة موحدة.
3. **الخلط بين التجاوز والإخفاء**: التجاوز يستبدل التابع، والإخفاء يضيف تابعًا جديدًا بنفس الاسم.
4. **الوراثة المفرطة**: لا ترث لمجرد إعادة استخدام كود. استخدم الاحتواء (Composition) أحيانًا.

## قائمة تحقق ✅

- [ ] فهم مفهوم التعددية الشكلية.
- [ ] كتابة دوال تعمل مع أصناف مختلفة.
- [ ] استخدام التبط (Duck Typing).
- [ ] بناء نظام كائني كامل مع وراثة وتعددية.

