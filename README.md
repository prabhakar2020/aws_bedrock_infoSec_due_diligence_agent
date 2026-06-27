# AWS Bedrock Agent - Information Security Due Diligence Agent

Organizations receive information security due diligence questionnaires from customers before onboarding, contract renewals, or audits. These questionnaires assess the organization's security, privacy, compliance, and operational controls.

I have prepared Bedrock agent, it enables customers, auditors, and internal stakeholders to ask natural language questions related to the organization's security posture (Security, Sales, Compliance, Engineering, and Customer Success) to quickly retrieve accurate, consistent, and approved answers from the organization's Knowledge Base, reducing manual effort and accelerating customer responses.

This Agent answers **Information Security Due Diligence** questions using a **Knowledge Base** containing security documentation, FAQs, policies, and compliance information.

# Execution flow

```
User -> AWS Bedrock Agent
   │
   ▼
Knowledge Base
   │
   ▼
Amazon S3
   │
   ├── Security Questionnaires
   ├── Security Policies
   ├── Security FAQs
   ├── Compliance Documents
   ├── Architecture Documents
   ├── CSV Files
   └── PDF Documents
```

# Prerequisites

* Knowledge Base documents
* Foundation Model access enabled
* IAM Role for Bedrock
* Bedrock access

### Step 1 - Prepare Knowledge Base Documents

Upload all organization information security related documents on S3 that contains organization security information.

Examples include:

* Information Security FAQs
* Security Policies
* Security Standards
* Security Whitepapers
* ISO 27001 Controls
* SOC2 Information
* GDPR Documentation
* Architecture Documents
* Cloud Security Controls
* Vendor Management Process
* Incident Response Process
* Disaster Recovery Plan
* Business Continuity Plan
* Risk Management Process
* Change Management Process

Supported formats include: PDF, DOCX, TXT, CSV, HTML

### Step 2 - Upload Documents to Amazon S3

Create a S3 bucket. 
```
organization-policy-documents
```
Create folders.

```
security-faq/
policies/
architecture/
compliance/
```
<img width="953" height="350" alt="image" src="https://github.com/user-attachments/assets/4dcddb37-42af-4c97-98a1-befa29579dc0" />

Upload all documentation.
## Step 3 - Create a knowledge base
Goto Amazon Bedrock -> Knowledge Base
<img width="937" height="465" alt="image" src="https://github.com/user-attachments/assets/5f407e88-d69e-4379-9d1a-cfe1f8f61f0c" />
You can choose Unstructure Store KB OR Structure Store KB based on your requirement. Here I am choosing Unstructure Store KB
<img width="938" height="475" alt="image" src="https://github.com/user-attachments/assets/1944e4d6-ccdc-49d5-a051-00aa2da7c833" />
<img width="940" height="446" alt="image" src="https://github.com/user-attachments/assets/4e4a3b6b-d417-4e06-8e5b-c45b20b620d5" />
Choose Data source 
<img width="937" height="450" alt="image" src="https://github.com/user-attachments/assets/3b62cb0c-5ef1-4e80-ab63-16463de9e729" />
### Step 3.1 - Choose knowldge base source, Choose the bucket containing documentation.
<img width="943" height="478" alt="image" src="https://github.com/user-attachments/assets/694786b0-c977-4dd0-8ac3-493b91f3c76c" />
<img width="953" height="478" alt="image" src="https://github.com/user-attachments/assets/91f533e4-56c8-4888-b0fa-03b2a67d4b2c" />
### Step 3.2 - Configure vector store - S3 Vector DB, OpenSearch
<img width="940" height="476" alt="image" src="https://github.com/user-attachments/assets/e9bb64b2-c28f-4c2f-af82-524dcbcbf7e1" />
### Step 3.3 - Choose embeddings model
<img width="943" height="345" alt="image" src="https://github.com/user-attachments/assets/28653f41-57c3-4baf-abe6-b6c95fef39ea" />
<img width="955" height="479" alt="image" src="https://github.com/user-attachments/assets/28528bea-9f6e-4209-a201-354889071883" />
### Step 3.4 - Sync Knowledge Base

```
Start ingestion.
Bedrock will:

* Read documents
* Chunk content
* Generate embeddings
* Store vectors
* Build searchable knowledge

Wait until the status becomes: Available
```

