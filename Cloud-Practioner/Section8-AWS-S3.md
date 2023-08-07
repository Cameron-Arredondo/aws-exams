# AWS S3
Infinitely scaling storage

## Use Cases
- Back up/ Storage
- Disaster Recovery
- Archive Files
- Hybrid Cloud Storage
- Application hosting
- Host Media
- Data Lake and Big Data Analytics
- Host static websites

Amazon S3 allows people to store files in buckets (directories)
Buckets Must have a globally unique name (across all regions)
Buckets are defined at the region level
no uppercase, no underscore for naming buckets

## Objects
Objects are (files) have a key.  The key is the Full Path, the key is composed of a prefix + object name.
- Object values are the content of the body:
    - Max OBJ size is 5TB (5000GB)
    - If uploading more than 5GB, must use "multi-part upload"
    - Metadata, Tags, Version ID