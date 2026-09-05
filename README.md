Here's a table detailing each model, specifying our findings relating to key generation, storage, and access to storage:
|  Service/Test  | Who Is Generating the Key | Where Is the Key Stored | Who Has Access to Storage |
| ------------- | ------------- | ------------- | ------------- |
| S3 + Google Colab  | The user  | The user's device  | The user  |
| Cryptomator  | Cryptomator  | Vault Folder  | The user  |
|  SSE-S3 | Amazon S3 | Amazon’s secure S3 backend | Amazon S3 |
| AWS KMS Amazon Managed Key | AWS KMS | AWS KMS | AWS and the user |
| AWS KMS CMK| The user | AWS KMS | The user and AWS |
| GCS | The user | GCS backend | GCS and the user|

This table shows each model's strengths and weaknesses:

| Model | Strengths | Weaknesses |
| ------------- | ------------- | ------------- |
| SSE-S3 | Easy, automatic, User doesn’t manage keys | Zero user control, complete trust in AWS |
| SSE-KMS | Simple, some auditability | Provider-controlled, confusing for non-experts |
| S3 + Colab CSE | User controls key | Risk of losing key, harder setup, manual sharing |
| CSE(Cryptomator) | Full client control, zero-trust model | Risk of losing key, less convenient for collaboration |
| AWS KMS CMK | Granular control, key rotation, strong audit trails | Complex setups, risk of locking out data, trust in AWS |
| GCS | Precise control, key rotation, simpler interface | Key rotation = no decryption, might lock data out, trust in GCS |
