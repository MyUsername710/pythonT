📌 יצירת טבלה (CREATE TABLE)
sql
Copy
Edit
CREATE TABLE Customers (
    customer_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    age INTEGER
);
יוצר טבלה בשם Customers עם עמודות customer_id, first_name, last_name, ו-age.

📌 הוספת נתונים (INSERT INTO)
sql
Copy
Edit
INSERT INTO Customers (customer_id, first_name, last_name, age) 
VALUES (1, 'Alice', 'Johnson', 28);

INSERT INTO Customers (customer_id, first_name, last_name, age) 
VALUES (2, 'Bob', 'Smith', 35);

INSERT INTO Customers (customer_id, first_name, last_name, age) 
VALUES (3, 'Charlie', 'Brown', 22);
מכניס שלושה לקוחות עם customer_id, first_name, last_name ו-age לטבלה Customers.

📌 שליפת נתונים (SELECT)
sql
Copy
Edit
SELECT * FROM Customers;
מציג את כל הנתונים מהטבלה Customers.

sql
Copy
Edit
SELECT * FROM Customers WHERE age > 30;
מציג את כל הלקוחות שהגיל שלהם גדול מ-30.

sql
Copy
Edit
SELECT first_name, last_name FROM Customers WHERE customer_id = 1;
מציג רק את השם הפרטי ושם המשפחה של הלקוח עם customer_id = 1.

📌 עדכון נתונים (UPDATE)
sql
Copy
Edit
UPDATE Customers SET age = 29 WHERE customer_id = 1;
מעדכן את הגיל של הלקוח עם customer_id = 1 ל-29.

sql
Copy
Edit
UPDATE Customers SET last_name = 'Miller' WHERE first_name = 'Bob';
משנה את שם המשפחה של כל הלקוחות בשם Bob ל-Miller.

📌 מחיקת נתונים (DELETE)
sql
Copy
Edit
DELETE FROM Customers WHERE customer_id = 3;
מוחק את הלקוח עם customer_id = 3 מהטבלה Customers.

sql
Copy
Edit
DELETE FROM Customers WHERE age < 25;
מוחק את כל הלקוחות שגילם קטן מ-25.

sql
Copy
Edit
DELETE FROM Customers;
⚠ מוחק את כל הנתונים מהטבלה!

📌 מחיקת טבלה (DROP TABLE)
sql
Copy
Edit
DROP TABLE Customers;
מוחק את כל הטבלה Customers לחלוטין ממסד הנתונים.

🔹 SELECT – לשליפת נתונים
🔹 INSERT – להוספת נתונים
🔹 UPDATE – לעדכון נתונים
🔹 DELETE – למחיקת נתונים
🔹 DROP TABLE – למחיקת טבלה

🚀 ככה משתמשים ב-SQL כדי לנהל מסד נתונים בצורה בסיסית!


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
