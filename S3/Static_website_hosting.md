STATIC WEBSITE HOSTING IN S3
Step 1: Creating a Bucket
First, we have to launch our S3 instance. Follow these steps for creating a Bucket
•	https://ap-south-1.console.aws.amazon.com/s3/bucket/create?region=ap-south-1&bucketType=general

![image](https://github.com/user-attachments/assets/14380611-1179-4ae1-a9b8-a9c24273b3fd)
             
             
 
•	Choose Bucket Name – Bucket Name Should be Unique
•	 AWS Region –  Choose a region close to you or the region where you want to create the bucket (Example — Mumbai)
•	 Object Ownership – Enable for making Public, Otherwise disable
 
 ![image](https://github.com/user-attachments/assets/4fb71233-fd75-411f-a5d7-731e631a0daf)

Step 2: Block Public Access settings for the bucket
•	Uncheck (Block all public access) for the public, otherwise set default. If you uncheck (Block all public keys).

 ![image](https://github.com/user-attachments/assets/2fe9fe1b-0c67-497b-aabf-ca1501585b51)

•	Bucket Versioning:- You have to do Nothing (Disable)
•	Tags(0) : Optional
•	Default encryption: Disable    
Step 3: Now upload code files
•	Select Bucket and Click your Bucket Name

![image](https://github.com/user-attachments/assets/86529f6a-b8f0-48f0-aad0-21d1ca0ea654)
 
•	Now, click on upload (then click add File/folder) and select your HTML code file from your PC/Laptop.
•	I download a simple static website code from internet

![image](https://github.com/user-attachments/assets/3f520a3c-1a80-4277-9dc5-94163c9703a0)
 
•	Click on upload
•	The files is upload successfully into the bucket
	 
![image](https://github.com/user-attachments/assets/3e467265-c7ca-4573-9286-212287a6548b)

Step 4:- Make public Object

•	Now, Click on Objects.
•	Select your All Objects.
•	Now, Click on Actions.
•	Select Make Public Using ACL.
•	Now, Click on Make Public and Close.
 
![image](https://github.com/user-attachments/assets/ab020cd6-470a-4afe-9324-ef41539dd657)
                 
![image](https://github.com/user-attachments/assets/7cc0cdb2-ef33-485f-aa0b-71ccab36f970)

STEP 5:
•	Go to Properties of bucket and enable Static website hosting
•	Also in index document fill with index.html and in error error.html
          
![image](https://github.com/user-attachments/assets/1fd65095-1f93-4f18-a4ae-aaa9fd68900c)

![image](https://github.com/user-attachments/assets/fadf5a22-d703-415b-a0c1-e87ca176b1fe)
  

•	Click on save changes


STEP 6:

•	After static website hosting enable we will get url copy that url paste in browser

![image](https://github.com/user-attachments/assets/a56fbed8-0c83-42e3-8264-b4394df45f26)
 



![Uploading image.png…]()


 

•	“STATIC WEBSITE IS HOSTED IN AWS S3 SUCCESSFULLY”

