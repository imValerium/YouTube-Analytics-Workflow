# YouTube Channel Analytics Insights Workflow

This n8n project consists of 2 automated workflows. One than automates the process of fetching YouTube analytics data and generating detailed insights, which are then sent to your Gmail as a weekly report. And another that supports dynamic queries based on user input.

Features
- Fetches YouTube channel metrics (e.g., views, likes, subscribers, etc.) dynamically based on user input or weekly schedules.
- Sends detailed analytics summaries via Gmail.
- Configurable to adapt to your YouTube channel and email settings.

---

Setup Instructions

1. Requirements
- n8n instance: Local or hosted instance of n8n.
- **YouTube Analytics API access**:
  - Create a project in the [Google Cloud Console](https://console.cloud.google.com/).
  - Enable the **YouTube Analytics API** and configure OAuth2 credentials.
- **Gmail API access**:
  - Enable the **Gmail API** and configure OAuth2 credentials.
- **OpenAI API key** (optional):
  - Sign up for an API key at [OpenAI](https://platform.openai.com/).

---

2. Workflow Configuration

Environment Variables
Update your `.env` file with the following variables:
```env
USER_EMAIL=your_email@example.com
CHANNEL_ID=your_channel_id

Required Credentials
In your n8n instance, configure the following credentials:

YouTube OAuth2 API:
Add the YouTube OAuth2 credential in the Credentials section.
Use the client ID and secret from your Google Cloud project.

Gmail OAuth2 API:
Add the Gmail OAuth2 credential.
Use the client ID and secret from your Google Cloud project.

OpenAI API (or other LLM):
Add the OpenAI API credential using your OpenAI API key.

3. Workflow Setup
Webhook Setup
Replace YOUR_WEBHOOK_ID with your webhook ID. n8n will generate this ID automatically when you save the workflow.

Node Parameters
Dynamic Query Handling:
Metrics and dates are fetched dynamically based on user input.
Ensure the Code2 and Fetch Analytics Data nodes are configured with the correct field mappings.
Email Configuration:
Update the email template with any custom formatting or additional data fields as needed.
Testing

Import the workflow into a new n8n instance.
Test the webhook by sending a chat message or triggering the workflow manually.

4. Workflow Overview
Workflow Nodes

Trigger Options:
When chat message received: Handles real-time user input for custom analytics queries.
Schedule Trigger: Automates weekly analytics reporting.

Data Fetching:
Fetch Analytics Data: Queries YouTube Analytics API for the requested metrics.

Data Parsing:
Code Nodes: Parse and structure the API responses for detailed analytics.

Insights and Reporting:
AI Agents: Generate detailed insights using OpenAI's API (optional).
Gmail: Sends the final report to your email.

5. Customization
Add Metrics
To add additional YouTube metrics, update the Analytics Fetcher node to include the new metrics.
Change Email Format
Modify the email template in the Gmail node to include personalized content or additional formatting.
Error Handling
Add error-handling logic in the Code nodes or use Error Trigger nodes to handle issues like missing data or API failures.

6. Sharing the Workflow
When sharing the workflow:
Ensure sensitive information like API keys and OAuth credentials is replaced with placeholders.
Include clear instructions for setting up credentials and environment variables.

Example Scenarios
Real-Time User Query:
User sends a message: "Fetch my analytics for the last 7 days."
The workflow fetches data dynamically and sends the insights via email.
Automated Weekly Reporting:
The workflow triggers every Sunday at 3 PM and sends a detailed weekly analytics report.

Troubleshooting
Error: Missing Credentials
Ensure all required credentials are configured correctly in n8n.
Error: No Data Returned
Check the YouTube Analytics API permissions and ensure the channel ID is correct.
