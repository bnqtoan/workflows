# Amy Bank - Text to Bank Transfer QR Code Generator

This n8n workflow automates the process of generating QR codes for bank transfers in Vietnam by extracting banking information from text messages.

## Use Cases

1. **Quick Bank Transfer QR Generation**: Customer service representatives can quickly generate QR codes from text messages containing bank transfer details, making it easier for customers to make payments.

2. **Standardizing Transfer Information**: Convert various text formats containing bank transfer information into standardized QR codes, ensuring consistency and reducing manual data entry errors.

3. **Chat-based Payment Processing**: Integration with chat systems to automatically process payment information and generate QR codes when customers share bank transfer details.

## How it Works

1. The workflow is triggered when a chat message is received through a webhook endpoint.

2. An Information Extractor node processes the incoming message to extract key banking details:
   - Bank name
   - Account number
   - Transfer amount
   - Transfer content/description

3. The extracted information is processed using Google's Gemini AI model to ensure accurate interpretation of the text.

4. A code node transforms the bank transfer content by:
   - Normalizing Vietnamese characters
   - Removing special characters
   - Generating a QR code URL using the sepay.vn service

5. Finally, the workflow generates a formatted response containing:
   - The generated QR code image
   - Bank name and account number
   - Transfer content
   - Formatted amount

## Services

- **Google Gemini AI**: Used for natural language processing and information extraction
- **Sepay QR Generator**: Generates bank transfer QR codes (qr.sepay.vn)
- **Webhook Integration**: For receiving chat messages

## Hashtags

#bankingAutomation #qrCode #chatbot #vietnamFintech #n8n 