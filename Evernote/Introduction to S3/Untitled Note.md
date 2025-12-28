---
---
**Introduction to S3**

**Differences between block, file, and object storage**

* Block storage
	* implemented in storage arrays
	* stores data in an array of unrelated blocks
	* the host file system places the data on a disk
	* Amazon Elastic Block Store (EBS) provides this storage
		* provides consistent block storage
* File Storage
	* stores data in a hierarchy of files and folders
	* used in mainstream operating systems
	* Provided by Amazon Elastic File System (EFS)
		* provides simple, scalable file storate
		* can mount EFS on one's own servers and connect EFS to Amazon's private cloud
* Object Storage
	* flat storage system
	* stores data as objects
		* objects consist of data, metadata, and a unique identifier
	* provided by Amazon S3
		* stores and scales a large amount of data
		* can store from a variety of sources

**S3 overview**

* made to be simple
* durable
	* made for 99.999999999% durability
* highly available
* high performance
* scalable
* pay as you go
	* pay for what you use
	* no need to pre-provision a store of data
* integrates with other AWS products
* Storage classes
	* S3 Standard
	* S3 Intelligent Tiering
	* S3 Standard - Infrequent Access
	* S3 One Zone - Infrequent Access
	* S3 Glacier
	* S3 Glacier Deep Archive
* S3 data is stored in buckets and can be accessed via
	* Amazon S3 Console
	* AWS CLI
	* Amazon SDKs

**Use cases for S3**

* Backup Storage
	* many 3rd party vendors use S3
	* Amazon S3 CLI can automatically store files
* Media Hosting
* Application Assets
	* as apps need to read/write data, these apps can be configured to use S3
* Data Lake
	* can store structured/unstructured data
* Content Delivery

**Charges for S3**

* <https://aws.amazon.com/s3/pricing/>

* there are no upfront fees
* pay for what you use
* provides billing reports
* **Storage**
	* the rate depends on the object's size, how long they've been stored in S3 during the month, and the storage class
* **Requests**
	* You pay for requests (GET, PUT, COPY) made against buckets and objects
	* you also pay for requests associated with lifecycle actions
	* these rates depend on the storage class and type of request made
* **Mangement**
	* pay for storage management features enabled on your account's buckets
* **Data Transfer**
	* pay for all data transferred in/out from S3 **except:**
		* data transferred in from the internet
		* data transferred to an Amazon EC2 instance, when the instance is in the same region as the S3 bucket
		* data transferred to Amazon CloudFront
	* fees are also paid for data transferred using S3 Transfer Acceleration to replicated with cross-region replication
* **Storage classes**
	* **Standard**
		* pay for objects stored
		* no additional fees for objects stored on S3 Standard storage class
	* **Infrequent access**
		* pay for objects stored
		* pay for retrieving objects stored in S3 Standard-IA and S3 One Zone-IA
		* objects that are deleted, overwritten, or transitioned to a different storage class before 30 days
		* S3 Standard-IA and S3 One Zone-IA objects have a minimum billable size of 128k; anything smaller will be billed at that rate
	* **Intelligent-Tiering**
		* There are no additional retrieval fees for retrieving objects stored in S3 Intelligent-Tiering
			* you pay for:
				* objects stored
				* monthly monitoring and automation fee
				* objects that are deleted, overwritten, or transitioned to a different storage class before 30 days
				* have a minimum billable size of 128k; anything smaller will be billed at the Frequent Access tier rates
	* **Glacier**
		* ![[./_resources/Untitled_Note.resources/unknown_filename.png]]
	* **Deep Archive**
		* there is standard and bulk archiving
		* ![[./_resources/Untitled_Note.resources/unknown_filename.1.png]]

**Bills**

* you can view costs per region where your data is stored

Where to view  usage and billing information
