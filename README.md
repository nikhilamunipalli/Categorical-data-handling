#categorical data handling
from sklearn.preprocessing import LabelEncoder,OneHotEncoder
labelencoder = LabelEncoder()

#list of categorical data columns
l=[1,3,4,5,6,7]
count = 0

for j in l :
     X[:,j] = labelencoder.fit_transform(X[:,j])

y = labelencoder.fit_transform(y) 
     
#dummy variable trap    
for i,j in enumerate(l) :
    onc = OneHotEncoder(categorical_features = [count + j - (2*i)])
    onc.fit(X)
    count = count+ int(onc.n_values_)
    X = onc.fit_transform(X).toarray()
    X= X[:,1:]
    
