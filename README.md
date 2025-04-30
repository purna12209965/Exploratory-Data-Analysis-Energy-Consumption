#!/usr/bin/env python
# coding: utf-8

# # Importing Libraries

# In[28]:


import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


# # Importing Dataset

# In[3]:


df = pd.read_csv('global-data-on-sustainable-energy (1).csv')


# # Exploring Dataset

# In[4]:


df.head()


# In[5]:


df.tail()


# In[7]:


df.shape


# In[8]:


df.describe()


# In[9]:


df.info()


# In[16]:


df.isnull().sum()


# In[11]:


df.duplicated().sum()


# # Datacleaning

# In[17]:


df_cleaned = df.dropna()


# In[20]:


df_cleaned.isnull().sum()


# In[24]:


df.duplicated()


# In[25]:


df.drop_duplicates()


# In[29]:


import matplotlib.pyplot as plt
import seaborn as sns

# Set the size of the plot
plt.figure(figsize=(10, 6))

# Use seaborn's boxplot to visualize outliers in a specific column
# Replace 'column_name' with the column you want to check for outliers
sns.boxplot(data=df, x='gdp_per_capita')

# Add a title and labels for clarity
plt.title('Boxplot for Detecting Outliers in GDP per Capita')
plt.xlabel('GDP per Capita')
plt.show()


# # Data Analysis

# #the trend of access to electricity over the years

# In[31]:


df_grouped = df.groupby('Year')['Access to electricity (% of population)'].mean()

plt.figure(figsize=(10, 6))
plt.plot(df_grouped, marker='o', color='b')
plt.title('Trend of Access to Electricity Over the Years')
plt.xlabel('Year')
plt.ylabel('Access to Electricity (% of population)')
plt.grid(True)
plt.show()


# the relationship between primary energy consumption per capita and CO2 emissions

# In[33]:


plt.figure(figsize=(8, 6))
sns.scatterplot(data=df, x='Primary energy consumption per capita (kWh/person)', y='Value_co2_emissions_kt_by_country')
plt.title('Energy Consumption per Capita vs CO2 Emissions')
plt.xlabel('Energy Consumption per Capita (kWh/person)')
plt.ylabel('CO2 Emissions (kt)')
plt.grid(True)
plt.show()


# access to electricity relate to GDP growth

# In[34]:


plt.figure(figsize=(8, 6))
sns.scatterplot(data=df, x='Access to electricity (% of population)', y='gdp_growth')
plt.title('Access to Electricity vs GDP Growth')
plt.xlabel('Access to Electricity (% of population)')
plt.ylabel('GDP Growth (%)')
plt.grid(True)
plt.show()


# In[ ]:
