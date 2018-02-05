S3
==

General
--

- What is Amazon S3?

  Amazon S3 is storage for the Internet. It’s a simple storage service that offers software developers a highly-scalable, reliable, and low-latency data storage infrastructure at very low costs.

- How much data can I store?

  The total volume of data and number of objects you can store are unlimited. Individual Amazon S3 objects can range in size from a minimum of 0 bytes to a maximum of 5 terabytes. The largest object that can be uploaded in a single PUT is 5 gigabytes. For objects larger than 100 megabytes, customers should consider using the Multipart Upload capability.

- What storage classes does Amazon S3 offer?

  Amazon S3 offers a range of storage classes designed for different use cases. There are three highly durable storage classes including Amazon S3 Standard for general-purpose storage of frequently accessed data, Amazon S3 Standard - Infrequent Access for long-lived, but less frequently accessed data, and Amazon Glacier for long-term archive. You can learn more about those three storage classes on the Amazon S3 Storage Classes page.

  Reduced Redundancy Storage (RRS) is an Amazon S3 storage option that enables customers to reduce their costs by storing noncritical, reproducible data at lower levels of redundancy than Amazon S3’s standard storage. You can learn more about Reduced Redundancy Storage on the Reduced Redundancy detail page.

- How can I delete large numbers of objects?

  You can use Multi-Object Delete to delete large numbers of objects from Amazon S3. This feature allows you to send multiple object keys in a single request to speed up your deletes. Amazon does not charge you for using Multi-Object Delete.

- How is Amazon S3 data organized?

  Amazon S3 is a simple key-based object store. When you store data, you assign a unique object key that can later be used to retrieve the data. Keys can be any string, and can be constructed to mimic hierarchical attributes.

- How reliable is Amazon S3?

  Amazon S3 gives any developer access to the same highly scalable, reliable, fast, inexpensive data storage infrastructure that Amazon uses to run its own global network of web sites. S3 Standard is designed for 99.99% availability and Standard - IA is designed for 99.9% availability. Both are backed by the Amazon S3 Service Level Agreement.

- What data consistency model does Amazon S3 employ?

  Amazon S3 buckets in all Regions provide read-after-write consistency for PUTS of new objects and eventual consistency for overwrite PUTS and DELETES.

- What is the BitTorrent™ protocol, and how do I use it with Amazon S3?

  BitTorrent is an open source Internet distribution protocol. Amazon S3’s bandwidth rates are inexpensive, but BitTorrent allows developers to further save on bandwidth costs for a popular piece of data by letting users download from Amazon and other users simultaneously. Any publicly available data in Amazon S3 can be downloaded via the BitTorrent protocol, in addition to the default client/server delivery mechanism. Simply add the ?torrent parameter at the end of your GET request in the REST API.

- How can I Increase the number of Amazon S3 buckets that I can provision?

  By default, customers can provision up to 100 buckets per AWS account. However, you can increase your Amazon S3 bucket limit by visiting AWS Service Limits.

Regions
--

- Where is my data stored?

  You specify a region when you create your Amazon S3 bucket. Within that region, your objects are redundantly stored on multiple devices across multiple facilities.

Billing
--

- How much does Amazon S3 cost?

  With Amazon S3, you pay only for what you use. There is no minimum fee. You can estimate your monthly bill using the AWS Simple Monthly Calculator.

Security
--

- How secure is my data?

  Amazon S3 is secure by default. Only the bucket and object owners originally have access to Amazon S3 resources they create. Amazon S3 supports user authentication to control access to data. You can use access control mechanisms such as bucket policies and Access Control Lists (ACLs) to selectively grant permissions to users and groups of users. Amazon S3 console highlights your publicly accessible buckets, indicates the source of public accessibility, and also warns you if changes to your bucket policies or bucket ACLs would make your bucket publicly accessible.

  You can securely upload/download your data to Amazon S3 via SSL endpoints using the HTTPS protocol. If you need extra security you can use the Server Side Encryption (SSE) option to encrypt data stored at rest. You can configure your Amazon S3 buckets to automatically encrypt objects before storing them if the incoming storage requests do not have any encryption information. Alternatively you can use your own encryption libraries to encrypt data before storing it in Amazon S3.

- What options do I have for encrypting data stored on Amazon S3?

  You can choose to encrypt data using SSE-S3, SSE-C, SSE-KMS, or a client library such as the Amazon S3 Encryption Client. All four enable you to store sensitive data encrypted at rest in Amazon S3:

  - SSE-S3 provides an integrated solution where Amazon handles key management and key protection using multiple layers of security. You should choose SSE-S3 if you prefer to have Amazon manage your keys.

  - SSE-C enables you to leverage Amazon S3 to perform the encryption and decryption of your objects while retaining control of the keys used to encrypt objects. With SSE-C, you don’t need to implement or use a client-side library to perform the encryption and decryption of objects you store in Amazon S3, but you do need to manage the keys that you send to Amazon S3 to encrypt and decrypt objects. Use SSE-C if you want to maintain your own encryption keys, but don’t want to implement or leverage a client-side encryption library.

  - SSE-KMS enables you to use AWS Key Management Service (AWS KMS) to manage your encryption keys. Using AWS KMS to manage your keys provides several additional benefits. With AWS KMS, there are separate permissions for the use of the master key, providing an additional layer of control as well as protection against unauthorized access to your objects stored in Amazon S3. AWS KMS provides an audit trail so you can see who used your key to access which object and when, as well as view failed attempts to access data from users without permission to decrypt the data. Also, AWS KMS provides additional security controls to support customer efforts to comply with PCI-DSS, HIPAA/HITECH, and FedRAMP industry requirements.

  - Using an encryption client library, such as the Amazon S3 Encryption Client, you retain control of the keys and complete the encryption and decryption of objects client-side using an encryption library of your choice.


- What is an Amazon VPC Endpoint for Amazon S3?

  An Amazon VPC Endpoint for Amazon S3 is a logical entity within a VPC that allows connectivity only to S3. The VPC Endpoint routes requests to S3 and routes responses back to the VPC. For more information about VPC Endpoints, read Using VPC Endpoints.

- What is Amazon Macie?

  Amazon Macie is an AI-powered security service that helps you prevent data loss by automatically discovering, classifying, and protecting sensitive data stored in Amazon S3. Amazon Macie uses machine learning to recognize sensitive data such as personally identifiable information (PII) or intellectual property, assigns a business value, and provides visibility into where this data is stored and how it is being used in your organization. Amazon Macie continuously monitors data access activity for anomalies, and delivers alerts when it detects risk of unauthorized access or inadvertent data leaks.

  You can use Amazon Macie to protect against security threats by continuously monitoring your data and account credentials. Amazon Macie gives you an automated and low touch way to discover and classify your business data. It provides controls via templated Lambda functions to revoke access or trigger password reset policies upon the discovery of suspicious behavior or unauthorized data access to entities or third-party applications. When alerts are generated, you can use Amazon Macie for incident response, using Amazon CloudWatch Events to swiftly take action to protect your data.


Data Protection
--

- How durable is Amazon S3?

  Amazon S3 Standard and Standard - IA are designed to provide 99.999999999% durability of objects over a given year. This durability level corresponds to an average annual expected loss of 0.000000001% of objects. For example, if you store 10,000 objects with Amazon S3, you can on average expect to incur a loss of a single object once every 10,000,000 years. In addition, Amazon S3 is designed to sustain the concurrent loss of data in two facilities.

  As with any environments, the best practice is to have a backup and to put in place safeguards against malicious or accidental users errors. For S3 data, that best practice includes secure access permissions, Cross-Region Replication, versioning and a functioning, regularly tested backup.

- What is Versioning?

  Versioning allows you to preserve, retrieve, and restore every version of every object stored in an Amazon S3 bucket. Once you enable Versioning for a bucket, Amazon S3 preserves existing objects anytime you perform a PUT, POST, COPY, or DELETE operation on them. By default, GET requests will retrieve the most recently written version. Older versions of an overwritten or deleted object can be retrieved by specifying a version in the request.

- How can I ensure maximum protection of my preserved versions?

  Versioning’s MFA Delete capability, which uses multi-factor authentication, can be used to provide an additional layer of security. By default, all requests to your Amazon S3 bucket require your AWS account credentials. If you enable Versioning with MFA Delete on your Amazon S3 bucket, two forms of authentication are required to permanently delete a version of an object: your AWS account credentials and a valid six-digit code and serial number from an authentication device in your physical possession. To learn more about enabling Versioning with MFA Delete, including how to purchase and activate an authentication device, please refer to the Amazon S3 Technical Documentation.



S3 Standard - Infrequent Access
--

