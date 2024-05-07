# EX.NO:8 Implementation-of-K-Means-Clustering-for-Customer-Segmentation
# DATE:
## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Start the program
2. Import the necessary python libraries
3. Read the dataset of Mall_Customers csv file
4. From sklearn libraary select the cluster and import KMeans Clustering
5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method
6. Plot the graph x and y as Number of Clusters and wcss respectively
7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)
8. Stop the program

## Program:
```
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Paul Samson.S
RegisterNumber:  212222230104
```
```
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("/content/Mall_Customers.csv")

data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i,init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
data["cluster"] = y_pred

df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]

plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="olive",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="orange",label="cluster4")
```

## Output:

## Data Head:
![Screenshot 2024-04-17 085623](https://github.com/haritha-venkat/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/121285701/7f562d82-6439-40f7-9e80-fefd3522302b)

## Checking For Null Data:
![Screenshot 2024-04-17 085751](https://github.com/haritha-venkat/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/121285701/768c509e-c4ff-4616-be74-fd1ad2c02f6c)

## Data Information:
![Screenshot 2024-04-17 085719](https://github.com/haritha-venkat/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/121285701/48b33d47-c8d3-4447-80a1-0e1c9e1926c1)

## Elbow Method Graph:
![Screenshot 2024-04-17 085816](https://github.com/haritha-venkat/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/121285701/0b80ecd8-7f12-4f83-9621-6f8cd524b763)

## K-means Cluster:
![image](https://github.com/haritha-venkat/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/121285701/f27249cb-ddca-45ed-b255-76893082acce)

## Customer Segments Graph:
![Screenshot 2024-04-17 085908](https://github.com/haritha-venkat/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/121285701/c207d316-90c4-4700-b9a3-64cd5c136eb8)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
