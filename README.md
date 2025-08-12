# MCP AWS SES SMTP Email Server

A Model Context Protocol (MCP) server for sending emails via AWS SES SMTP interface.

## Features

- 🚀 **Full MCP Protocol Compliance** - JSON-RPC 2.0 with proper error handling
- 📧 **AWS SES SMTP Integration** - Simple username/password authentication
- 🔧 **Essential Email Tools** - Send emails with attachments and templates
- ⚡ **Cloudflare Workers** - Fast, global edge deployment
- 🔒 **Type Safe** - Full TypeScript with Zod validation
- 💰 **Cost Effective** - AWS SES competitive pricing with SMTP simplicity

## Available Tools

### `send_email`
Send a single email to one or more recipients.

**Parameters:**
- `to`: Array of recipient email addresses
- `subject`: Email subject line
- `body`: Email body (HTML or plain text)
- `from`: Sender email (optional, uses default)
- `replyTo`: Reply-to address (optional)

### `get_email_quota`
Check your SES sending quota and usage.

## Setup

### 1. Set up GitHub Actions (Optional)

To enable automatic deployment, move the deploy.yml file to .github/workflows/deploy.yml:

\`\`\`bash
mkdir -p .github/workflows
mv deploy.yml .github/workflows/deploy.yml
\`\`\`

Or deploy manually using the Cloudflare Workers button:

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/GITHUB_USERNAME/mcp-email-aws-ses-smtp-template)

### 2. Configure Environment Variables

Set these in your Cloudflare Workers dashboard or via GitHub secrets:

- `AWS_SES_USERNAME`: Your SES SMTP username (from SES console)
- `AWS_SES_PASSWORD`: Your SES SMTP password (from SES console)
- `AWS_REGION`: AWS region (default: us-east-1)
- `EMAIL_DEFAULT_FROM`: Default sender email address (must be verified in SES)

### 3. AWS SES Setup

1. **Verify your sending domain/email** in AWS SES console
2. **Create SMTP credentials** in SES console → SMTP settings
3. **Request production access** if sending to non-verified emails
4. **Configure bounce/complaint handling** (recommended)

### 4. Connect to Claude Desktop

Add to your Claude Desktop configuration:

\`\`\`json
{
  "mcpServers": {
    "email": {
      "url": "https://your-worker.workers.dev",
      "transport": "http"
    }
  }
}
\`\`\`

## Usage Examples

### Send a Simple Email
\`\`\`
Please send an email to john@example.com with subject "Meeting Tomorrow" and body "Don't forget our 2pm meeting"
\`\`\`

### Send HTML Email
\`\`\`
Send a welcome email to new@user.com with our branded HTML template
\`\`\`

### Check Sending Limits
\`\`\`
What's my current SES email quota and usage?
\`\`\`

## Local Development

1. Clone this repository
2. Install dependencies: `npm install`
3. Copy environment variables from AWS SES console
4. Run locally: `npm run dev`
5. Deploy: `npm run deploy`

## Error Handling

The server provides detailed error messages for:
- Invalid email addresses
- Missing SES credentials
- SMTP authentication failures
- Rate limiting
- Unverified sender addresses

## AWS SES SMTP Considerations

- **Sandbox Mode**: New AWS accounts start in sandbox mode (can only send to verified emails)
- **Sending Limits**: AWS SES has sending quotas that increase over time
- **SMTP Endpoint**: Uses region-specific SMTP endpoints (e.g., email-smtp.us-east-1.amazonaws.com)
- **Authentication**: Simple username/password from SES console

## Support

For issues or questions:
- Check the [MCP Creator documentation](https://mcp-creator.com/docs)
- Open an issue in this repository
- Contact support via the MCP Creator platform
- Review [AWS SES SMTP documentation](https://docs.aws.amazon.com/ses/latest/dg/send-email-smtp.html)
