# Prediction-Using-Naive-Bayes-Algorithm
Prediction using Social_Network_Ads



#Install Library
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import *

#load dataset
df = pd.read_csv('/content/Social_Network_Ads.csv')

#Displaying dataset
df.head()

#Diplay Dataset Info
df.info()

#Split data
#X adalah variabel indepenen - berisi AGE dan Estimated Salary
X = df.iloc[:, [2, 3]].values

#y adalah dependen - berisi fitur Purchased
y = df.iloc[:, -1].values

print('X : \n',X[:5])
print('\ny : \n',y[:5])

X_train, X_test, y_train, y_test = train_test_split(X, y,
                                                    test_size = 0.20,
                                                    random_state = 0)

print(X_train.shape)
print(y_train.shape)
print(X_test.shape)
print(y_test.shape)

#Create Clafier Model
classifier_model_binary = GaussianNB()
classifier_model_binary.fit(X_train, y_train)

#Predict test Data
y_pred = classifier_model_binary.predict(X_test)

y_pred

y_test

# Menggunakan model Gaussian Naive Bayes
classifier_model_binary = GaussianNB()

# Melatih model
classifier_model_binary.fit(X_train, y_train)

# Melakukan prediksi probabilitas
probabilities = classifier_model_binary.predict_proba(X_test)

# Menampilkan hasil prediksi probabilitas
print(probabilities)

#Evaluate
print(classification_report(y_test,y_pred,zero_division=0))

#Predict New Data
def predict_one(age, salary):
  print('Prediction : ', classifier_model_binary.predict([[age, salary]]))
  print('Probability : ', classifier_model_binary.predict_proba([[age, salary]]))

predict_one(39,100000)

#Multiclass Clasification
#Install Library
import numpy as np
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import *

#Load dataset
df_train = pd.read_excel("/content/data_train.xlsx")
df_test = pd.read_csv("/content/data_test.csv")

#Displaying Dataset
df_train.head(100)

df_train.info()

#Train Data
X_train = df_train.drop(["Jurusan"], axis=1).values
y_train = df_train["Jurusan"].values

X_test = df_test.drop(["Jurusan"], axis=1).values
y_test = df_test["Jurusan"].values

X_train

classifier_model_multiclass = GaussianNB()
classifier_model_multiclass.fit(X_train, y_train)

y_predict = classifier_model_multiclass.predict(X_test)
print("Prediksi Naive Bayes : ",y_predict)

classifier_model_multiclass.predict_proba(X_test)

print(classification_report(y_test,y_predict,zero_division=0))

def predict_one(mat,ingg,indo,presis,presek):
  print('Predicted Jurusan : ',classifier_model_multiclass.predict([[mat,ingg,indo,presis,presek]]))
  print('Probabiilty : ',classifier_model_multiclass.predict_proba([[mat,ingg,indo,presis,presek]]))


predict_one(92,82,85,1,1)
