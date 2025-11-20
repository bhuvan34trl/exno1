# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
            <<include your coding and its corressponding output screen shots here
    import pandas as pd
    data=pd.read_csv("Data_set.csv")
    df=pd.DataFrame(data)
    print(df)  
    
![1](https://github.com/user-attachments/assets/31b73eb9-a220-43bb-89d1-3aa5e3867a9d)

    df.info()
    
[2](https://github.com/user-attachments/assets/e880ad5f-272c-4bda-b4c9-578ed88d50bb)

    df.describe()
    
![15](https://github.com/user-attachments/assets/d6be4298-987c-462a-9aad-84b3f3611f8d)

    df.isna().sum()
    
![3](https://github.com/user-attachments/assets/6e15a867-09ce-466b-9c24-0a7c8010e4ff)

    df.dropna(axis=0,inplace=True)
    
![5](https://github.com/user-attachments/assets/03954226-f6a0-4404-8515-c60213200d72)

    df.to_csv('newdata1.csv', index-False)
    data1=pd.read_csv("newdata1.csv")
    df=pd.DataFrame(data1)
    df

![6](https://github.com/user-attachments/assets/12ccbb30-366a-41eb-9855-3e606bcd1cbd)

    df.["num_episodes")

![WhatsApp Image 2025-11-20 at 09 20 50_fb443505](https://github.com/user-attachments/assets/136239e4-7f01-4d4d-9836-d61a3862cda8)

    import seaborn as sns
    import numpy as np
    sns.boxplot(data=df["num_episodes"])
            
![WhatsApp Image 2025-11-20 at 09 25 05_179dd57f](https://github.com/user-attachments/assets/a52254ee-d072-4734-83a3-e7be0bca72f6)

    sns.scatterplot(data=df["num_episodes"])

![7](https://github.com/user-attachments/assets/163fa1bd-cff0-4506-8ba3-dd0542d600ad)

    q1=df["num_episodes"].quantile(0.25)
    q3=df["num_episodes"].quantile(0.75)
    IQR=q3-q1
    up_bound=q3+(1.5*IQR)
    low_bound=q1-(1.5*IQR)
    outliers=[x for x in df["num_episodes"] if x<low_bound or x>up_bound]
    print("q1:",q1)
    print("q3:",q3)
    print("IQR:",IQR)
    print("upper bound:",up_bound," and lower bound:",low_bound)
    print("Outliers:",outliers)    

![WhatsApp Image 2025-11-20 at 09 34 22_bad7723f](https://github.com/user-attachments/assets/667ab2ea-e435-4d39-8f45-ecafe7111874)

    mean=np.mean(df["num_episodes"])
    std=np.std(df["num_episodes"])
    threshold=3
     outliers=[]
    for i in df["num_episodes"]:
        z=(i-mean)/std
        if np.abs(z)>threshold:
            outliers.append(i)
    print("Mean:",mean)
    print("Standard deviation:",std)
   print("Outliers:",outliers)        
            
![16](https://github.com/user-attachments/assets/ec935f5f-2115-457d-ae10-fdba4e1bcd0e)
    index_to_delete = df[df["num_episodes"] ==50].index
    df.drop(index_to_delete, inplace=True)
    
 ![WhatsApp Image 2025-11-20 at 09 41 40_2fe91b4c](https://github.com/user-attachments/assets/39e962a4-5d21-4504-8f5f-569b5938310b)

    sns.scatterplot(data=df["num_episodes"])
    
![17](https://github.com/user-attachments/assets/10ed2296-6c69-483d-966c-d2826c80f7b4)
    sns.boxploat(data=df["num_episodes"])
![13](https://github.com/user-attachments/assets/e01fae05-050b-499f-8a9a-ccaa252f0383)


            
# Result
          Thus the program to read the given data and perform data cleaning and save the cleaned data to a file and removing outliers using IQR
 method and Z-score method is written and executed successfully
