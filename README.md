# Project n8n - Business Automation Workflows

This repository contains n8n automation workflows and templates designed to streamline business processes, lead generation, and data analysis using AI-powered tools.

## 📋 Overview

This project leverages n8n (a free, open-source workflow automation tool) to create powerful automations that:
- Search and discover business leads automatically
- Analyze online presence using AI
- Extract contact information from web search results
- Provide structured, actionable business intelligence

All automations use **completely free tools and services** with no subscription fees or paywalls.

---

## 🚀 Current Automations

### 1. Business Lead Discovery Workflow

**File:** `business-lead-discovery-workflow.json`

A comprehensive automation that searches the web for businesses in specific categories and locations, then uses AI to analyze their online presence.

#### Features:
- ✅ **Input Handling**: Accept business category (e.g., "hotels", "restaurants") and location (e.g., "Kigali", "New York")
- ✅ **Web Search**: Automatically searches for businesses using Google Custom Search API (free tier: 100 queries/day)
- ✅ **Data Parsing**: Extracts business names, websites, and snippets from search results
- ✅ **Contact Extraction**: Finds email addresses and phone numbers using pattern matching
- ✅ **AI Analysis**: Determines online presence quality and professional website status
- ✅ **Structured Output**: Returns formatted results with scores and insights

#### Workflow Structure:
```
Input Parameters → Web Search → Parse Results → Extract Contact Info → AI Analysis → Format Output → Output Results
```

#### Nodes Used:
1. **Input Parameters** - Sets business category and location variables
2. **Web Search** - HTTP request to Google Custom Search API
3. **Parse Search Results** - Code node to extract business data
4. **Extract Contact Info** - Code node with regex for emails/phones
5. **AI Analysis** - OpenAI/HuggingFace node for intelligent analysis
6. **Format Output** - Code node to combine all data
7. **Output Results** - NoOp node for final output

#### Sample Input:
```json
{
  "business_category": "hotels",
  "location": "Kigali"
}
```

#### Sample Output:
```json
{
  "business_name": "Hotel Example",
  "website_url": "https://hotelexample.com",
  "has_website": true,
  "has_email": true,
  "has_phone": true,
  "emails": "info@hotelexample.com",
  "phones": "+250 788 123 456",
  "search_rank": 1,
  "online_presence_score": 8,
  "has_professional_website": "Yes",
  "ai_analysis": "Strong online presence with professional website and complete contact information.",
  "timestamp": "2026-03-04T10:30:00Z"
}
```

#### Setup Requirements:
1. **Google Custom Search API Key** (Free)
   - Visit: https://console.cloud.google.com/
   - Create a new project
   - Enable Custom Search API
   - Generate API key

2. **Custom Search Engine ID** (Free)
   - Visit: https://cse.google.com/cse/
   - Create a new search engine
   - Copy the Search Engine ID (cx parameter)

3. **OpenAI API Key** (Free tier available) OR alternatives:
   - Hugging Face (free models)
   - Ollama (local, completely free)
   - Any other LLM provider supported by n8n

#### How to Use:
1. Import `business-lead-discovery-workflow.json` into n8n
2. Update API keys in the "Web Search" node
3. Configure AI model credentials if using OpenAI
4. Modify input parameters as needed
5. Execute the workflow
6. Review structured business leads in output

---

## 🛠️ Technology Stack

- **Automation Platform**: n8n (open-source, self-hosted)
- **Search API**: Google Custom Search API (free tier)
- **AI/ML**: OpenAI GPT-3.5-turbo or compatible alternatives
- **Data Processing**: JavaScript (Code nodes)
- **Output Format**: JSON

---

## 📦 Installation & Setup

### Prerequisites
- n8n instance (self-hosted or cloud)
- Node.js 16+ (for self-hosting)
- API keys for required services

### Quick Start
1. Clone or download this repository
2. Open your n8n instance
3. Click "Import Workflow" in n8n
4. Select any `.json` workflow file from this repo
5. Configure API credentials in the respective nodes
6. Activate and run the workflow

---

## 🔮 Planned Automations

Future workflows to be added:
- [ ] Social Media Lead Generation
- [ ] Email Verification & Validation
- [ ] Competitor Price Monitoring
- [ ] Customer Feedback Aggregation
- [ ] Multi-platform Content Publishing
- [ ] CRM Data Synchronization

---

## 📝 License

This project is licensed under the terms specified in the LICENSE file.

---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Submit new workflow templates
- Improve existing automations
- Report bugs or issues
- Suggest new features

---

## 💡 Tips & Best Practices

1. **Rate Limits**: Be mindful of API rate limits (Google Custom Search: 100 queries/day free)
2. **Error Handling**: Add error handling nodes for production workflows
3. **Credentials**: Store API keys securely using n8n's credential management
4. **Testing**: Test workflows with small batches before scaling
5. **Monitoring**: Set up webhook notifications for workflow failures

---

## 📞 Support

For questions or issues:
- Check n8n documentation: https://docs.n8n.io/
- Review workflow JSON files for inline comments
- Refer to API provider documentation for authentication details

---

**Last Updated**: March 4, 2026
