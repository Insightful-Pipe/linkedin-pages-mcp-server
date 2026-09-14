# LinkedIn Page & Profile MCP Server by Insightful Pipe

[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-blue)](https://insightfulpipe.com/mcp-servers/linkedin-pages)
[![Insightful Pipe](https://img.shields.io/badge/Insightful_Pipe-MCP_Servers-purple)](https://insightfulpipe.com/mcp-servers)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

> **Connect LinkedIn Page & Profile to AI assistants: company page and personal profile analytics and publishing.**

Part of the [Insightful Pipe MCP Server Collection](https://insightfulpipe.com/mcp-servers) — use LinkedIn Page & Profile from Claude, ChatGPT, Cursor, and other AI assistants through the Model Context Protocol (MCP).

<img src="images/linkedin-pages-icon.svg" alt="LinkedIn Page & Profile MCP Server" width="64" height="64">

## MCP Server URL

```
https://linkedin-pages.insightfulmcp.com/
```

## What is LinkedIn Page & Profile MCP?

LinkedIn Page & Profile MCP is a **remote Model Context Protocol server** hosted by InsightfulPipe. Track LinkedIn page performance, follower growth, post engagement, and publish content on your organisation page and personal profile.

## Installation

### Claude

1. Copy the MCP Server URL: `https://linkedin-pages.insightfulmcp.com/`
2. Open [Claude Connectors Settings](https://claude.ai/settings/connectors)
3. Scroll to the bottom and click **Add custom connector**
4. Paste the URL and click **Add**
5. Click **Connect** on the connector to start authorization
6. Click **Authorize access** in the browser to complete the connection

### ChatGPT

Custom MCP servers are added through ChatGPT's **Developer mode**. Availability depends on your ChatGPT plan, and workspace admins may need to allow it.

1. Turn on **Developer mode** in ChatGPT settings
2. Create a new app for a remote MCP server and paste the URL: `https://linkedin-pages.insightfulmcp.com/`
3. Authorize with your InsightfulPipe account

See OpenAI's guide: [Developer mode and MCP apps in ChatGPT](https://help.openai.com/en/articles/12584461-developer-mode-and-mcp-apps-in-chatgpt)

### Claude Code

```bash
claude mcp add --transport http linkedin-pages https://linkedin-pages.insightfulmcp.com/
```

### Cursor

Add the server to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{
  "mcpServers": {
    "linkedin-pages": {
      "url": "https://linkedin-pages.insightfulmcp.com/"
    }
  }
}
```

Then authorize the connection when Cursor prompts you.

## Available Actions

45 actions: 30 read, 15 write.

### Read Actions (30)

<details>
<summary>Show all 30 read actions</summary>

| Action | Description |
|--------|-------------|
| `fetch_follower_statistics` | Fetch current follower demographics (by function, geo, industry, seniority, company size) |
| `fetch_follower_statistics_time_bound` | Fetch follower gains over time (organic + paid), daily or monthly |
| `fetch_member_connections_count` | Fetch the authenticated member's 1st-degree connection count |
| `fetch_member_followers_count` | Fetch lifetime follower count for the authenticated member |
| `fetch_member_followers_count_time_bound` | Fetch daily follower count for the authenticated member over a date range |
| `fetch_member_post_analytics_aggregated` | Fetch aggregated post analytics across all of the authenticated member's posts |
| `fetch_member_profile` | Fetch the authenticated member's profile (name, vanity name, profile picture) |
| `fetch_org_notifications` | Pull engagement notifications (likes, comments, shares, mentions) for the org |
| `fetch_org_video_analytics` | Fetch video analytics for an org post that contains a video |
| `fetch_organization_admins` | Fetch admin roles for the organization (ADMINISTRATOR, CONTENT_ADMIN, etc.) |
| `fetch_organization_brands` | Fetch showcase / brand pages under the organization |
| `fetch_organization_details` | Fetch full organization details (name, description, logo, website, etc.) |
| `fetch_organization_events` | Fetch events organized by the organization |
| `fetch_organization_posts` | Fetch posts published by the organization (paginated) |
| `fetch_page_statistics` | Fetch lifetime page view statistics (desktop/mobile breakdown by section) |
| `fetch_page_statistics_time_bound` | Fetch time-bound page view statistics, daily or monthly |
| `fetch_post_by_urn` | Fetch a single post by its URN |
| `fetch_post_comments` | Fetch comments on a post (paginated) |
| `fetch_post_reactions` | Fetch reactions (likes) on a post (paginated) |
| `fetch_share_statistics` | Fetch aggregate engagement metrics (impressions, clicks, likes, comments, shares) |
| `fetch_share_statistics_per_post` | Fetch engagement stats for specific org posts (impressions, clicks, likes, comments, shares) |
| `fetch_share_statistics_time_bound` | Fetch engagement metrics over time, daily or monthly |
| `fetch_social_metadata` | Fetch reaction breakdown (LIKE, PRAISE, EMPATHY, etc.) and comment counts for a post |
| `fetch_total_follower_count` | Fetch total follower count for the organization |
| `get_document_status` | Fetch processing status for an initialized document |
| `get_image_status` | Fetch processing status for an initialized image |
| `get_post_social_actions` | Get summary of likes, comments, shares for a post |
| `get_video_status` | Fetch processing status for an initialized or finalized video |
| `search_organization_by_vanity_name` | Search for an organization by its vanity name (URL slug, e.g. "insightful-pipe") |
| `search_organization_followers` | Typeahead search through the organization's followers |

</details>

### Write Actions (15)

| Action | Description |
|--------|-------------|
| `create_member_comment` | Post a comment on a post as the authenticated member |
| `create_member_post` | Create a new post as the authenticated member |
| `create_organization_comment` | Post a comment on a post as the organization |
| `create_organization_post` | Create a new post on behalf of the organization |
| `create_reaction` | React (LIKE) to a post as the org or member |
| `delete_comment` | Delete a comment on a post |
| `delete_member_post` | Delete a member's post |
| `delete_organization_post` | Delete an organization post |
| `delete_reaction` | Remove a reaction from a post |
| `finalize_video_upload` | Finalize a video upload after all chunks are uploaded |
| `initialize_document_upload` | Initialize a document/PDF upload (for carousels) |
| `initialize_image_upload` | Initialize an image upload |
| `initialize_video_upload` | Initialize a video upload |
| `reshare_member_post` | Reshare a post as the authenticated member |
| `reshare_organization_post` | Reshare an existing post on behalf of the organization |

## Control What Your AI Can Do

You decide what AI agents can do with each connected account:

- **Turn individual actions on or off** for every connected account, so agents only see the actions you allow.
- **Connect as Read-only or Read & Write.** A read-only connection can only enable read actions.
- **Destructive actions stay off by default.** Actions such as deletes are disabled until an admin enables them.
- **Team access per account.** Restricted team members only use the accounts they are granted, with the read actions enabled on them.

## Usage Examples

```
"How did our LinkedIn page followers grow over the last 90 days?"
```

```
"Which company page posts got the most engagement this month?"
```

```
"Publish a post on our company page announcing our new webinar"
```

## Ready-Made Skills and Prompts

- [Claude skills for LinkedIn](https://insightfulpipe.com/marketing-claude-skills/linkedin-ads) — ready-made skills that run on your connected data

## Explore More MCP Servers by Insightful Pipe

Visit **[insightfulpipe.com/mcp-servers](https://insightfulpipe.com/mcp-servers)** to discover our full collection of MCP servers.

- [Instagram MCP](https://insightfulpipe.com/mcp-servers/instagram)
- [Facebook Pages MCP](https://insightfulpipe.com/mcp-servers/facebook-pages)
- [YouTube MCP](https://insightfulpipe.com/mcp-servers/youtube)

**[View All MCP Servers →](https://insightfulpipe.com/mcp-servers)**

## Resources

- [Documentation](https://insightfulpipe.com/docs/connectors-linkedin-pages)
- [Video Tutorial](https://www.youtube.com/playlist?list=PLJNzvjxzI5Xwe__BJJLAelSF0ewO3mEFk)
- [InsightfulPipe Blog](https://insightfulpipe.com/blog)

## Support

- **Documentation**: [insightfulpipe.com/docs](https://insightfulpipe.com/docs)
- **All MCP Servers**: [insightfulpipe.com/mcp-servers](https://insightfulpipe.com/mcp-servers)
- **Email**: support@insightfulpipe.com

---

**[Insightful Pipe](https://insightfulpipe.com)** — AI-powered marketing analytics through MCP servers. [Explore all integrations →](https://insightfulpipe.com/mcp-servers)

## License

MIT License - see [LICENSE](LICENSE) for details.
