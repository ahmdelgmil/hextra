---
title: دليل كامل لجافاسكريبت
date: 2025-01-19
authors:
  - name: imfing
    link: https://github.com/imfing
    image: https://github.com/imfing.png
  - name: Octocat
    link: https://github.com/octocat
    image: https://github.com/octocat.png
tags:
  - JavaScript
  - دليل
  - أمثلة
excludeSearch: false
---

# دليل كامل لجافاسكريبت 🖥️

جافاسكريبت واحدة من أشهر لغات البرمجة اللي بتُستخدم بشكل أساسي في تطوير الويب. 🌐 الدليل ده هيشرح كل أجزاء اللغة بمعلومات وأمثلة تفصيلية.

## فهرس المحتوى 📚
1. [المتغيرات](#المتغيرات)
2. [أنواع البيانات](#أنواع-البيانات)
3. [العوامل](#العوامل)
4. [هياكل التحكم](#هياكل-التحكم)
5. [الدوال](#الدوال)
6. [الكائنات](#الكائنات)
7. [المصفوفات](#المصفوفات)
8. [الكلاسات](#الكلاسات)
9. [الوعود و Async/Await](#الوعود-و-asyncawait)
10. [الوحدات](#الوحدات)

## المتغيرات 🛠️
المتغيرات بتُستخدم لتخزين البيانات عشان تستخدمها بعدين. في جافاسكريبت تقدر تعرّف المتغيرات باستخدام `var`, `let`, أو `const`. وكل واحدة ليها قواعد مختلفة:

- `var`: متغير عام ممكن تعرّفه أكتر من مرة.
- `let`: متغير محلي ما ينفعش تعرّفه بنفس الاسم في نفس المجال.
- `const`: متغير محلي ثابت (ما ينفعش تغير قيمته).

```javascript
let name = "أحمد"; // متغير محلي
const age = 25;    // متغير ثابت
var city = "القاهرة"; // متغير عام
```

### أهم النقاط ✨
- استخدم `let` و `const` في الكود الحديث.
- اعتمد على `const` لو القيمة مش هتتغير.

## أنواع البيانات 📊
جافاسكريبت بتدعم نوعين من البيانات:

### الأنواع الأولية (Primitive)
- **Number**: للأرقام الصحيحة أو العشرية.
- **String**: للنصوص.
- **Boolean**: `true` أو `false`.
- **Null**: بيعبر عن قيمة غير موجودة.
- **Undefined**: متغير متعرف بس مش مخصص له قيمة.
- **Symbol**: بيعبر عن قيمة فريدة.
- **BigInt**: للأرقام الكبيرة جدًا.

### الأنواع غير الأولية
- **Object**: مجموعة من أزواج المفتاح والقيمة.

```javascript
let num = 42; // رقم
let str = "مرحبًا بالعالم"; // نص
let isAlive = true; // قيمة منطقية
let obj = { key: "value" }; // كائن
```

## العوامل 🔢
جافاسكريبت بتوفر مجموعة من العوامل عشان تنفذ العمليات الحسابية والمقارنات.

### عوامل حسابية
- `+` للجمع
- `-` للطرح
- `*` للضرب
- `/` للقسمة
- `%` باقي القسمة

### عوامل مقارنة
- `===` مساواة صارمة
- `!==` عدم مساواة صارمة
- `>` أكبر من
- `<` أصغر من

### عوامل منطقية
- `&&` و منطقي
- `||` أو منطقي
- `!` نفي منطقي

```javascript
let sum = 5 + 3; // جمع
let isEqual = (10 === 10); // مقارنة
let isValid = true && false; // و منطقي
```

## هياكل التحكم 🔄
هياكل التحكم بتحدد تدفق الكود في البرنامج.

### الجمل الشرطية 🛤️
استخدم `if`, `else if`, و `else` لتنفيذ الكود بناءً على شرط معين:

```javascript
if (age > 18) {
    console.log("بالغ");
} else {
    console.log("قاصر");
}
```

### الحلقات 🔁
الحلقات بتكرر جزء من الكود كذا مرة.

#### حلقة `for`
```javascript
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```

#### حلقة `while`
```javascript
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```

## الدوال 🧩
الدوال عبارة عن كود ممكن تعيد استخدامه لتنفيذ مهام محددة.

### التعريف
```javascript
function greet(name) {
    return `مرحبًا, ${name}!`;
}

console.log(greet("فاطمة"));
```

### الدوال السهمية
طريقة مختصرة لكتابة الدوال:
```javascript
const add = (a, b) => a + b;
console.log(add(2, 3));
```

## الكائنات 🗂️
الكائنات بتخزن البيانات على شكل أزواج مفتاح وقيمة، وممكن تشمل دوال.

```javascript
let person = {
    name: "أحمد",
    age: 30,
    greet: function () {
        console.log(`مرحبًا، أنا ${this.name}`);
    }
};

person.greet();
```

### إضافة خصائص
```javascript
person.job = "مطور";
console.log(person);
```

## المصفوفات 📋
المصفوفات هي قوائم مرتبة من القيم. ممكن تخزن أي نوع بيانات.

### مثال
```javascript
let numbers = [1, 2, 3, 4];
numbers.push(5); // إضافة عنصر
console.log(numbers);
```

### دوال شائعة
- `push()`: إضافة عنصر للنهاية.
- `pop()`: إزالة آخر عنصر.
- `shift()`: إزالة أول عنصر.
- `unshift()`: إضافة عنصر للبداية.

## الكلاسات 🏛️
الكلاسات هي قوالب لإنشاء كائنات بخصائص وسلوك مشترك.

### مثال
```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} بيعمل صوت.`);
    }
}

let dog = new Animal("كلب");
dog.speak();
```

## الوعود و Async/Await ⏳
البرمجة غير المتزامنة بتسمح لك بتنفيذ مهام زي طلبات API من غير ما توقف البرنامج.

### الوعود
```javascript
let promise = new Promise((resolve, reject) => {
    let success = true;
    if (success) {
        resolve("تم بنجاح!");
    } else {
        reject("فشل!");
    }
});

promise.then(console.log).catch(console.error);
```

### Async/Await
```javascript
async function fetchData() {
    let response = await fetch("https://api.example.com/data");
    let data = await response.json();
    console.log(data);
}

fetchData();
```

## الوحدات 📦
الوحدات بتسمح بتقسيم الكود على ملفات منفصلة للتنظيم.

### التصدير
```javascript
export function add(a, b) {
    return a + b;
}
```

### الاستيراد
```javascript
import { add } from './math.js';
console.log(add(2, 3));
```

الدليل ده بيغطي الأساسيات المهمة في جافاسكريبت، وبيوفر أساس قوي للمطورين. برمجة سعيدة! 🎉
