Versioning in AWS:

▪	Versioning is a means of keeping the multiple forms of an object in the same S3 bucket. Versioning can be used to retrieve, preserve and restore every version of an object in S3 bucket.
▪	Versioning-enabled buckets allow you to recover the objects from the deletion or overwrite. 

It serves two purposes:

o	If you delete an object, instead of deleting the object permanently, it creates a delete marker which becomes a current version of an object.
o	If you overwrite an object, it creates a new version of the object and also restores the previous version of the object.

While Creating bucket enable bucket versioning 

 
![image](https://github.com/user-attachments/assets/b72dabd6-b09f-46d2-bd66-da672de8fb3f)


•	I uploaded the file index.html intot the bucket 

![image](https://github.com/user-attachments/assets/2a0781a0-26b0-4510-b805-ea0a2e705b41)
 
•	I upload the same file index.html again.by default s3 replace old file with new file when the file name is same.
•	I the old file is deleted and we can see that old file in versions
	
![image](https://github.com/user-attachments/assets/4a556544-831a-4b59-ad61-edff0cd91de6)
 

