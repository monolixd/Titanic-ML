### สรุปผลการเรียนรู้จาก Jupyter Notebook (Titanic Dataset) 🚢

#### **1. โหลดและสำรวจข้อมูล**
- ใช้ **pandas** เพื่อโหลดข้อมูลจาก `train.csv`
- ใช้ `df.head()` เพื่อตรวจสอบตัวอย่างข้อมูล
- ใช้ `df.info()` เพื่อตรวจสอบประเภทข้อมูลแต่ละคอลัมน์

```python
import pandas as pd

df = pd.read_csv('dataset/train.csv')

df.head()
df.info()
```

#### **2. ตรวจสอบค่าที่หายไป (Missing Values)**
- ใช้ `.isnull().sum()` เพื่อนับจำนวนค่าที่หายไปในแต่ละคอลัมน์

```python
df.isnull().sum()
```

#### **3. วิเคราะห์การกระจายตัวของอายุผู้โดยสาร**
- ใช้ **Matplotlib และ Seaborn** วาดกราฟฮิสโตแกรมแสดงการกระจายตัวของอายุผู้โดยสาร

```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.figure(figsize=(10, 5))
sns.histplot(df['Age'].dropna(), bins=30, kde=False)

plt.title('Age Distribution of Titanic Passengers')
plt.xlabel('Age')
plt.ylabel('Count')

plt.show()
```

#### **4. วิเคราะห์อัตราการรอดชีวิต**
- ใช้ `.value_counts()` นับจำนวนผู้รอดชีวิตและไม่รอดชีวิต
- สร้างกราฟแท่งแสดงสัดส่วนการรอดชีวิต

```python
survivals_count = df['Survived'].value_counts()

plt.figure(figsize=(6, 4))
sns.barplot(x=survivals_count.index, y=survivals_count.values, palette="viridis")

plt.title('Survival Count of Titanic Passengers')
plt.xticks([0, 1], ['Not Survived', 'Survived'])
plt.xlabel("Survival Status")
plt.ylabel("Count")

plt.show()
```

#### **5. วิเคราะห์อัตราการรอดชีวิตแยกตามเพศ**
- สร้างกราฟเปรียบเทียบอัตราการรอดชีวิตระหว่างเพศชายและเพศหญิง

```python
plt.figure(figsize=(6, 4))
sns.barplot(x='Sex', y='Survived', data=df, palette="Set2")

plt.title('Survival Rate by Gender')
plt.xlabel("Gender")
plt.ylabel("Survival Rate")

plt.show()
```

---

💡 **หมายเหตุ:** ไฟล์นี้ใช้ **Python, Pandas, Matplotlib และ Seaborn** สำหรับการวิเคราะห์ข้อมูลจาก Titanic Dataset
