<img width="1251" height="728" alt="image" src="https://github.com/user-attachments/assets/bbbf13ca-877c-4094-aab2-6ff1955cae81" />



<img width="1249" height="707" alt="image" src="https://github.com/user-attachments/assets/bd2cde2a-65ee-466a-8155-bcd0093cd1a6" />

````markdown
# 📚 Book List – תרגול JavaScript OOP

פרויקט קטן ב־JavaScript שמדגים איך לבנות **אפליקציית רשימת ספרים** בגישה מונחית־עצמים (OOP).  
הפרויקט הוא חלק ממסלול הלימוד בקורס JavaScript שאני מלמד, ומתמקד במיוחד בהבנה מעשית של OOP בדפדפן.

---

## 🔍 מה האפליקציה עושה?

- טופס להוספת ספר: כותרת, מחבר, מספר סידורי (ISBN).
- הצגת כל הספרים בטבלה.
- מחיקה של ספר מהרשימה.
- שמירה אוטומטית של הספרים ב־`localStorage` כך שהרשימה נשמרת גם אחרי ריענון הדף (בגרסת ה־ES6).

---

## 🧠 איפה נכנס ה־OOP?

הפרויקט בנוי סביב **מחלקות (Classes)** ותפיסה של **הפרדת אחריויות**:

### 1. `Book` – מודל הספר (Model)
```js
class Book {
  constructor(title, author, isbn) {
    this.title = title;
    this.author = author;
    this.isbn = isbn;
  }
}
````

* מייצגת **אובייקט ספר אחד**.
* כל ספר חדש שנוצר בטופס הופך לאובייקט מסוג `Book`.
* זהו מודל קלאסי של OOP: כל ספר הוא מופע (instance) של מחלקה.

---

### 2. `UI` – ניהול הממשק (View / Controller)

```js
class UI {
  addBookToList(book) { ... }
  showAlert(message, className) { ... }
  deleteBook(target) { ... }
  clearFields() { ... }
}
```

המחלקה הזאת אחראית על:

* הוספת ספר לטבלה ב־DOM.
* הצגת הודעות הצלחה/שגיאה למשתמש.
* מחיקת ספר מה־DOM.
* ניקוי השדות בטופס.

➡️ כך אנחנו **מפרידים** בין:

* הלוגיקה של הנתונים (`Book`, `Store`)
* לבין הלוגיקה של התצוגה (`UI`).

זוהי דוגמה טובה ל־**Encapsulation**: כל מחלקה מטפלת בתחום אחריות אחד ברור.

---

### 3. `Store` – עבודה עם LocalStorage (Data Layer)

```js
class Store {
  static getBooks() { ... }
  static displayBooks() { ... }
  static addBook(book) { ... }
  static removeBook(isbn) { ... }
}
```

* מחלקת עזר סטטית שמנהלת את הנתונים ב־`localStorage`.
* אין צורך ליצור מופע (`new Store()`), אלא פשוט לקרוא לפונקציות סטטיות:

  * `Store.getBooks()`
  * `Store.addBook(book)`
  * `Store.removeBook(isbn)`
  * `Store.displayBooks()`

כך התלמידים לומדים:

* מה זה **מתודות סטטיות (static methods)**.
* איך להפריד בין **שכבת הנתונים** לבין הממשק הגרפי.

---

## 🧱 שתי גישות: ES6 Classes לעומת ES5 Prototypes

בפרויקט קיימות **שתי גרסאות**:

1. **גרסת ES6 (מודרנית)** – עם `class`:

   * `class Book`
   * `class UI`
   * `class Store`
   * שימוש ב־`localStorage` לשמירת הספרים.

2. **גרסת ES5 (קלאסית)** – עם פונקציות בנאי ו־`prototype`:

   ```js
   function Book(title, author, isbn) { ... }
   UI.prototype.addBookToList = function(book) { ... }
   ```

   גרסה זו עוזרת להבין:

   * איך עבד OOP ב־JavaScript **לפני** שהוסיפו `class`.
   * מה ההבדל הסינטקטי והקונספטואלי בין `prototype` ל־`class`.

זה מאפשר בשיעור:

* להראות **התפתחות של השפה**.
* להסביר שהתיכון הוא אותו תיכון (Prototype-based), אבל הסינטקס נהיה נוח וברור יותר.

---

## 🧪 נושאים עיקריים שהתלמידים לומדים בפרויקט

* יצירת מחלקות עם `constructor`.
* יצירת אובייקטים מתוך מחלקות (`new Book(...)`).
* הפרדת אחריות:

  * מחלקה לנתונים
  * מחלקה לממשק
  * מחלקה לאחסון
* אירועי DOM:

  * `submit` לטופס
  * `click` למחיקת ספר
  * `DOMContentLoaded` לטעינת נתונים קיימים.
* עבודה עם `localStorage`:

  * `localStorage.setItem`
  * `localStorage.getItem`
  * שימוש ב־`JSON.stringify` ו־`JSON.parse`.

---

## 📂 מבנה הקבצים המוצע

```bash
.
├── index.html        # טופס + טבלה להצגת הספרים
├── appes6.js         # גרסת ES6 – מחלקות Book, UI, Store
└── app_es5.js        # גרסת ES5 – פונקציות בנאי ו-prototype (אופציונלי ללימוד)
```

> שים לב: בקובץ `index.html` הקוד נטען כרגע מתוך `appes6.js`.

---

## 🚀 איך מריצים את הפרויקט

1. הורדה / Clone של הריפו:

   ```bash
   git clone https://github.com/YOUR_USERNAME/REPO_NAME.git
   ```
2. פתיחת הקובץ `index.html` בדפדפן (Double-click או Drag & Drop).
3. הוסיפו ספרים דרך הטופס, מחקו ספרים, ורעננו את הדף כדי לראות שהנתונים נשמרים.

---

## 💡 רעיונות להרחבות לתלמידים

* הוספת שדה **שנת פרסום** או **קטגוריה**.
* תצוגת הודעת אישור לפני מחיקה (`confirm`).
* מיון ספרים לפי שם מחבר / כותרת.
* חיפוש בתוך רשימת הספרים.
* יצירת כפתור "נקה את כל הרשימה" (כולל מחיקת `localStorage`).

---

## 🎓 למי מיועד הפרויקט?

* לתלמידים בשיעורי JavaScript שרוצים להבין **OOP בצורה פרקטית**.
* כחלק מחוג תכנות / מסלול ניתוח נתונים / קורס ווב.
* למי שמכיר כבר DOM בסיסי ורוצה לעשות צעד קדימה לארגון קוד מקצועי יותר.

---

בהמשך אוסיף עוד פרויקטים דומים שמתמקדים ב־OOP, עבודה עם ה־DOM והכנה לפיתוח ווב מודרני.
מוזמנים להשאיר ⭐ ב־GitHub אם אהבתם 😊

```
```

