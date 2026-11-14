# BusinessRateChecker connector (MCP)

[![Listed on mcpservers.org](https://mcpservers.org/badge.svg)](https://mcpservers.org/servers/rspiegelberg-cmd/businessratechecker-mcp)

Business rates data for England and Wales inside an AI assistant: rateable values, comparables, an overpayment verdict, rating history and Valuation Tribunal decisions.

This repository is the public listing for the hosted connector. It holds no code and no data. The connector runs at:

```
https://www.businessratechecker.com/mcp
```

Transport: streamable HTTP (Model Context Protocol). Official MCP Registry name: `com.businessratechecker/mcp`.

## Connect

Step-by-step instructions for Claude, ChatGPT, Microsoft Copilot and other assistants: https://www.businessratechecker.com/connect

Two tools answer with no sign-in. The rest ask you to sign in once with an email address.

Generic client configuration:

```json
{
  "mcpServers": {
    "businessratechecker": {
      "type": "http",
      "url": "https://www.businessratechecker.com/mcp"
    }
  }
}
```

## What it answers

| Tool | What it does | Sign-in |
|---|---|---|
| `explain_business_rates` | How bills, multipliers and reliefs work, transitional relief, Check, Challenge and Appeal, deadlines and contacts, for England or Wales, with official sources | No |
| `get_overpayment_map` | How many properties our checks flag as paying too much, by country or council, with each council's rank | No |
| `find_properties` | Look up an address by postcode and words in the address or description | Yes |
| `get_property` | Rateable value, how the Valuation Office built it, estimated bill and whether a Check or Challenge has been decided | Yes |
| `get_overpayment_verdict` | Our verdict from comparable evidence, the indicative saving, and how the Valuation Office's own scheme values similar properties | Yes |
| `get_comparables` | The similar properties behind the verdict, with £ per m² and distance | Yes |
| `get_rating_history` | Rateable values on earlier rating lists and changes on the 2026 list | Yes |
| `search_properties` | Filter and sort an area's properties: type, size, value, £ per m², verdict, business name, street | Yes |
| `area_breakdown` | Counts, medians and totals by street, sector, property type, postcode or verdict | Yes |
| `search_tribunal_decisions` | Published business rates appeal decisions in England (since 2020) and Wales (since 2018): which succeeded, which failed, how far values came down, and why | Yes |
| `find_rating_surveyors` | The firms most active at the tribunal in the last 12 months, plus rating firms with an office nearby | Yes |
| `get_area_statistics` | What the Valuation Office changed in one month, by council | Yes |
| `get_sector_statistics` | What the Valuation Office changed in one month, by sector | Yes |
| `get_account_usage` | How much of your monthly allowance is left and when it resets | Yes |

## The data

- Every non-domestic property in England and Wales on the 2026 rating list from the Valuation Office: address, description, rateable value, floor area, the valuation lines and the UARN, with the 2023-list value (England and Wales) and the 2017-list value (England) where held.
- Every Valuation Office alteration to the 2026 list, and the Check and Challenge case status recorded against each property.
- Published decisions of the Valuation Tribunal for England and the Valuation Tribunal for Wales, linked to the properties they concern, with the firms that represented the ratepayer.
- Matched property by property where available: floor areas from the EPC register, and business names from the Food Standards Agency register, the NHS pharmacy, dental and optical registers and council ratepayer lists.
- A comparable-evidence verdict and indicative saving for every property, the same as on the website.

Our pipeline runs every day and collects what the Valuation Office, the tribunals and the other registers have published.

Scotland and Northern Ireland have separate rating systems and are not covered.

## Example questions

- "Is my unit in Hereford paying too much in business rates?"
- "The 10 biggest offices in Manchester by £ per m²"
- "What happened at the Valuation Tribunal for shops in Leeds?"
- "Which firms take the most rating appeals to the tribunal in Bristol?"
- "How does small business rate relief work in Wales?"

## Terms and contact

- Plans, how it works and questions: https://www.businessratechecker.com/professionals
- Terms, including the Valuation Office licence conditions: https://www.businessratechecker.com/api/terms
- Privacy: https://www.businessratechecker.com/privacy
- Support: support@businessratechecker.com

Verdicts are indicative estimates from comparable evidence, not valuations or advice. Valuation Office data is used under licence; the Valuation Office does not endorse this service.

BusinessRateChecker is operated by Mirror Mountain Ltd (company no. 15478792).
