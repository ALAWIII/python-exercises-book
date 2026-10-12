# مفهوم الوراثة في البرمجة

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. إنشاء صنف فرعي (Child Class) يرث من صنف أساس (Parent Class).
2. إعادة تعريف (Overriding) توابع الصنف الأساس في الصنف الفرعي.
3. استخدام `super()` لاستدعاء توابع الصنف الأساس من الصنف الفرعي.
4. إضافة توابع ومتغيرات جديدة في الصنف الفرعي.
5. فهم مفهوم الوراثة المتعددة (Multiple Inheritance).

📖 يقابل هذا الفصل: **الفصل 19 «مفهوم الوراثة في البرمجة»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- الصنف قالب لإنشاء كائنات.
- `__init__` هو الباني الذي يُهيّئ الكائن.
- `self` تشير إلى الكائن الحالي.
- التوابع تُعرَّف داخل الصنف وتعمل على كائناته.
- كل كائن يمتلك متغيرات خاصة به.

## إحماء 🔥

### إحماء 1

```python
class Animal:
    def speak(self):
        return "..."

class Dog(Animal):
    pass

d = Dog()
print(d.speak())
```

<details>
<summary>الحل</summary>

```text
...
```

`Dog` يرث من `Animal`، فيحصل على كل توابعه. `pass` تعني أننا لم نضف شيئًا جديدًا.
</details>

### إحماء 2

```python
class Animal:
    def speak(self):
        return "..."

class Dog(Animal):
    def speak(self):
        return "Woof!"

d = Dog()
print(d.speak())
```

<details>
<summary>الحل</summary>

```text
Woof!
```

`Dog` أعاد تعريف `speak()` (Overriding)، فتابعه الخاص يحل محل تابع الصنف الأساس.
</details>

### إحماء 3

```python
class Animal:
    def __init__(self, name):
        self.name = name

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)
        self.breed = breed

d = Dog("Rex", "Labrador")
print(d.name, d.breed)
```

<details>
<summary>الحل</summary>

```text
Rex Labrador
```

`super().__init__(name)` يستدعي باني الصنف الأساس لتهيئة `name`، ثم يضيف الصنف الفرعي `breed`.
</details>

---

## التمارين

### تمرين 1 ⭐ — وراثة بسيطة

لديك صنف أساس `Person` بباني يأخذ `name`. أنشئ صنفًا فرعيًا `Student` يرث منه بدون إضافة شيء. أنشئ كائنًا واطبع الاسم.

💡 تلميح 1: الصيغة `class Student(Person):`.

💡 تلميح 2: لا تحتاج كتابة `__init__` في الصنف الفرعي.

<details>
<summary>الحل المفصّل</summary>

```python
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):
    pass

s = Student("Ahmad")
print(s.name)  # Ahmad
```

الصنف الفرعي يرث كل شيء من الصنف الأساس تلقائيًا.
</details>

---

### تمرين 2 ⭐⭐ — إضافة متغيرات في الصنف الفرعي

أضف للصنف `Student` متغير `grade` (الدرجة) في بانيه الخاص، مع استخدام `super()` لاستدعاء باني `Person`.

المخرجات المتوقعة:

```text
Ahmad | Grade: 85
```

💡 تلميح 1: اكتب `__init__` في الصنف الفرعي.

💡 تلميح 2: استدعِ `super().__init__(name)` أولًا.

<details>
<summary>الحل المفصّل</summary>

```python
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):
    def __init__(self, name, grade):
        super().__init__(name)
        self.grade = grade

s = Student("Ahmad", 85)
print(s.name, "| Grade:", s.grade)
```

لماذا `super()`؟ لأنه يضمن أن باني الصنف الأساس يعمل أولًا (يهيئ `name`)، ثم نضيف نحن المتغيرات الجديدة.
</details>

---

### تمرين 3 ⭐⭐⭐ — إعادة تعريف تابع

لديك صنف `Student` بتابع `get_status()`. أنشئ صنفًا فرعيًا `ScholarshipStudent` يعيد تعريف `get_status()` بحيث يشترط درجة >= 90 للمنحة.

