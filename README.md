# Aram-Radif-AI-Custom-Named-Entity-Recognition-Custom-NER-
Building, training, evaluating, and deploying a Custom Named Entity Recognition (NER) model 

Overview
Custom Named Entity Recognition (NER) enables you to extract domain specific entities (such as prices, locations, legal terms, or product names) from unstructured text where built in NER categories are insufficient.
Typical use cases include:
•	Legal and financial document analysis
•	Knowledge mining for search and discovery
•	Compliance and audit text scanning
•	Classified ads, invoices, or contracts
An entity can represent a person, place, object, event, skill, or value.
________________________________________
Objectives
•	Custom vs built in NER in Azure
•	Define and label custom entities
•	Train, evaluate, and improve a custom NER model
•	Deploy a trained model for production use
•	Extract entities using the Azure AI Text Analytics SDK
________________________________________
Custom vs Built in NER
Built in NER
Azure provides pre trained entity recognition for common categories such as:
•	Person
•	Location
•	Organization
•	URL
•	DateTime
These require minimal setup and are ideal for general extraction tasks.
Custom NER
Custom NER is used when:
•	Entities are domain specific
•	Only specific entity types should be extracted
•	Built in categories are insufficient
Examples:
•	Bank statements (AccountNumber, LoanAmount)
•	Legal contracts (ClauseType, EffectiveDate)
•	Classified ads (ItemForSale, Price, Location)
________________________________________
Azure Language Project Lifecycle
1.	Define entities – Clearly specify what you want to extract
2.	Label data – Tag entity spans in training documents
3.	Train model – Teach the model how to identify entities
4.	Evaluate model – Review precision, recall, and F1 score
5.	Improve model – Add or refine training data
6.	Deploy model – Make it accessible via API
7.	Extract entities – Consume results from your application
________________________________________
Data & Entity Design Best Practices
Data Quality
•	Diversity: Use documents from multiple formats and sources
•	Distribution: Match real world frequency of entities
•	Accuracy: Real data > synthetic data
Entity Design
•	Avoid ambiguous entity definitions
•	Prefer specific entities over broad ones
•	Example:
o	❌ ContactInfo
o	✅ PhoneNumber, Email, SocialHandle
________________________________________
Labeling Your Data
Labeling is critical for model performance.
Labeling Principles
•	Consistency – Same entity, same labeling rules
•	Precision – Label only the exact entity text
•	Completeness – Don’t miss valid entities
Tools
•	Azure AI Language Studio (recommended)
•	Supports manual labeling with auto generated JSON metadata
________________________________________
Training & Evaluation Metrics
Azure evaluates models using:
Metric	Description
Precision	Correct extractions ÷ total extractions
Recall	Correct extractions ÷ actual entities
F1 Score	Harmonic mean of precision & recall
Interpretation
•	High precision, low recall → model is cautious
•	Low precision, high recall → model over extracts
•	Low both → insufficient or inconsistent training data
A confusion matrix is available to diagnose entity level issues.
________________________________________
Entity Extraction via API
Custom NER extraction is executed using the CustomEntityRecognition task.
Key inputs:
•	Project name
•	Deployment name
•	One or more text documents
The API returns recognized entities with confidence scores.
________________________________________
 Azure Service Limits (Summary)
•	Training files: 10 – 100,000
•	Entity types: Up to 200
•	Deployments: 10 per project
•	Models: 50 per project
Refer to official Azure documentation for full limits.
________________________________________
End to End Lab (Summary)
1. Provision Azure AI Language Service
•	Enable Custom NER feature
•	Create associated Storage Account
2. Configure Access
•	Assign Storage Blob Data Contributor role
3. Upload Training Data
•	Upload sample classified ads to Blob Storage
4. Create Custom NER Project
•	Define project metadata
•	Connect storage container
5. Label Entities
•	ItemForSale
•	Price
•	Location
6. Train Model
•	Automatically split training/testing data
7. Evaluate & Improve
•	Review model performance metrics
8. Deploy Model
•	Create deployment endpoint
9. Consume from Python App
•	Use Azure AI Text Analytics SDK
•	Extract entities from text files
________________________________________
 Python SDK Highlights
•	Uses TextAnalyticsClient
•	Authenticated via endpoint + API key
•	Supports batch document processing
•	Returns entities with category & confidence score
________________________________________
Clean Up
To avoid unnecessary costs:
•	Delete the Custom NER project from Language Studio
•	Remove the Azure AI Language resource
•	Delete the associated Storage Account
________________________________________
📚 References
•	Azure AI Language Documentation
•	Custom Named Entity Recognition
•	Azure AI Text Analytics SDK
________________________________________
Repository Structure
.
├── ads/ # Sample text documents
├── custom-entities.py # Python extraction script
├── requirements.txt # Python dependencies
├── .env # Azure credentials (not committed)
└── README.md # Project documentation
Security note: Add .env to .gitignore to avoid committing secrets.
________________________________________
 Getting Started
Prerequisites
•	Azure subscription with Azure AI Language Service enabled (Custom NER)
•	Python 3.9+
•	Deployed Custom NER project and deployment
Installation
python -m venv .venv
source .venv/bin/activate # Windows: .venv\Scripts\activate
pip install -r requirements.txt
Configuration
Create a .env file with the following values:
AI_LANGUAGE_ENDPOINT=<your-endpoint>
AI_LANGUAGE_KEY=<your-key>
PROJECT_NAME=<your-project-name>
DEPLOYMENT_NAME=<your-deployment-name>
Run
python custom-entities.py
The script will process the sample ads and print extracted entities with confidence scores.
________________________________________
Clean-Up
To avoid unnecessary Azure costs:
•	Delete the Custom NER project from Azure AI Language Studio
•	Remove the Azure AI Language resource
•	Delete the associated Storage Account
________________________________________

--

Aram Radif

