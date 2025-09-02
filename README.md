# AI News Agent

## Project Overview
This project is an automated AI agent built using n8n.io. The agent performs the following actions daily:
1.  Fetches the top latest articles from Google News based on drone-related keywords.
2.  Uses the Google Gemini API to generate a unique, ready-to-publish social media post for each article.
3.  Automatically posts these formatted summaries to a designated Discord channel.

## Tools Used
- **Automation Platform:** n8n.io (Cloud Version)
- **News Source:** Google News RSS Feed
- **AI Model:** Google Gemini API (via HTTP Request Node)
- **Output Platform:** Discord (via Webhook)

## Project Decisions & Technical Challenges
During development, several key decisions were made to ensure a robust and successful workflow:

* **Social Media Platform:** The agent posts the final content to a Discord channel. This method was chosen to effectively demonstrate a successful, end-to-end AI workflow without the need for complex developer account applications and authentication required by the LinkedIn or X (Twitter) APIs.

* **Image Extraction:** I investigated a method to scrape a featured image from each article. However, this was found to be unreliable because the Google News RSS feed provides redirect links, not direct article links. These links use complex JavaScript to redirect, which cannot be processed by standard automation tools. Therefore, to ensure reliability, the project was scoped to be text-only.

* **Link Reliability:** The links provided by the Google News RSS feed are temporary redirect links, not permanent URLs. This can cause intermittent failures when Discord attempts to generate a link preview. After investigation, it was determined that the most stable approach is to have the AI present the link plainly, as additional formatting attempts were found to interfere with the fragile redirect URLs. The occasional link failure is a known limitation of the data source.