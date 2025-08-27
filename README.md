# Exno:1
Data Cleaning Process

---

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

---

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

---

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

---

# Coding and Output

```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="801" height="654" alt="Screenshot 2025-08-27 171514" src="https://github.com/user-attachments/assets/360d73c8-f4df-47cb-8045-8389cbd2efe0" />

```
df.head()
```
<img width="792" height="202" alt="Screenshot 2025-08-27 172046" src="https://github.com/user-attachments/assets/cbb87944-84b8-4bda-9878-35d5692d0903" />

```
df.tail()
```
<img width="778" height="193" alt="Screenshot 2025-08-27 172056" src="https://github.com/user-attachments/assets/d22e5d71-6259-482c-929a-d2e67eea1bc4" />

```
df.info()
```
<img width="339" height="337" alt="Screenshot 2025-08-27 172902" src="https://github.com/user-attachments/assets/15dc76ba-f1c6-49d3-a7e1-24b226d0c88f" />

```
df.describe()
```
<img width="717" height="287" alt="Screenshot 2025-08-27 173200" src="https://github.com/user-attachments/assets/554f75e3-47cd-4108-b537-a31978461d4f" />

```
 df.isnull().sum()
```
<img width="257" height="341" alt="Screenshot 2025-08-27 175109" src="https://github.com/user-attachments/assets/c97ad964-990e-462c-b9ad-bf192b041934" />

```
df.isnull().any()
```
<img width="267" height="337" alt="Screenshot 2025-08-27 175254" src="https://github.com/user-attachments/assets/b08f1017-0022-44a5-be97-2c8715b157a8" />

```
df.notnull().sum()
```
<img width="195" height="337" alt="Screenshot 2025-08-27 175216" src="https://github.com/user-attachments/assets/60d4987d-baf6-4e86-92b4-2b99a43a0273" />

```
df.nunique()
```
<img width="185" height="261" alt="Screenshot 2025-08-27 175553" src="https://github.com/user-attachments/assets/203d7f50-7bf5-4604-a407-1e787b2286a3" />

```
df.dropna()
```
<img width="792" height="424" alt="Screenshot 2025-08-27 175712" src="https://github.com/user-attachments/assets/3c5ace58-4882-4374-a343-473d456aed84" />

```
df.dropna(axis=0)
```
<img width="793" height="427" alt="Screenshot 2025-08-27 175758" src="https://github.com/user-attachments/assets/5aef0f86-1868-481b-9b75-3721a83b4d35" />

```
df.dropna(axis=1)
```
<img width="289" height="629" alt="Screenshot 2025-08-27 175943" src="https://github.com/user-attachments/assets/041f1d49-ffe0-47bc-ba40-e66a90bc4d3a" />

```
df.fillna(10)
```
<img width="794" height="627" alt="Screenshot 2025-08-27 180038" src="https://github.com/user-attachments/assets/4b8dce2d-130c-476c-a3cb-a07e4b5f8855" />

```
df.fillna(method = 'ffill')
```
<img width="794" height="629" alt="Screenshot 2025-08-27 180508" src="https://github.com/user-attachments/assets/07fec6c3-5190-4c36-8c14-97b3ee8db551" />

```
df.fillna(method = 'bfill')
```
<img width="799" height="630" alt="Screenshot 2025-08-27 180800" src="https://github.com/user-attachments/assets/0026c188-3f80-4f19-b352-506c6522c30c" />

```
ir =pd.read_csv('iris.csv')
ir
```
<img width="668" height="507" alt="Screenshot 2025-08-27 180849" src="https://github.com/user-attachments/assets/4679cd60-c731-4b7f-9e84-b951aa4921f0" />

```
ir.describe()
```
<img width="584" height="363" alt="Screenshot 2025-08-27 180944" src="https://github.com/user-attachments/assets/a9cf4c44-6547-466c-8956-25791a7ab0bb" />

```
 import seaborn as sns
 sns.boxplot(x ='sepal_width', data=ir)
```
<img width="756" height="638" alt="Screenshot 2025-08-27 181118" src="https://github.com/user-attachments/assets/9b01fc2c-7d67-46c6-90cc-14b99e2d8f29" />

```
q1=ir.sepal_width.quantile(0.25)
 q3=ir.sepal_width.quantile(0.75)
 iq=q3-q1
 print(iq)
```
<img width="410" height="138" alt="Screenshot 2025-08-27 181218" src="https://github.com/user-attachments/assets/7f09a69a-7924-45ec-b5ef-c9a21707a829" />

```
rid=ir[((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
 rid['sepal_width']
```
<img width="741" height="184" alt="Screenshot 2025-08-27 181336" src="https://github.com/user-attachments/assets/0890e0bb-ece2-4e52-ab50-5d41067b2b98" />

```
delid=ir[~((ir.sepal_width<(q1-1.5*iq))|(ir.sepal_width>(q3+1.5*iq)))]
 delid
```
<img width="783" height="502" alt="Screenshot 2025-08-27 181431" src="https://github.com/user-attachments/assets/18c2c6cb-06b4-443e-a794-f562cd7e4061" />

```
 sns.boxplot(x ='sepal_width', data=delid)
```
<img width="791" height="627" alt="Screenshot 2025-08-27 181556" src="https://github.com/user-attachments/assets/6957b89e-b0c0-4ec1-a49c-882f059abe24" />

```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(ir['sepal_width']))
z
```
<img width="531" height="66" alt="Screenshot 2025-08-27 181724" src="https://github.com/user-attachments/assets/704c039a-a146-45cc-a92d-9cd7fb664ba9" />
<img width="553" height="334" alt="Screenshot 2025-08-27 181758" src="https://github.com/user-attachments/assets/cdd5d816-ab4b-4b76-b076-0049438fa222" />

```
ir1 = ir[z<3]
ir1
```
<img width="619" height="497" alt="Screenshot 2025-08-27 181947" src="https://github.com/user-attachments/assets/1e4bad40-6cdc-4f1e-96ed-5b40254a74b5" />

---

# Result
Thus, we have read the given data and performed data cleaning and saved the cleaned data to a file successfully.
