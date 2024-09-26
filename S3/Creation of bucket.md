
CREATION OF S3 BUCKET

STEP 1:
            SEARCH FOR S3 IN AWS CONSOLE
![image](https://github.com/user-attachments/assets/587fc9fe-0c39-4e91-8b09-1017df627f36)

           

STEP 2:
              Create a bucket the bucket name should be Globally unique
                                    
![image](https://github.com/user-attachments/assets/42eee19c-ad1e-410f-8080-18aa69732f61)


        
STEP 3:
•	Click on upload to upload files from local system to s3 bucket 

![image](https://github.com/user-attachments/assets/4578f4fe-d153-42e2-b850-ad206ff921af)


•	Click on Add files
![image](https://github.com/user-attachments/assets/5f50dac9-ebd7-42e3-9949-25ddd9e8049c)
 
•	After selecting file from local system click on upload
 
![image](https://github.com/user-attachments/assets/6c2a27fd-c3d2-4692-aa5b-9b3a0faea9d8)



•	The file has been uploaded successfully into the bucket
![image](https://github.com/user-attachments/assets/375672d5-eef4-49e4-836c-3c3ccd37193a)
 
 
STEP 4: Access the file from the internet

•	By default AWS blocks the public access to the bucket
![image](https://github.com/user-attachments/assets/d40f8193-3412-4bd6-a420-6414cb72a550)

 
•	This is security in feature in s3 at bucket level
•	To acces the files which is bucket through internet.we need to unblock public access to the bucket 
•	To disable the public access Click on bucket > Click on permission > Edit block public  access >

![image](https://github.com/user-attachments/assets/0b64d01a-36c3-41ad-84f5-a2fc3b2831ac)
 
•	Untick the block public access and click on save changes           
           ![image](https://github.com/user-attachments/assets/a3d01d4d-3e90-4800-82f7-bf9ab4b9a9fc)

•	Block all public access is disable
 
![image](https://github.com/user-attachments/assets/d9eccee7-cc6d-4f79-b7db-601aa05d4f2f)

•	Click on the object in bucket (here object is nothing but file which we upload in bucket)
 ![image](https://github.com/user-attachments/assets/6dd32ce5-e6cc-4078-8e8e-53decb5433ae)
 
•	Copy the object url and paste in browser
![image](https://github.com/user-attachments/assets/f8025f09-3855-4dfd-af5c-cf23bdfc856d)


•	We get output as above.although we gave public access to bucket.This happens because not only bucket . we need to make object in bucket as public.
•	First we need to enable ACL (access control list) by default it is disabled
 
![image](https://github.com/user-attachments/assets/fc0cd3cb-935f-4de5-9892-905d72172045)
 
•	Click on object > go to actions > make public using ACL.
•	Now we access the file in bucket through internet

![Uploading image.png…]()
 
•	“WE SUCCESSFULLY ACCESS THE FILE IN BUCKET THROUGH INTERNET”
 
                                       