- What is S3 Standard - Infrequent Access?

  Amazon S3 Standard - Infrequent Access (Standard - IA) is an Amazon S3 storage class for data that is accessed less frequently, but requires rapid access when needed. Standard - IA offers the high durability, throughput, and low latency of Amazon S3 Standard, with a low per GB storage price and per GB retrieval fee. This combination of low cost and high performance make Standard - IA ideal for long-term storage, backups, and as a data store for disaster recovery. The Standard - IA storage class is set at the object level and can exist in the same bucket as Standard, allowing you to use lifecycle policies to automatically transition objects between storage classes without any application changes.

- How durable is Standard - IA?

  S3 Standard - IA is designed for the same 99.999999999% durability as Standard and Amazon Glacier. Standard - IA is designed for 99.9% availability, and carries a service level agreement providing service credits if availability is less than our service commitment in any billing cycle.

- Is there a minimum duration for Standard - IA?

  Standard - IA is designed for long-lived, but infrequently accessed data that is retained for months or years. Data that is deleted from Standard - IA within 30 days will be charged for a full 30 days


Query in Place
--

- What is "Query in Place" functionality?

  Amazon S3 allows customers to run sophisticated queries against data stored without the need to extract, transform, and load (ETL) into a separate analytics platform. The ability to query this data in place on Amazon S3 can significantly increase performance and reduce cost for analytics solutions leveraging S3 as a data lake. S3 offers multiple query in place options, including S3 Select, Amazon Athena, and Amazon Redshift Spectrum, allowing you to choose one that best fits your use case. You can even use Amazon S3 Select with AWS Lambda to build serverless apps that can take advantage of the in-place processing capabilities provided by S3 Select.

- What is S3 Select?

  S3 Select is an Amazon S3 feature (currently in Preview) that makes it easy to retrieve specific data from the contents of an object using simple SQL expressions without having to retrieve the entire object. You can use S3 Select to retrieve a subset of data using SQL clauses, like SELECT and WHERE, from delimited text files and JSON objects in Amazon S3.

- What is Amazon Athena?

  Amazon Athena is an interactive query service that makes it easy to analyze data in Amazon S3 using standard SQL. Athena is serverless, so there is no infrastructure to setup or manage, and you can start analyzing data immediately. You don’t even need to load your data into Athena, it works directly with data stored in S3. To get started, just log into the Athena Management Console, define your schema, and start querying. Amazon Athena uses Presto with full standard SQL support and works with a variety of standard data formats, including CSV, JSON, ORC, Apache Parquet and Avro. While Amazon Athena is ideal for quick, ad-hoc querying and integrates with Amazon QuickSight for easy visualization, it can also handle complex analysis, including large joins, window functions, and arrays.

- What is Amazon Redshift Spectrum?

  Amazon Redshift Spectrum is a feature of Amazon Redshift that enables you to run queries against exabytes of unstructured data in Amazon S3, with no loading or ETL required. When you issue a query, it goes to the Amazon Redshift SQL endpoint, which generates and optimizes a query plan. Amazon Redshift determines what data is local and what is in Amazon S3, generates a plan to minimize the amount of Amazon S3 data that needs to be read, requests Redshift Spectrum workers out of a shared resource pool to read and process data from Amazon S3.

  Redshift Spectrum scales out to thousands of instances if needed, so queries run quickly regardless of data size. And, you can use the exact same SQL for Amazon S3 data as you do for your Amazon Redshift queries today and connect to the same Amazon Redshift endpoint using your same BI tools. Redshift Spectrum lets you separate storage and compute, allowing you to scale each independently. You can setup as many Amazon Redshift clusters as you need to query your Amazon S3 data lake, providing high availability and limitless concurrency. Redshift Spectrum gives you the freedom to store your data where you want, in the format you want, and have it available for processing when you need it.


Amazon Glacier
--

- Does Amazon S3 provide capabilities for archiving objects to lower cost storage options?

  Yes, Amazon S3 enables you to utilize Amazon Glacier’s extremely low-cost storage service as storage for data archival.  Amazon Glacier stores data for as little as $0.004 per gigabyte per month. To keep costs low yet suitable for varying retrieval needs, Amazon Glacier provides three options for access to archives, from a few minutes to several hours. Some examples of archive uses cases include digital media archives, financial and healthcare records, raw genomic sequence data, long-term database backups, and data that must be retained for regulatory compliance.

- Can I use the Amazon S3 APIs or Management Console to list objects that I’ve archived to Amazon Glacier?

  Yes, like Amazon S3’s other storage options (Standard or Standard - IA), Amazon Glacier objects stored using Amazon S3’s APIs or Management Console have an associated user-defined name. You can get a real-time list of all of your Amazon S3 object names, including those stored using the Amazon Glacier option, using the Amazon S3 LIST API.

