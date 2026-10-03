# Conical Forum Record

Conical Forum builds a working model of how you think through conversation. This plugin connects that
record to Claude, so Claude can look up what you have said you believe, how you have changed your mind,
and how you tend to approach decisions, and give advice that fits you instead of generic advice.

## What you get

- **A connector** to the Conical Forum record at `https://forum.conical.tech/mcp`. You sign in with your
  Forum account and approve what Claude may do. You can limit access to specific domains, or read-only.
- **A skill, `conical-record`,** that tells Claude when to consult your record (questions about you,
  personal decisions, "what did I think about X"), when to save to it, and what never to do. For example,
  Claude never shows raw personality scores and always says whether something was stated by you or inferred.

## Use it

1. Add the plugin, then connect **Conical Forum Record** from the plugin's Connectors tab and sign in.
   You need a Conical Forum account with connector access enabled.
2. Ask naturally:
    - "What did I decide about moving teams, and did I change my mind?"
    - "Given how I work, how should I approach this negotiation?"
    - "Remember that I value autonomy over salary."
    - "Save this conversation to my record."
    - "Let's tidy up my record." Claude walks you through uncertain beliefs one at a time.

## Tools the connector provides

| Tool                   | What it does                                                  | Changes data? |
| ---------------------- | ------------------------------------------------------------- | ------------- |
| `list_domains`         | Lists the domains in your record                              | No            |
| `get_profile`          | Domains plus narrative insights (no scores)                   | No            |
| `get_user_context`     | Quick calibration: current beliefs and recent themes          | No            |
| `ask_record`           | Answers a question about you from your record, with citations | No            |
| `how_do_i_approach`    | Describes how you tend to approach a situation                | No            |
| `get_operating_manual` | "How to work with me" summary                                 | No            |
| `what_did_i_think`     | Belief history, including revisions and retractions           | No            |
| `search` / `fetch`     | Keyword search and full item lookup                           | No            |
| `get_wrap_up`          | Reads an existing daily wrap-up (never generates one)         | No            |
| `review_queue`         | Lists inferred beliefs for you to confirm                     | No            |
| `record_belief`        | Saves a belief you stated                                     | Adds          |
| `record_entry`         | Saves a journal entry you wrote                               | Adds          |
| `save_conversation`    | Saves a conversation transcript                               | Adds          |
| `rate_result`          | Records whether a result was helpful                          | Adds          |
| `refine_belief`        | Confirms, revises or retracts a belief (history kept)         | Changes       |

Tools that add or change data are marked as such, so Claude asks before running them. Claude only writes
when you ask, or after offering once and getting a yes.

## Data

The plugin itself stores nothing and sends nothing. It is a connector address and a skill file. When you
use the connector, the questions and content Claude passes to the tools are sent to Conical Forum
(`forum.conical.tech`), stored in your Forum account, and processed by Google's Gemini models to answer
questions and extract beliefs. Nothing is sent to any other destination.

You can disconnect at any time from Forum under **Account → Connected apps**, which takes effect
immediately. You can delete conversations and your account from Forum.

- Documentation: <https://conical-tech.com/docs/connect-to-your-ai/claude-connector>
- Privacy policy: <https://forum.conical.tech/privacy>
- Terms: <https://forum.conical.tech/terms>
- Support: <contact@conical-tech.com>
