# pythonT


📌 שליפת נתונים (SELECT)
משמש להצגת מידע מטבלה במסד הנתונים.
SELECT * FROM Customers;
👉 מציג את כל הנתונים מהטבלה Customers.
SELECT * FROM Orders WHERE customer_id=4;
👉 מציג את כל ההזמנות של הלקוח עם customer_id=4 מהטבלה Orders.
SELECT * FROM Shippings WHERE customer=1 OR customer=2;
👉 מציג את כל המשלוחים בטבלה Shippings עבור לקוחות עם customer=1 או customer=2.
📌 הוספת נתונים (INSERT INTO)
משמש להוספת רשומות חדשות לטבלה.
INSERT INTO Orders VALUES (10, 'Monitor', 100, 3);
👉 מוסיף הזמנה חדשה לטבלה Orders עם הפרטים:

order_id = 10
item = Monitor
amount = 100
customer_id = 3
INSERT INTO Shippings VALUES (6, 'Delivered', 3);
👉 מוסיף רשומה חדשה לטבלה Shippings עם הפרטים:

shipping_id = 6
status = Delivered
customer_id = 3
📌 מחיקת נתונים (DELETE)
משמש להסרת נתונים מטבלה.
DELETE FROM Orders WHERE customer_id=4;
👉 מוחק את כל ההזמנות בטבלה Orders השייכות ללקוח עם customer_id=4.
DELETE FROM Customers WHERE age < 30;
👉 מוחק מהטבלה Customers את כל הלקוחות שגילם קטן מ-30.
⚠ שימו לב: ללא תנאי WHERE, הפקודה תמחק את כל הנתונים בטבלה!

📌 עדכון נתונים (UPDATE)
משמש לעדכון רשומות קיימות בטבלה.
UPDATE Orders SET amount = 100;
👉 מעדכן את כל ההזמנות בטבלה Orders כך שהסכום (amount) יהיה 100.
UPDATE Customers SET first_name='Noam' WHERE first_name='Robert';
👉 משנה את שם הלקוחות בטבלה Customers מ-'Robert' ל-'Noam'.
🚀 סיכום קצר
🔹 SELECT – לשליפת נתונים
🔹 INSERT – להוספת נתונים
🔹 DELETE – למחיקת נתונים
🔹 UPDATE – לעדכון נתונים






import sqlite3

# יצירת חיבור למסד הנתונים (או יצירה אם לא קיים)
conn = sqlite3.connect("example.db")
cursor = conn.cursor()

# יצירת טבלה
cursor.execute("""
    CREATE TABLE IF NOT EXISTS Users (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        age INTEGER NOT NULL
    )
""")

# הכנסת נתונים
cursor.execute("INSERT INTO Users (name, age) VALUES (?, ?)", ("Alice", 25))
cursor.execute("INSERT INTO Users (name, age) VALUES (?, ?)", ("Bob", 30))
cursor.execute("INSERT INTO Users (name, age) VALUES (?, ?)", ("Charlie", 22))

# שמירת השינויים
conn.commit()

# שליפת נתונים
cursor.execute("SELECT * FROM Users")
rows = cursor.fetchall()

# הצגת הנתונים
for row in rows:
    print(row)

# סגירת החיבור למסד הנתונים
conn.close()
מה הקוד עושה?
יוצר (או פותח אם קיים) מסד נתונים בשם example.db.
מוודא שקיימת טבלה בשם Users עם עמודות id, name, age.
מכניס שלושה משתמשים עם שם וגיל.
שולף את כל הנתונים מהטבלה ומדפיס אותם.
סוגר את החיבור למסד הנתונים.