<img width="937" height="474" alt="image" src="https://github.com/user-attachments/assets/4076df24-b13c-43c3-ad9a-f1a6241c55dd" />

## Step 4 - Create Agent and Choose Knowledge base
### Step 4.1 - Create Agent - Goto Amazon Bedrock -> Agents
<img width="947" height="397" alt="image" src="https://github.com/user-attachments/assets/9ea8d203-1acc-4a16-89a1-4989943bc69f" />
<img width="952" height="470" alt="image" src="https://github.com/user-attachments/assets/fbfaa793-29fc-4d13-8c2a-49cf3aad756c" />

### Step 4.2 - Click on "Edit in  Builder"
<img width="944" height="368" alt="image" src="https://github.com/user-attachments/assets/19d3df5e-974e-4ebc-bb3d-d5cb6afc9832" />

### Step 4.3 - Choose foundational model
<img width="941" height="477" alt="image" src="https://github.com/user-attachments/assets/3f83023d-e215-4319-b2e6-91dbf9a79e59" />
<img width="940" height="494" alt="image" src="https://github.com/user-attachments/assets/15e5df2b-6410-421b-b198-560ee3af0fd8" />


### Step 4.4 - Configure Agent Instructions "Instructions for the Agent"
<img width="937" height="476" alt="image" src="https://github.com/user-attachments/assets/911fec0e-7e6b-42dc-b4b3-0c7bcc15eb05" />
<img width="938" height="473" alt="image" src="https://github.com/user-attachments/assets/864cfb0d-029f-402c-bd97-654e5aaa9cb8" />

```
Organizations receive information security due diligence questionnaires from customers before onboarding, contract renewals, or audits. These questionnaires assess the organization's security, privacy, compliance, and operational controls.

The Amazon Bedrock Agent enables internal teams (Security, Sales, Compliance, Engineering, and Customer Success) to quickly retrieve accurate, consistent, and approved answers from the organization's Knowledge Base, reducing manual effort and accelerating customer responses.
```
### Step 4.5 - Associate Knowledge Base
<img width="945" height="355" alt="image" src="https://github.com/user-attachments/assets/f3183a2c-4e2e-40b1-acbe-f1205b1bfd53" />
<img width="950" height="477" alt="image" src="https://github.com/user-attachments/assets/1bb72a98-427c-433e-a42c-d5c2d27b6074" />
<img width="952" height="395" alt="image" src="https://github.com/user-attachments/assets/c164b948-9f60-4bd5-89be-236098aea85f" />
Update "Knowledge base instructions for the Agent"
```
Knowledge base for all information security related content
```
<img width="938" height="442" alt="image" src="https://github.com/user-attachments/assets/f5466594-ee38-4ad6-96d8-620958f26809" />
Click on Save and Exit
# Step 5 - Configure IAM Permissions

Ensure the Bedrock Agent IAM Role has access to:

* Amazon S3
* Bedrock
* OpenSearch
* CloudWatch Logs
* KMS (if applicable)

# Step 6 - Build the Agent

Choose

```
Prepare Agent
```
<img width="946" height="481" alt="image" src="https://github.com/user-attachments/assets/a252149b-b647-45b1-ae22-48e4fc0e0231" />

Wait until the agent status becomes

```
Prepared
```


# Step 7 - Test the Agent

Use the built-in test console.
<img width="950" height="477" alt="image" src="https://github.com/user-attachments/assets/fa2e45ae-d5a4-4cd7-a6ec-559b6985e446" />

Example prompts:

```
How do you segregate tenant data?

Do you support BYOK?

How is data encrypted?

What is your disaster recovery strategy?

Describe your change management process.

How are privileged users managed?

Do you support logical tenant isolation?

Can customers use customer managed KMS keys?

Describe your incident response process.

How do you onboard third-party vendors?
```



# Troubleshooting

## Agent does not answer correctly

* Verify Knowledge Base ingestion completed successfully.
* Ensure documents contain the required information.
* Re-sync the Knowledge Base after document updates.
* Confirm the correct Knowledge Base is attached to the agent.

## No response from Knowledge Base

* Check IAM permissions.
* Verify S3 bucket access.
* Confirm vector store is healthy.
* Ensure embedding generation completed successfully.

