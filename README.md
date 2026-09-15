# Google Maps Lead Scraper — n8n

A reusable n8n workflow that collects business leads from Google Maps using Apify and automatically stores them in Google Sheets.

The workflow also prevents duplicate businesses from being added by using the Google Maps `placeId` as a unique identifier.

## 🚀 Features

- Collect business leads from Google Maps
- Search by keyword and location
- Choose the number of businesses to collect
- Choose the language
- Store results automatically in Google Sheets
- Remove duplicates within the current run
- Prevent previously collected businesses from being added again
- Uses `placeId` for duplicate detection
- No custom scraping code required

🛠️ Tools
  -n8n
  -Apify
  -Google Sheets
  -Google Maps

  📋 Input Fields
  | Field    | Description                         |
| -------- | ----------------------------------- |
| Keyword  | Business type or search term        |
| Location | City, region, or location to search |
| Number   | Maximum number of places to collect |
| Language | Language used for the search        |

Example
Keyword: Restaurants
Location: Constantine, Algeria
Number: 50
Language: English

📊 Output
The workflow stores the following information in Google Sheets:
| Column           | Description                         |
| ---------------- | ----------------------------------- |
| Name of Business | Business name                       |
| Address          | Business address                    |
| City             | City                                |
| Phone            | Business phone number               |
| Score            | Google Maps rating                  |
| Website          | Business website                    |
| placeId          | Unique Google Maps place identifier |


🔁 Duplicate Protection
The workflow uses placeId to prevent duplicate businesses.

There are two levels of duplicate protection:

1. Current run

The Remove Duplicates node removes repeated businesses returned during the same scraping run.

2. Previous runs

The workflow retrieves existing rows from Google Sheets and compares their placeId values with the new results.

Only businesses that do not already exist in the spreadsheet are appended.

⚙️ Setup
Requirements

You need your own:

n8n instance
Apify account
Google account
Google Sheets spreadsheet
1. Import the workflow

Download or clone this repository and import workflow.json into n8n.

2. Connect Apify

Create your own Apify account and configure the HTTP Request node with your own Apify API authentication.

Do not use or share someone else's API token.

3. Connect Google Sheets

Connect your own Google Sheets account to both Google Sheets nodes:

Get row(s) in sheet
Append row in sheet
4. Create your spreadsheet

Create a Google Sheet with the following column headers:
Name of Business  Address   City   Phone  Score   Website   placeId
Make sure the headers match the workflow fields.

5. Configure the spreadsheet

Select your spreadsheet and worksheet in both Google Sheets nodes.

6. Activate the workflow

After testing the workflow successfully, activate it in n8n.


🔐 Security

This repository does not contain:
  Apify API tokens
  Google OAuth credentials
  Private Google Sheets
  Personal account information


Always use your own credentials when configuring the workflow.

Never commit API keys, passwords, OAuth tokens, or other secrets to GitHub.


📁 Repository Structure
google-maps-lead-scraper-n8n/
│
├── README.md
├── workflow.json
├── screenshots/
│   ├── workflow.png
│   └── result.png
│
└── .gitignore

💡 Possible Improvements

Future versions could include:

  Lead qualification filters
  Industry/category filters
  Website availability filtering
  Rating filters
  Export to CSV
  Email notifications
  Automatic lead scoring
  CRM integration
  AI-powered lead qualification
  Scheduled scraping



📄 License

This project is provided as an n8n workflow template for learning and automation purposes.
