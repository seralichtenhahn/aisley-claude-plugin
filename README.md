# Aisley for Claude

[Aisley](https://getaisley.com) is an AI wedding planner. She writes to the venues, reads the replies, and does the chasing. You make the decisions.

This plugin brings your Aisley wedding into Claude: the Aisley connector, plus skills that teach Claude how to plan with it.

## What you can ask

- "What needs us this week?" for a short briefing: days to the wedding, replies waiting on you, follow-ups ready to send, and the to-dos that matter most.
- "Find barn venues near Bath for 120 guests under £15k." Aisley searches, explains why each venue fits, and saves the ones you pick to your shortlist.
- "Ask our top three venues if they're free next June." Aisley drafts a personal enquiry to each venue. You read every email in full, and it goes from your Gmail only once you approve it.
- "Who hasn't got back to us?" Claude shows who you are waiting on and for how long, and the follow-up Aisley drafted for each.
- "What did the Old Rectory say?" Claude summarises the reply and drafts an answer with you.

You can also keep the to-do list, the budget, your notes and your moodboards up to date from the conversation.

## What's inside

| Component | What it does |
| --- | --- |
| Aisley connector (`.mcp.json`) | Connects Claude to your wedding at `https://getaisley.com/mcp` |
| `wedding-check-in` skill | The weekly briefing |
| `venue-search` skill | Searching for venues and working the shortlist |
| `venue-outreach` skill | Enquiries to one or several venues |
| `vendor-inbox` skill | Reading replies, answering them, and sending follow-ups |

The skills are plain instructions. The plugin runs no code on your computer.

## Install

You need an Aisley account with a wedding set up. Sign up at [getaisley.com/signup](https://getaisley.com/signup).

**claude.ai and Cowork:** add the plugin from **Customize > Plugins**, then connect Aisley from the plugin's **Connectors** tab. You sign in to Aisley and choose which wedding to connect.

**Claude Code:**

```bash
claude plugin marketplace add seralichtenhahn/aisley-claude-plugin
claude plugin install aisley@aisley
```

Then run `/mcp` and sign in to Aisley.

## Your data

The plugin talks only to Aisley's server at `getaisley.com`, over OAuth: you sign in on getaisley.com and choose one wedding, and Claude never sees your password. Claude reads and changes that wedding's plan in Aisley: venues, conversations with venues and suppliers, to-dos, budget, notes and moodboards. Emails go from your connected Gmail only after you approve the exact text. Aisley never deletes your wedding or removes anyone from it.

Disconnect at any time from Aisley's settings. The [privacy policy](https://getaisley.com/privacy-policy) explains what Aisley stores and for how long, and the [terms](https://getaisley.com/terms-of-service) cover the service. Developer documentation is at [getaisley.com/developers](https://getaisley.com/developers).

## Support

Write to [hello@getaisley.com](mailto:hello@getaisley.com) or use [getaisley.com/contact](https://getaisley.com/contact).

## License

MIT. See [LICENSE](LICENSE).