المخرجات المتوقعة:

```text
Ahmad: Pass
Salma: Scholarship
```

💡 تلميح 1: عرّف `get_status()` في الصنف الفرعي بنفس الاسم.

💡 تلميح 2: الصنف الفرعي يتحقق من شرط إضافي.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name, grade):
        self.name = name
        self.grade = grade

    def get_status(self):
        return "Pass" if self.grade >= 60 else "Fail"

class ScholarshipStudent(Student):
    def get_status(self):
        if self.grade >= 90:
            return "Scholarship"
        elif self.grade >= 60:
            return "Pass"
        return "Fail"

s1 = Student("Ahmad", 75)
s2 = ScholarshipStudent("Salma", 95)

print(s1.name + ":", s1.get_status())
print(s2.name + ":", s2.get_status())
```
</details>

---

### تمرين 4 ⭐⭐⭐⭐ — دفتر الدرجات مع الوراثة 📚

وسّع دفتر الدرجات: أنشئ صنف `ScholarshipStudent` يرث من `Student` ويضيف:
- متغير `discount` (نسبة الخصم).
- تابع `get_final_grade()` يضيف 5 درجات مكافأة.

المخرجات المتوقعة:

```text
Salma: Final=97.0 (Scholarship)
Ahmad: Final=85.0 (Pass)
```

💡 تلميح 1: `get_final_grade()` يضيف 5 إلى المعدل.

💡 تلميح 2: أعد تعريف `__str__` ليعرض معلومات إضافية.

<details>
<summary>الحل المفصّل</summary>

```python
class Student:
    def __init__(self, name, grades):
        self.name = name
        self.grades = grades

    def get_average(self):
        return round(sum(self.grades) / len(self.grades), 1)

    def get_status(self):
        return "Pass" if self.get_average() >= 60 else "Fail"

class ScholarshipStudent(Student):
    def __init__(self, name, grades, discount):
        super().__init__(name, grades)
        self.discount = discount

    def get_final_grade(self):
        return round(self.get_average() + 5, 1)

    def get_status(self):
        if self.get_final_grade() >= 90:
            return "Scholarship"
        return super().get_status()

ahmad = Student("Ahmad", [80, 85, 90])
salma = ScholarshipStudent("Salma", [90, 92, 95], discount=20)

print(salma.name + ": Final=" + str(salma.get_final_grade()) + " (" + salma.get_status() + ")")
print(ahmad.name + ": Final=" + str(ahmad.get_average()) + " (" + ahmad.get_status() + ")")
```
</details>

---

### تمرين 5 ⭐⭐⭐⭐⭐ — مشروع مصغّر: نظام الطلاب الكامل 📚

لنبني النسخة النهائية الكائنية من **دفتر الدرجات** مع الوراثة!

أنشئ ثلاثة أصناف:
1. `Person` (الأساس): `name`, `age`, `__str__()`.
2. `Student(Person)`: يضيف `grades`, `get_average()`, `get_status()`.
3. `ScholarshipStudent(Student)`: يضيف `discount`, `get_final_grade()`.

ثم أنشئ `Gradebook` يدير قائمة من الطلاب ويطبع تقريرًا شاملًا.

💡 تلميح 1: كل صنف يستدعي `super().__init__()` أولًا.

💡 تلميح 2: `Gradebook` يتحقق من نوع الطالب بـ `isinstance()`.

<details>
<summary>الحل المفصّل</summary>

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return self.name + " (age " + str(self.age) + ")"


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

    def get_status(self):
        return "Pass" if self.get_average() >= 60 else "Fail"


class ScholarshipStudent(Student):
    def __init__(self, name, age, discount):
        super().__init__(name, age)
        self.discount = discount

    def get_final_grade(self):
        return round(self.get_average() + 5, 1)

    def get_status(self):
        if self.get_final_grade() >= 90:
            return "Scholarship"
        return super().get_status()


class Gradebook:
    def __init__(self):
        self.students = []

    def add_student(self, student):
        self.students.append(student)

    def print_report(self):
        print("=== Final Grade Book Report ===")
        for s in self.students:
            if isinstance(s, ScholarshipStudent):
                print(s.name + ": Final=" + str(s.get_final_grade()) + " (" + s.get_status() + ") [Discount: " + str(s.discount) + "%]")
            else:
                print(s.name + ": Average=" + str(s.get_average()) + " (" + s.get_status() + ")")
        print("================================")


gb = Gradebook()

ahmad = Student("Ahmad", 14)
ahmad.add_grade(80)
ahmad.add_grade(85)

salma = ScholarshipStudent("Salma", 15, 20)
salma.add_grade(90)
salma.add_grade(95)

gb.add_student(ahmad)
gb.add_student(salma)
gb.print_report()
```

