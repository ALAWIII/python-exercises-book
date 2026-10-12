# الوحدات (Modules)

## ماذا سنتقن؟

بنهاية هذا الفصل ستتمكن من:

1. استيراد الوحدات المدمجة مثل `math` و `random`.
2. استخدام صيغ الاستيراد المختلفة: `import` و `from ... import`.
3. إعطاء أسماء مستعارة للوحدات باستخدام `as`.
4. إنشاء وحدات مخصصة (ملفات `.py` خاصة بك) واستيرادها.
5. استخدام `if __name__ == "__main__":` للتحكم في تنفيذ الكود.

📖 يقابل هذا الفصل: **الفصل 17 «الوحدات: استيرادها وإنشاؤها»** من كتاب «البرمجة بلغة بايثون».

## مراجعة سريعة

- الدوال تُغلّف الكود القابل لإعادة الاستخدام.
- الملفات التي تنتهي بامتداد `.py` هي ملفات بايثون.
- عندما يصبح البرنامج كبيرًا، نحتاج لتقسيمه إلى عدة ملفات (وحدات) لتسهيل الصيانة والقراءة.

## إحماء 🔥

### إحماء 1

```python
import math
print(math.pi)
```

<details>
<summary>الحل</summary>

```text
3.141592653589793
```

`math` وحدة مدمجة توفر ثوابت ودوال رياضية. نصل إليها باستخدام النقطة `.`.
</details>

### إحماء 2

```python
from random import randint
print(randint(1, 10))
```

<details>
<summary>الحل</summary>

```text
(رقم عشوائي بين 1 و 10)
```

`from ... import` تستورد دالة محددة مباشرة، مما يتيح استخدامها بدون كتابة اسم الوحدة.
</details>

---

## التمارين

### تمرين 1 ⭐ — استيراد وحدة `math`

استورد وحدة `math` واستخدم الدالة `sqrt()` لحساب الجذر التربيعي للعدد 144 واطبعه.

💡 تلميح 1: الصيغة `math.sqrt(number)`.

💡 تلميح 2: لا تنسَ `import math` في البداية.

<details>
<summary>الحل المفصّل</summary>

```python
import math
result = math.sqrt(144)
print(result) # 12.0
```
</details>

---

### تمرين 2 ⭐⭐ — استيراد دوال محددة

من وحدة `random`، استورد الدالة `choice()` فقط. استخدمها لاختيار مادة عشوائية من قائمة المواد وطباعتها.

```python
subjects = ["Math", "Science", "History", "Art"]
```

💡 تلميح 1: الصيغة `from module import function`.

💡 تلميح 2: `choice(list)` تختار عنصرًا عشوائيًا من قائمة.

<details>
<summary>الحل المفصّل</summary>

```python
from random import choice

subjects = ["Math", "Science", "History", "Art"]
print(choice(subjects))
```
</details>

---

### تمرين 3 ⭐⭐⭐ — الأسماء المستعارة (Aliasing)

استورد وحدة `random` وأعطها الاسم المستعار `rnd`. استخدم `rnd.randint()` لتوليد درجة عشوائية بين 50 و 100.

💡 تلميح 1: الصيغة `import module as alias`.

💡 تلميح 2: هذا مفيد لتقليل الكتابة أو تجنب التعارض مع متغيرات تحمل نفس الاسم.

<details>
<summary>الحل المفصّل</summary>

```python
import random as rnd

random_grade = rnd.randint(50, 100)
print("Random Grade:", random_grade)
```
</details>

---

### تمرين 4 ⭐⭐⭐ — إنشاء وحدة مخصصة

تخيل أن لدينا ملفين في نفس المجلد:
1. `calculations.py` (يحتوي على دالة `get_status(grade)`).
2. `main.py` (البرنامج الرئيسي).

اكتب الكود اللازم في `main.py` لاستيراد الدالة `get_status` من ملف `calculations` واستخدامها.

💡 تلميح 1: بايثون يعتبر أي ملف `.py` وحدة.

💡 تلميح 2: لا تكتب امتداد `.py` عند الاستيراد، فقط اسم الملف.

<details>
<summary>الحل المفصّل</summary>

**في ملف `calculations.py`:**
```python
def get_status(grade):
    return "Pass" if grade >= 60 else "Fail"
```

**في ملف `main.py`:**
```python
from calculations import get_status

print(get_status(85)) # Pass
```
</details>

---

### تمرين 5 ⭐⭐⭐⭐ — حارس الوحدة `__name__ == "__main__"`

في ملف `calculations.py` السابق، أضف كودًا يطبع `"Testing calculations module..."` ويشغل الدالة، ولكن **فقط** إذا تم تشغيل الملف مباشرة، وليس عند استيراده في ملف آخر.

💡 تلميح 1: المتغير الخاص `__name__` يأخذ القيمة `"__main__"` فقط في الملف الذي يتم تشغيله مباشرة.

💡 تلميح 2: الصيغة: `if __name__ == "__main__":`.

<details>
<summary>الحل المفصّل</summary>

