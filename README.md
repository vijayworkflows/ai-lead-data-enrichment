# AI-Powered Lead Enrichment


## Project Overview

Sales teams often receive leads with limited company and prospect information. Manually researching every prospect takes time and makes it difficult to prioritize opportunities.

<img width="959" height="413" alt="AI_Lead_Enrichment" src="https://github.com/user-attachments/assets/56e9bbd0-40ff-4f8a-8166-47dbd136b27d" />


This project automates the enrichment process by combining website data extraction with AI-powered analysis.

The workflow receives qualified leads from Project 01, retrieves publicly available company website content, and uses Google Gemini to generate actionable sales intelligence.

## Business Objectives

- Automate company research and lead enrichment.
- Reduce manual prospect research.
- Identify potential business challenges and product use cases.
- Assess buying intent and decision-maker relevance.
- Generate personalized first-touch sales outreach.
- Return structured enrichment data for downstream sales workflows.

## Workflow Architecture

```text
Project 01
Lead Qualification
       |
       v
Project 02
AI-Powered Lead Enrichment
       |
       v
Normalize Lead
       |
       v
Validate Website
       |
       v
HTTP Request
(Fetch Website Content)
       |
       v
Basic AI Input
(Extract and Prepare Text)
       |
       v
Basic LLM Chain
       |
       +------ Google Gemini
       |
       +------ Structured Output Parser
       |
       v
AI Node
       |
       v
Enriched Lead Output
```

## Technology Stack

| Technology               | Purpose                                |
| ------------------------ | -------------------------------------- |
| n8n                      | Workflow orchestration and automation  |
| Google Gemini            | AI-powered company and lead analysis   |
| HTTP Request             | Retrieve company website content       |
| JavaScript               | Data normalization and text extraction |
| Structured Output Parser | Generate structured JSON responses     |
| JSON                     | Data exchange between workflows        |

## Key Features

### 1. Workflow Integration

Receives qualified lead records from the parent lead qualification workflow using n8n's Execute Sub-workflow functionality.

### 2. Website Normalization

Normalizes company website URLs and checks whether a valid website is available before attempting retrieval.

### 3. Website Content Extraction

Uses HTTP Request to retrieve website HTML and JavaScript code to extract relevant page information, including:

- Page title
- Meta description
- Main page content
- Relevant company information

### 4. AI-Powered Lead Analysis

Google Gemini analyzes the lead information alongside the extracted website content.

The AI generates:

- Company overview
- Business model
- Likely business challenges
- Potential product use cases
- Buying intent
- Decision-maker relevance
- Recommended sales approach
- Personalized outreach message
- Confidence level
- Evidence and unknowns

### 5. Structured JSON Output

Uses the Structured Output Parser to ensure the AI response follows a predefined JSON schema, making it easier for downstream workflows and sales systems to consume the results.

## Sample Output Structure

```json
{
  "companyOverview": "Company overview based on available evidence",
  "businessModel": "Description of the business model",
  "likelyChallenges": [
    "Potential business challenge 1",
    "Potential business challenge 2"
  ],
  "potentialUseCases": [
    "Potential use case 1",
    "Potential use case 2"
  ],
  "buyingIntent": "Unknown",
  "decisionMakerRelevance": "Assessment of the prospect's role",
  "recommendedSalesApproach": "Recommended sales strategy",
  "personalizedOutreach": "Suggested first-touch message",
  "confidence": "Medium",
  "evidenceAndUnknowns": [
    "Evidence: Information found on the company website",
    "Unknown: Information not available from the supplied data"
  ]
}
```

## Business Value

- Reduces repetitive manual company research.
- Helps sales teams understand prospects before outreach.
- Supports more relevant and personalized communication.
- Standardizes lead enrichment outputs.
- Creates a foundation for automated CRM updates and sales handoffs.

## Limitations and Considerations

- Website analysis depends on publicly accessible website content.
- Some websites may block automated HTTP requests.
- AI-generated business challenges and use cases may contain assumptions.
- Buying intent cannot be reliably established from company website content alone.
- AI-generated insights should be reviewed before being used in customer communication.

## Setup Requirements

1. An n8n instance.
2. A Google Gemini API key.
3. A configured Google Gemini credential in n8n.
4. Import the workflow JSON into n8n.
5. Connect the Gemini credential to the Google Gemini Chat Model node.
6. Connect the workflow to the parent lead qualification workflow.

**Security:** Never commit API keys, credentials, `.env` files, or real customer data to the repository.

## Project Status

**Completed** — AI-powered lead enrichment workflow built and tested.

## Future Enhancements

- Integrate company data enrichment APIs.
- Add CRM integration for enriched lead updates.
- Introduce confidence-based lead review.
- Add automated sales routing based on enrichment results.
- Implement website content caching to reduce repeated requests.

## Author

**Vijay Prakash**

GTM Engineering | Marketing Automation | Workflow Automation