- Can I use Amazon Glacier APIs to access objects that I’ve archived to Amazon Glacier?

  Because Amazon S3 maintains the mapping between your user-defined object name and Amazon Glacier’s system-defined identifier, Amazon S3 objects that are stored using the Amazon Glacier option are only accessible through the Amazon S3 APIs or the Amazon S3 Management Console.

- How can I retrieve my objects that are archived in Amazon Glacier?

  To retrieve Amazon S3 data stored in Amazon Glacier, initiate a retrieval request using the Amazon S3 APIs or the Amazon S3 Management Console. The retrieval request creates a temporary copy of your data in RRS while leaving the archived data intact in Amazon Glacier. You can specify the amount of time in days for which the temporary copy is stored in RRS. You can then access your temporary copy from RRS through an Amazon S3 GET request on the archived object.

- How long will it take to retrieve my objects archived in Amazon Glacier?

  When processing a retrieval job, Amazon S3 first retrieves the requested data from Amazon Glacier, and then creates a temporary copy of the requested data in RRS (which typically takes on the order of a few minutes). The access time of your request depends on the retrieval option you choose: Expedited, Standard, or Bulk retrievals. For all but the largest objects (250MB+), data accessed using Expedited retrievals are typically made available within 1 – 5 minutes. Objects retrieved using Standard retrievals typically complete between 3 – 5 hours. Lastly, Bulk retrievals typically complete within 5 – 12 hours. For more information about the retrieval options, please refer to the Glacier FAQ.

-  How am I charged for deleting objects from Amazon Glacier that are less than 3 months old?

  Amazon Glacier is designed for use cases where data is retained for months, years, or decades. Deleting data that is archived to Amazon Glacier is free if the objects being deleted have been archived in Amazon Glacier for three months or longer. If an object archived in Amazon Glacier is deleted or overwritten within three months of being archived then there will be an early deletion fee. This fee is prorated. If you delete 1GB of data 1 month after uploading it, you will be charged an early deletion fee for 2 months of Amazon Glacier storage. If you delete 1 GB after 2 months, you will be charged for 1 month of Amazon Glacier storage.


Event Notification
--

- What are Amazon S3 event notifications?

  Amazon S3 event notifications can be sent in response to actions in Amazon S3 like PUTs, POSTs, COPYs, or DELETEs. Notification messages can be sent through either Amazon SNS, Amazon SQS, or directly to AWS Lambda.

- What can I do with Amazon S3 event notifications?

  Amazon S3 event notifications enable you to run workflows, send alerts, or perform other actions in response to changes in your objects stored in Amazon S3. You can use Amazon S3 event notifications to set up triggers to perform actions including transcoding media files when they are uploaded, processing data files when they become available, and synchronizing Amazon S3 objects with other data stores. You can also set up event notifications based on object name prefixes and suffixes. For example, you can choose to receive notifications on object names that start with “images/."


Static Website Hosting
--
- Can I host my static website on Amazon S3?

  Yes, you can host your entire static website on Amazon S3 for an inexpensive, highly available hosting solution that scales automatically to meet traffic demands. Amazon S3 gives you access to the same highly scalable, reliable, fast, inexpensive infrastructure that Amazon uses to run its own global network of web sites. Service availability corresponds to storage class and the service level agreement provides service credits if a customer’s availability falls below our service commitment in any billing cycle. To learn more about hosting your website on Amazon S3, please see our walkthrough on setting up an Amazon S3 hosted website.

-  What kinds of websites should I host using Amazon S3 static website hosting?

  Amazon S3 is ideal for hosting websites that contain only static content, including html files, images, videos, and client-side scripts such as JavaScript. Amazon EC2 is recommended for websites with server-side scripting and database interaction.