**في ملف `calculations.py`:**
```python
def get_status(grade):
    return "Pass" if grade >= 60 else "Fail"

# هذا الجزء لن يُنفذ عند الاستيراد من ملف آخر
if __name__ == "__main__":
    print("Testing calculations module...")
    print(get_status(70))
```
هذا النمط ضروري لكتابة وحدات يمكن اختبارها بشكل مستقل، ثم استيرادها بأمان في برامج أخرى دون أن تُشغّل أكواد الاختبار تلقائيًا.
</details>

---

### تمرين 6 ⭐⭐⭐⭐⭐ — مشروع مصغّر: تقسيم دفتر الدرجات 📚

لنبني النسخة النهائية من **دفتر الدرجات** 📚 كبرنامج متعدد الملفات!
1. أنشئ ملفًا باسم `grade_utils.py` وضع فيه دوال الحساب (`calculate_average`, `get_highest`).
2. أنشئ ملفًا باسم `app.py` يحتوي على بيانات الطلاب (قاموس) ويستورد الدوال من `grade_utils` لطباعة التقرير النهائي.

💡 تلميح 1: في `grade_utils.py`، اجعل الدوال تأخذ القاموس كمعامل.

💡 تلميح 2: في `app.py`، استخدم `import grade_utils`.

<details>
<summary>الحل المفصّل</summary>

**ملف `grade_utils.py`:**
```python
def calculate_average(gradebook):
    if not gradebook: return 0
    return round(sum(gradebook.values()) / len(gradebook), 1)

def get_highest(gradebook):
    if not gradebook: return None
    highest_grade = max(gradebook.values())
    for name, grade in gradebook.items():
        if grade == highest_grade:
            return name, grade
```

**ملف `app.py`:**
```python
import grade_utils

students = {
    "Ahmad": 85,
    "Salma": 92,
    "Omar": 55,
    "Noor": 78
}

print("--- Final Report ---")
for name, grade in students.items():
    print(f"{name}: {grade}")

avg = grade_utils.calculate_average(students)
top_name, top_grade = grade_utils.get_highest(students)

print(f"Average: {avg}")
print(f"Top Student: {top_name} ({top_grade})")
```

تهانينا! 🎉 لقد بنيت للتو برنامجًا حقيقيًا ببنية احترافية (Modular Architecture).
</details>

---

## مختبر الأخطاء 🧪

### 🧪 خطأ 1 — وحدة غير موجودة

```python
import maths
print(maths.pi)
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
ModuleNotFoundError: No module named 'maths'
```
السبب: خطأ إملائي في اسم الوحدة. الاسم الصحيح هو `math` بدون `s`.
الإصلاح: `import math`.
</details>

---

### 🧪 خطأ 2 — استيراد دالة غير موجودة

```python
from math import squareroot
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
ImportError: cannot import name 'squareroot' from 'math'
```
السبب: الدالة غير موجودة في الوحدة `math`. الاسم الصحيح هو `sqrt`.
الإصلاح: `from math import sqrt`.
</details>

---

### 🧪 خطأ 3 — نسيان اسم الوحدة عند الاستدعاء

```python
import random
print(randint(1, 10))
```

<details>
<summary>التحليل والإصلاح</summary>

المخرجات المتوقعة:
```text
NameError: name 'randint' is not defined
```
السبب: عندما نستخدم `import random`، يجب استدعاء الدوال عبر الوحدة `random.randint()`. 
الإصلاح: إما استخدام `random.randint(1, 10)`، أو تغيير الاستيراد إلى `from random import randint`.
</details>

---

## تحدي المتعة 🎮 — مولد كلمات المرور العشوائية

استخدم وحدة `random` ووحدة `string` لكتابة دالة تُولّد كلمة مرور عشوائية بطول 8 أحرف تحتوي على حروف وأرقام.

<details>
<summary>الحل</summary>

```python
import random
import string

def generate_password():
    chars = string.ascii_letters + string.digits
    password = ""
    for _ in range(8):
        password += random.choice(chars)
    return password

print(generate_password())
```
</details>

---

## أخطاء شائعة عند المبتدئين

1. **كتابة امتداد الملف عند الاستيراد**: `import my_module.py` خطأ. الصحيح `import my_module`.
2. **تسمية ملفك بنفس اسم وحدة مدمجة**: إذا سميت ملفك `math.py`، فسيحدث تعارض عند محاولة `import math`.
3. **نسيان أن الاستيراد يتم مرة واحدة فقط**: بايثون يخزن الوحدات المستوردة في الذاكرة. إذا عدّلت ملف الوحدة أثناء تشغيل البرنامج، لن يتم تحديثه إلا إذا أعدت تشغيل البرنامج.
4. **الخلط بين `import module` و `from module import *`**: الأخيرة تعتبر ممارسة سيئة لأنها تلوث النطاق الحالي بأسماء قد تتعارض مع متغيراتك.

## قائمة تحقق ✅

- [ ] استيراد الوحدات المدمجة (`math`, `random`).
- [ ] استخدام `from ... import ...`.
- [ ] استخدام `as` للأسماء المستعارة.
- [ ] إنشاء واستيراد وحدات مخصصة.
- [ ] استخدام `if __name__ == "__main__":`.

---

انتهت **الوحدة السادسة — الدوال والوحدات** ✅. 
لقد قطعنا شوطًا رائعًا! المشروع التراكمي (دفتر الدرجات) أصبح الآن برنامجًا هيكليًا متكاملًا.
