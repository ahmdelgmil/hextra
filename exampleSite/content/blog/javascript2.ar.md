---
title: دليل كامل لـ Async/Await في جافاسكريبت
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
  - Async/Await
  - Promises
  - أمثلة
excludeSearch: false
---

# دليل كامل لـ Async/Await في جافاسكريبت

في عالم البرمجة غير المتزامنة (Asynchronous Programming)، تُعتبر `async/await` من الأدوات القوية التي تُسهل التعامل مع العمليات غير المتزامنة في جافاسكريبت. في هذا المقال، سنستعرض كل ما تحتاج معرفته عن `async/await` مع العديد من الأمثلة التوضيحية.

## ما هي `async/await`؟

`async/await` هي syntactic sugar تُبنى على أساس الـ Promises، وتُسهل كتابة الكود غير المتزامن بطريقة تبدو وكأنها متزامنة (Synchronous). بمعنى آخر، تسمح لك بكتابة كود غير متزامن بطريقة سهلة القراءة والفهم.

### الكلمة المفتاحية `async`

تُستخدم الكلمة المفتاحية `async` قبل تعريف الدالة لتحويلها إلى دالة غير متزامنة (Asynchronous Function). الدالة التي تُعرف بـ `async` تعود دائمًا بـ `Promise`.

```javascript
async function fetchData() {
  return "Data fetched!";
}

fetchData().then(console.log); // Output: Data fetched!
```

في المثال أعلاه، الدالة `fetchData` تعود بـ `Promise` يحمل القيمة `"Data fetched!"`.

### الكلمة المفتاحية `await`

تُستخدم الكلمة المفتاحية `await` داخل الدوال المعرفة بـ `async` لانتظار انتهاء تنفيذ `Promise`. عند استخدام `await`، يتم إيقاف تنفيذ الدالة حتى يتم resolve أو reject الـ `Promise`.

```javascript
async function fetchData() {
  let data = await new Promise((resolve, reject) => {
    setTimeout(() => resolve("Data fetched!"), 2000);
  });
  console.log(data);
}

fetchData(); // بعد 2 ثانية: Output: Data fetched!
```

في المثال أعلاه، يتم انتظار 2 ثوانٍ حتى يتم resolve الـ `Promise`، ثم يتم طباعة `"Data fetched!"`.

## معالجة الأخطاء مع `async/await`

لحسن الحظ، يمكن استخدام `try/catch` للتعامل مع الأخطاء في `async/await`.

```javascript
async function fetchData() {
  try {
    let data = await new Promise((resolve, reject) => {
      setTimeout(() => reject("Error: Data could not be fetched!"), 2000);
    });
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}

fetchData(); // بعد 2 ثانية: Output: Error: Data could not be fetched!
```

في المثال أعلاه، يتم استخدام `try/catch` للتعامل مع الـ `reject` من الـ `Promise`.

## أمثلة عملية

### مثال 1: جلب بيانات من API

```javascript
async function fetchUserData() {
  try {
    let response = await fetch('https://jsonplaceholder.typicode.com/users/1');
    let user = await response.json();
    console.log(user);
  } catch (error) {
    console.error("Error fetching user data:", error);
  }
}

fetchUserData();
```

في هذا المثال، يتم جلب بيانات مستخدم من API باستخدام `fetch` و `async/await`.

### مثال 2: تنفيذ عدة طلبات بشكل متوازي

يمكن استخدام `Promise.all` لتنفيذ عدة طلبات بشكل متوازي.

```javascript
async function fetchMultipleUsers() {
  try {
    let [user1, user2] = await Promise.all([
      fetch('https://jsonplaceholder.typicode.com/users/1').then(res => res.json()),
      fetch('https://jsonplaceholder.typicode.com/users/2').then(res => res.json())
    ]);
    console.log(user1, user2);
  } catch (error) {
    console.error("Error fetching users:", error);
  }
}

fetchMultipleUsers();
```

في هذا المثال، يتم جلب بيانات مستخدمين بشكل متوازي باستخدام `Promise.all`.

### مثال 3: استخدام `async/await` مع `forEach`

لاحظ أن `forEach` لا يعمل بشكل جيد مع `async/await`. بدلاً من ذلك، يمكن استخدام `for...of`.

```javascript
async function fetchAllUsers() {
  let userIds = [1, 2, 3];
  for (let id of userIds) {
    let user = await fetch(`https://jsonplaceholder.typicode.com/users/${id}`).then(res => res.json());
    console.log(user);
  }
}

fetchAllUsers();
```

في هذا المثال، يتم جلب بيانات عدة مستخدمين باستخدام `for...of` بدلاً من `forEach`.

## الخلاصة

`async/await` هي أداة قوية تُسهل كتابة الكود غير المتزامن في جافاسكريبت. بفضل `async/await`، يمكنك كتابة كود غير متزامن بطريقة سهلة القراءة والفهم، مع إمكانية التعامل مع الأخطاء باستخدام `try/catch`. نأمل أن تكون هذه المقالة قد ساعدتك في فهم `async/await` بشكل أفضل.