-  Can I use my own host name with my Amazon S3 hosted website?

  Yes, you can easily and durably store your content in an Amazon S3 bucket and map your domain name (e.g. “example.com”) to this bucket. Visitors to your website can then access this content by typing in your website’s URL (e.g., “http://example.com”) in their browser.

- Does Amazon S3 support website redirects?

  Yes, Amazon S3 provides multiple ways to enable redirection of web content for your static websites. Redirects enable you to change the Uniform Resource Locator (URL) of a web page on your Amazon S3 hosted website (e.g. from www.example.com/oldpage to www.example.com/newpage) without breaking links or bookmarks pointing to the old URL. You can set rules on your bucket to enable automatic redirection. You can also configure a redirect on an individual S3 object.



Storage Management
--

- What are S3 Object Tags?

  S3 Object Tags are key-value pairs applied to S3 objects which can be created, updated or deleted at any time during the lifetime of the object. With these, you’ll have the ability to create Identity and Access Management (IAM) policies, setup S3 Lifecycle policies, and customize storage metrics. These object-level tags can then manage transitions between storage classes and expire objects in the background.

- How do I apply Object Tags to my objects?

  You can add tags to new objects when you upload them or you can add them to existing objects. Up to ten tags can be added to each S3 object and you can use either the AWS Management Console, the REST API, the AWS CLI, or the AWS SDKs to add object tags.

- How can I update the Object Tags on my objects?

  Object Tags can be changed at any time during the lifetime of your S3 object, you can use either the AWS Management Console, the REST API, the AWS CLI, or the AWS SDKs to change your object tags. Note that all changes to tags outside of the AWS Management Console are made to the full tag set. If you have five tags attached to a particular object and want to add a sixth, you need to include the original five tags in that request.

- Will my Object Tags be replicated if I use Cross-Region Replication?

  Object Tags can be replicated across regions using Cross-Region Replication.


S3 Analytics - Storage Class Analysis
--

- What is S3 Analytics – Storage Class Analysis?

  With storage class analysis, you can analyze storage access patterns and transition the right data to the right storage class. This new S3 Analytics feature automatically identifies infrequent access patterns to help you transition storage to Standard-IA. You can configure a storage class analysis policy to monitor an entire bucket, a prefix, or object tag. Once an infrequent access pattern is observed, you can easily create a new lifecycle age policy based on the results. Storage class analysis also provides daily visualizations of your storage usage on the AWS Management Console that you can export to a S3 bucket to analyze using business intelligence tools of your choice such as Amazon QuickSight.


S3 Inventory
--

- What is S3 Inventory?

  S3 Inventory provides a scheduled alternative to Amazon S3’s synchronous List API. You can configure S3 Inventory to provide a CSV or ORC file output of your objects and their corresponding metadata on a daily or weekly basis for an S3 bucket or prefix. You can simplify and speed up business workflows and big data jobs with S3 Inventory. You can use S3 inventory to verify encryption and replication status of your objects to meet business, compliance, and regulatory needs.


S3 CloudWatch Metrics
--

- How do I get started with S3 CloudWatch Metrics?

  You can use the AWS Management Console to enable the generation of 1-minute CloudWatch metrics for your S3 bucket or configure filters for the metrics using a prefix or object tag. Alternately, you can call the S3 PUT Bucket Metrics API to enable and configure publication of S3 storage metrics. Storage metrics will be available in CloudWatch within 15 minutes of being enabled.

- What alarms can I set on my storage metrics?

  You can use CloudWatch to set thresholds on any of the storage metrics counts, timers, or rates and fire an action when the threshold is breached. For example, you can set a threshold on the percentage of 4xx Error Responses and when at least 3 data points are above the threshold fire a CloudWatch alarm to alert a Dev Ops engineer.


Lifecycle Management Policies
--

- What is Lifecycle Management?

  S3 Lifecycle management provides the ability to define the lifecycle of your object with a predefined policy and reduce your cost of storage. You can set lifecycle transition policy to automatically migrate Amazon S3 objects to Standard - Infrequent Access (Standard - IA) and/or Amazon Glacier based on the age of the data. You can also set lifecycle expiration policies to automatically remove objects based on the age of the object. You can set a policy for multipart upload expiration, which expires incomplete multipart upload based on the age of the upload.


Cross-Region Replication
--

- What is Amazon S3 Cross-Region Replication (CRR)?

  CRR is an Amazon S3 feature that automatically replicates data across AWS regions. With CRR, every object uploaded to an S3 bucket is automatically replicated to a destination bucket in a different AWS region that you choose. You can use CRR to provide lower-latency data access in different geographic regions. CRR can also help if you have a compliance requirement to store copies of data hundreds of miles apart.

-  How do I enable CRR?

  **CRR is a bucket-level configuration.** You enable a CRR configuration on your source bucket by specifying a destination bucket in a different region for replication. You can use either the AWS Management Console, the REST API, the AWS CLI, or the AWS SDKs to enable CRR. **Versioning must be turned on for both the source and destination buckets to enable CRR**

- What does CRR replicate to the target bucket?

  CRR replicates every object-level upload that you directly make to your source bucket. The metadata and ACLs associated with the object are also part of the replication. Any change to the underlying data, metadata, or ACLs on the object would trigger a new replication to the destination bucket. You can either choose to replicate all objects uploaded to a source bucket or just a subset of objects uploaded by specifying prefixes. Existing data in the bucket prior to enabling CRR is not replicated. You can use S3’s COPY API to copy the existing data into your destination bucket.

- Can I use CRR with objects encrypted by AWS KMS?

  Yes, you can replicate KMS-encrypted objects by providing destination KMS key in your replication configuration

- Does enabling AWS KMS support for Cross-Region Replication affect KMS API rate?

  Yes, AWS KMS support for CRR will increase KMS API rate for your account. Specifically, **CRR will double the S3-related KMS API rate in the source region and increase by the same increment in the destination region.** We recommend requesting an increase in your KMS API rate limit by creating a case in the AWS support center. There is no additional cost for KMS API rate limit increase.


Amazon S3 Transfer Acceleration
--

- What is Transfer Acceleration?

  Amazon S3 Transfer Acceleration enables fast, easy, and secure transfers of files over long distances between your client and your Amazon S3 bucket. Transfer Acceleration leverages Amazon CloudFront’s globally distributed AWS Edge Locations. As data arrives at an AWS Edge Location, data is routed to your Amazon S3 bucket over an optimized network path.

- How should I choose between Transfer Acceleration and Amazon CloudFront’s PUT/POST?

  Transfer Acceleration optimizes the TCP protocol and adds additional intelligence between the client and the S3 bucket, making Transfer Acceleration a better choice if a higher throughput is desired. If you have objects that are smaller than 1GB or if the data set is less than 1GB in size, you should consider using Amazon CloudFront's PUT/POST commands for optimal performance.

- Can Transfer Acceleration complement AWS Direct Connect?

  AWS Direct Connect is a good choice for customers with a private networking requirement or have access to AWS Direct Connect exchanges. **Transfer Acceleration is best for submitting data from distributed client locations over the public Internet, or where variable network conditions make throughput poor.** Some AWS Direct Connect customers use Transfer Acceleration to help with remote office transfers, where they may suffer from poor Internet performance.


Amazon S3 and IPv6
--

- How do I get started with IPv6 on Amazon S3?

  You can get started by pointing your application to Amazon S3’s new “dual-stack” endpoint, which supports access over both IPv4 and IPv6. In most cases, no further configuration is required for access over IPv6, because most network clients prefer IPv6 addresses by default. Your applications may continue to access data through the existing APIs and virtual hosted style (e.g. http://bucket.s3.dualstack.aws-region.amazonaws.com) or path style (e.g. http://s3.dualstack.aws-region.amazonaws.com/bucket) URLs without code changes. When using Amazon S3 Transfer Acceleration, the “dual-stack” endpoint must be of the form http(s)://bucket.s3-accelerate.dualstack.amazonaws.com. However, you must also evaluate your bucket and Identity and Access Management (IAM) policies to ensure you have the appropriate access configured for your new IPv6 addresses

- If I point to Amazon S3's "dual-stack" endpoint, will I still be able to access Amazon S3's APIs over IPv4?

  Yes, you can continue to access Amazon S3 APIs using both IPv6 and IPv4 addresses when connecting to the Amazon S3 “dual-stack” endpoints. You will need to configure your client to prefer IPv4 addresses, which can be an application-level or host-level configuration option for many application runtime languages. Please consult the documentation for the language you are using for your runtime platform for the specific configuration option that prefers IPv4 connections.

- Do I need to update my bucket and IAM policies?

  Yes, if you use policies to grant or restrict access via IP addresses, you will need to update those policies to include the associated IPv6 ranges before you switch to the “dual-stack” endpoint. If your bucket grants or restricts access to specific IAM users, you will also need to have the IAM policy administrator review those users’ IAM policies to ensure they have appropriate access to the associated IPv6 ranges before you switch to the “dual-stack” endpoint. Failure to do so may result in clients incorrectly losing or gaining access to the bucket when they start using IPv6.

- Can I use IPv6 with all Amazon S3 features?

  No, IPv6 support is not currently available when using Website Hosting and access via BitTorrent. All other features should work as expected when accessing Amazon S3 using IPv6.

- Is IPv6 supported in all regions?

  You can use IPv6 with Amazon S3 in all commercial AWS Regions except China (Beijing). You can also use IPv6 in the AWS GovCloud (US) region.
