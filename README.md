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

## Step 1 - Prepare Knowledge Base Documents

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

## Step 2 - Upload Documents to Amazon S3

Create a S3 bucket. 
```
organization-knowledge-documents
```

Create folders.

```
security-faq/
policies/
architecture/
compliance/
```

Upload all documentation.
## Step 3 - Create a knowledge base
### Step 3.1 - Choose knowldge base source, Choose the bucket containing documentation.
### Step 3.2 - Configure vector store - S3 Vector DB, OpenSearch
### Step 3.3 - Choose embeddings model
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

## Step 4 - Create Agent and Choose Knowledge base
### Step 4.1 - Create Agent
### Step 4.2 - Edit in Agent
### Step 4.3 - Choose foundational model
### Step 4.4 - Configure Agent Instructions
### Step 4.5 - Associate Knowledge Base

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

Wait until the agent status becomes

```
Prepared
```


# Step 7 - Test the Agent

Use the built-in test console.

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

