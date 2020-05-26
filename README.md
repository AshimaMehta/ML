



# In[1]:


from keras.datasets import mnist
(X_train, y_train), (X_test, y_test) = mnist.load_data()


# In[2]:


X_train = X_train.reshape(6000,24,24,1)
X_test = X_test.reshape(1000,24,24,1)


# In[3]:


from keras.utils import to_categorical
y_train = to_categorical(y_train)
y_test = to_categorical(y_test)


# In[4]:


import random
from keras.models import Sequential
from keras.optimizers import Adam ,RMSprop ,SGD ,Nadam 
from keras.layers import Dense, Conv2D, Flatten
from keras.layers import MaxPool2D


# In[5]:



model = Sequential()


# In[6]:


x = random.randint(1,5)
for i in range(x):
    model.add(Conv2D(filters=random.randint(2,10),kernel_size=random.choice(((2,2),(3,3),(4,4),(5,5),(6,6))), activation="relu", input_shape=(24,24,1)))

model.add(Flatten())

model.add(Dense(units=10,activation=random.choice(('relu','sigmoid','softmax'))))

model.compile(optimizer=random.choice(('RMSprop','Adam','SGD','Nadam')), loss='categorical_crossentropy', metrics=['accuracy'])


# In[ ]:





# In[ ]:





# In[7]:



model.fit(X_train, y_train,epochs=random.randint(1,4))


# In[8]:


pred1=model.evaluate(X_test,y_test)


# In[9]:


print("Accuracy is : ",pred1[1]*100)


# In[14]:


Accuracy = str(pred1[1]*100)
mod = str(model.layers)
print(mod)


#Sending Mail If Accuracy is > 95%
import smtplib
import os
if pred1[1]*100 >= 95:
    email = 'abc@gmail.com' # Your email
    password = '************' # Your email account password
    send_to_email = 'abc@gmail.com' # Who you are sending the message to
    message1 = str(Accuracy) # The message in the email
    message2 = mod
    server = smtplib.SMTP('smtp.gmail.com', 587) # Connect to the server
    server.starttls() # Use TLS
    server.login(email, password) # Login to the email server
    server.sendmail(email, send_to_email , message1) # Send the email
    server.sendmail(email, send_to_email , message2)
    server.quit() # Logout of the email server
else:
    os.system ('curl --user "admin:root" )


from keras.datasets import mnist
(X_train, y_train), (X_test, y_test) = mnist.load_data()

