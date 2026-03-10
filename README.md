# 🚀 AI-Powered Lead Generation Engine (n8n)

An automated, end-to-end lead generation pipeline built on **n8n**. It intelligently sources business leads from Google Maps, conducts deep prospect research using **Google Gemini**, and verifies email deliverability via the **Reoon API**.

---

## ✨ Key Features

- **Automated Sourcing:** Scrapes local business data (names, websites, phone numbers) from Google Maps using **SerpAPI**.
- **AI-Driven Research:** Employs **Google Gemini 2.0 Flash** to identify decision-makers, job titles, and social media profiles.
- **Smart Verification:** Validates emails using **Reoon Email Verifier** to ensure high deliverability and protect your sender reputation.
- **Deduplication:** Automatically filters out duplicate leads and businesses without websites.
- **CRM Integration:** Syncs all data in real-time across structured **Google Sheets** tabs.

---

## 🏗️ Architecture

For a detailed breakdown of the system design and data flow, please refer to the [Architecture Documentation](./architecture.md).

---

## 🛠️ Prerequisites

To run this workflow, you will need:

1.  **n8n** (Self-hosted or Cloud version).
2.  **Google Cloud Project:** With Google Sheets API enabled.
3.  **API Keys for:**
    *   **SerpAPI:** For Google Maps scraping.
    *   **Google Gemini (PaLM/Google AI):** For AI research.
    *   **Reoon Email Verifier:** For lead validation.

---

## 🚀 Getting Started

### 1. Repository Setup
Clone this repository or download the JSON workflow:
```bash
git clone https://github.com/yourusername/lead-generation-n8n.git
```

### 2. Import to n8n
1. Open your n8n instance.
2. Click on **Workflows** > **Import from File**.
3. Select `workflow/Lead Generation.json`.

### 3. Configure Credentials
Set up the following credentials in n8n:
- **Google Sheets OAuth2:** For database access.
- **SerpApi:** For the Google Maps scraper node.
- **Google Gemini (PaLM) Api:** For the AI research nodes.
- **HTTP Request (Reoon):** Ensure your Reoon API key is correctly configured in the "Reoon Keys" node or as a global credential.

### 4. Setup Google Sheets
Create a Google Sheet with the following tabs:
- `Keywords`: Columns `Keywords`, `Status`.
- `Serp Raw Data`: As per the schema in [architecture.md](./architecture.md).
- `Raw Data`: For processed and researched leads.

---

## ⚙️ Configuration

- **Research Strategy:** The AI agent is pre-configured to prioritize official websites and social platforms. You can adjust the system prompt in the `Prospect Research` node for different industries.
- **Batch Processing:** Use the `Limit` nodes in each step to control how many leads are processed per run to manage API costs and rate limits.

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/yourusername/lead-generation-n8n/issues).