هذا هو **دفتر الدرجات** الكامل! من متغيرات بسيطة في الفصل الأول إلى نظام كائني متكامل مع الوراثة. 🎉
</details>

---

## مختبر الأخطاء 🧪

### 🧪 خطأ 1 — نسيان استدعاء باني الصنف الأساس

```python
class Person:
    def __init__(self, name):
        self.name = name

class Student(Person):
    def __init__(self, name, grade):
        self.grade = grade  # Forgot super().__init__(name)!

s = Student("Ahmad", 85)
print(s.name)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
AttributeError: 'Student' object has no attribute 'name'
```

السبب: عندما تكتب `__init__` في الصنف الفرعي، لا يُستدعى باني الصنف الأساس تلقائيًا. يجب استدعاؤه يدويًا بـ `super().__init__()`.

الإصلاح:
```python
class Student(Person):
    def __init__(self, name, grade):
        super().__init__(name)  # Initialize parent
        self.grade = grade
```
</details>

---

### 🧪 خطأ 2 — الوراثة من صنف غير موجود

```python
class Student(Teacher):
    pass
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
NameError: name 'Teacher' is not defined
```

السبب: تحاول الوراثة من صنف لم يُعرَّف بعد.

الإصلاح: عرّف الصنف الأساس أولًا، أو تأكد من استيراده.
</details>

---

## تحدي المتعة 🎮 — وراثة متعددة

أنشئ صنفين `Flyer` (بتابع `fly()`) و `Swimmer` (بتابع `swim()`). ثم أنشئ صنفًا `Duck` يرث من كليهما. استدعِ التابعين على كائن `Duck`.

<details>
<summary>الحل</summary>

```python
class Flyer:
    def fly(self):
        return "I can fly!"

class Swimmer:
    def swim(self):
        return "I can swim!"

class Duck(Flyer, Swimmer):
    pass

d = Duck()
print(d.fly())
print(d.swim())
```
</details>

---

## أخطاء شائعة عند المبتدئين

1. **نسيان `super().__init__()`** في باني الصنف الفرعي.
2. **إعادة تعريف كل شيء**: إذا كان التابع يعمل كما تريد، لا تعيد تعريفه.
3. **الوراثة العميقة جدًا**: لا تجعل سلسلة الوراثة أطول من 3-4 مستويات.
4. **الخلط بين الوراثة والاحتواء**: أحيانًا يكون من الأفضل أن يحتوي الصنف على كائن من صنف آخر بدل أن يرث منه.

## قائمة تحقق ✅

- [ ] إنشاء صنف فرعي يرث من صنف أساس.
- [ ] استخدام `super()` لاستدعاء باني الصنف الأساس.
- [ ] إعادة تعريف توابع في الصنف الفرعي.
- [ ] إضافة متغيرات وتوابع جديدة في الصنف الفرعي.
- [ ] فهم الوراثة المتعددة.

**ماذا سيعتمد عليه الفصل القادم؟** فصل «التعددية الشكلية»: سنتعلم كيف نستطيع التعامل مع كائنات من أصناف مختلفة بنفس الطريقة، مما يجعل الكود أكثر مرونة.