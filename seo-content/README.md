# Perplexity Workflow for n8n

This n8n workflow automates the process of generating SEO-optimized content for a WordPress blog post based on a given keyword. It leverages the Perplexity API for research, an AI language model for content generation, and WordPress integration for publishing. The workflow is designed to create content that adheres to Google's E-E-A-T (Experience, Expertise, Authoritativeness, Trustworthiness) and Helpful Content Guidelines.

## Workflow Overview

The workflow performs the following steps:
1. **Trigger**: Initiates when manually triggered (e.g., clicking "Test workflow").
2. **Set Keyword**: Defines the keyword for content generation (e.g., "khóa học AI automation với n8n").
3. **Perplexity API Call**: Sends a detailed prompt to the Perplexity API to research the keyword, analyze search intent, competition, and create an optimized prompt for content generation.
4. **AI Content Generation**: Uses an OpenRouter language model to generate a JSON output containing a blog post title, HTML content, and meta description.
5. **Structured Output Parsing**: Ensures the AI output is formatted correctly in JSON.
6. **WordPress Publishing**: Publishes the generated content directly to a WordPress site.

## Prerequisites

- **n8n Instance**: A running n8n instance with access to the workflow editor.
- **Credentials**:
  - Perplexity API (Bearer Auth) for the HTTP Request node.
  - OpenRouter API for the AI language model.
  - WordPress API for publishing content.
- **Dependencies**:
  - n8n-nodes-base (for Manual Trigger, Set, HTTP Request, and WordPress nodes).
  - @n8n/n8n-nodes-langchain (for Basic LLM Chain and Structured Output Parser).

## Node Details

1. **When clicking ‘Test workflow’** (Manual Trigger)
   - Initiates the workflow manually.
   - Pin Data: Sets the keyword (e.g., "khóa học thiết kế AI agent").

2. **Edit Fields** (Set Node)
   - Defines the keyword as a string (e.g., "khóa học AI automation với n8n").
   - Output: Passes the keyword to the next node.

3. **Outline** (HTTP Request Node)
   - Sends a POST request to the Perplexity API (`https://api.perplexity.ai/chat/completions`).
   - Uses Bearer Authentication with the Perplexity API credentials.
   - Sends a JSON body with a detailed prompt for SEO research and content outline creation.
   - Output: A prompt for generating JSON with title, HTML content, and meta description.

4. **Basic LLM Chain** (LangChain Node)
   - Processes the Perplexity API output using the OpenRouter Chat Model (`google/gemini-2.5-flash`).
   - Generates structured JSON output with the blog post details.

5. **OpenRouter Chat Model** (LangChain Node)
   - Configured with OpenRouter API credentials.
   - Provides the AI model for content generation.

6. **Structured Output Parser** (LangChain Node)
   - Ensures the AI output adheres to the required JSON schema (`title`, `content`, `meta_description`).

7. **Wordpress** (WordPress Node)
   - Publishes the generated content to a WordPress site.
   - Uses WordPress API credentials.
   - Sets the post title, content, and status (e.g., "publish").

## Setup Instructions

1. **Import Workflow**:
   - Copy the provided JSON workflow and import it into your n8n instance.
2. **Configure Credentials**:
   - Set up Perplexity API credentials for the "Outline" node.
   - Configure OpenRouter API credentials for the "OpenRouter Chat Model" node.
   - Add WordPress API credentials for the "Wordpress" node.
3. **Set Keyword**:
   - Update the "Edit Fields" node with your desired keyword or modify the pin data in the Manual Trigger node.
4. **Test Workflow**:
   - Run the workflow manually to test the content generation and publishing process.
5. **Deploy**:
   - Activate the workflow for automated or scheduled runs if needed.

## Output

The workflow generates a JSON object with:
- **title**: A concise, SEO-optimized title (<60 characters) containing the keyword.
- **content**: HTML body content (1500-2000 words) with proper tags (`<h1>`, `<h2>`, `<p>`, `<ul>`, `<img>`).
- **meta_description**: A 100-160 character description for SEO.

The content is published directly to WordPress as a blog post.

## Notes

- The workflow is tailored for Vietnamese content (`ngôn ngữ: Tiếng Việt`).
- Images are sourced from reputable platforms like Unsplash and Pexels, with direct URLs provided.
- The content adheres to Google’s SEO guidelines, incorporating LSI keywords, FAQs, and internal links.
- Ensure API rate limits and quotas for Perplexity and OpenRouter are not exceeded during execution.

## Troubleshooting

- **API Errors**: Verify credentials and API keys for Perplexity, OpenRouter, and WordPress.
- **Content Issues**: Check the Perplexity API response in the "Outline" node for correct prompt formatting.
- **WordPress Publishing**: Ensure the WordPress API endpoint and credentials are correctly configured.

For further assistance, refer to the n8n documentation or contact the workflow creator.