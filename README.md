<h1>🏏 AgenticAI-Powered Cricket Player Intelligence System</h1><br><br>
An intelligent n8n workflow that analyzes cricket players using multi-AI models (GPT-4 & Gemini). Extracts real-time data from ESPN Cricinfo/Cricbuzz, evaluates performance metrics, injury status & match suitability, then generates detailed PDF reports for strategic team selection decisions.<br><br>
📋 Overview<br>
This intelligent system analyzes cricket players' suitability for specific match scenarios by:

Searching and extracting real-time data from cricket databases
Performing multi-layered AI analysis using OpenAI GPT-4 and Google Gemini models
Generating comprehensive reports on player performance, fitness, and match suitability
Automatically creating and distributing detailed PDF reports

🎯 Key Features

Real-Time Data Extraction: Automatically searches ESPN Cricinfo and Cricbuzz for latest player statistics
Multi-AI Analysis: Utilizes GPT-4, Gemini Pro, and Gemini 2.5 Pro for comprehensive evaluation
International Cricket Focus: Excludes franchise leagues (IPL, BBL, CPL, PSL, BPL) to focus on ICC formats
Comprehensive Player Metrics: Analyzes batting average, bowling economy, injury status, form, and more
Automated Reporting: Generates Google Docs reports and emails them as PDFs
Match-Specific Analysis: Evaluates player suitability for specific opponents, locations, and match types

🏗️ Architecture<br>
Workflow Components<br>
Webhook (Input) <br>
    ↓<br>
Edit Fields (Data Formatting)<br>
    ↓<br>
HTTP Request (Google Custom Search API)<br>
    ↓<br>
Code Node (URL Extraction)<br>
    ↓<br>
┌──────────────────┬──────────────────┐
│                  │                  │
Information        AI Agent2          AI Agent1
Extractor          (OpenAI/Gemini)    (OpenAI/Gemini)<br>
│                  │                  │
└──────────────────┴──────────────────┘
                   ↓<br>
              AI Agent3 (Data Aggregation)<br>
                   ↓<br>
              AI Agent (Final Analysis)<br>
                   ↓<br>
         Create Google Document<br>
                   ↓<br>
         Update Document with Report<br>
                   ↓<br>
         Download as PDF<br>
                   ↓<br>
         Send via Gmail<br><br>
🚀 Getting Started<br>
Prerequisites<br>

n8n (self-hosted or cloud)<br>
API Keys:<br>

Google Custom Search API<br>
OpenAI API<br>
Google Gemini (PaLM) API<br>
Gmail OAuth2<br>
Google Docs API<br>
Google Drive API<br><br>



Configure API Credentials<br>

Set up credentials for each service in n8n:<br>

Google Custom Search API<br>
OpenAI API<br>
Google Gemini API<br>
Gmail OAuth2<br>
Google Docs OAuth2<br>
Google Drive OAuth2<br><br>




Update Configuration<br>

Modify the Google Drive folder ID in "Create a document" node<br>
Update email recipient in "Send a message" node<br><br>



📝 Usage<br>
Input Parameters<br>
Send a POST request to the webhook endpoint with the following JSON payload:<br>
json{<br>
  "playerName": "Dushmantha Chameera",<br>
  "matchType": "ODI",<br>
  "sericeType": "Away",<br>
  "compititor": "New Zealand",<br>
  "location": "England"<br>
}<br><br>
Parameters Explained<br>
ParameterDescriptionExampleplayerNameFull name of the cricket player"Virat Kohli"matchTypeFormat of the match"ODI", "Test", "T20I"sericeTypeHome or Away series"Home", "Away"compititorOpposing team"Australia", "England"locationMatch venue/country"India", "Australia"
Output<br>
The system generates:<br>

Google Document: Detailed analytical report<br>
PDF Report: Converted from Google Docs<br>
Email: Automatically sent to configured recipient with PDF attachment<br><br>

Sample Report Structure<br>
Executive Decision<br>
├── Player Suitability Assessment<br>
├── Deep-Dive Analysis<br>
│   ├── Venue Conditions Analysis<br>
│   ├── Opposition Assessment<br>
│   └── Player Skills Evaluation<br>
├── Historical Performance Data<br>
├── Risk Assessment<br>
└── Final Verdict & Recommendation<br><br>
🔧 Customization<br>
Modifying Search Parameters<br>
Edit the HTTP Request node to adjust search criteria:<br>
javascripthttps://www.googleapis.com/customsearch/v1?key=YOUR_API_KEY&cx=YOUR_CX&q={{ encodeURIComponent($('Webhook').item.json.body['playerName '] + ' international cricket stats career records injuries form ICC ODI Test T20I site:espncricinfo.com OR site:cricbuzz.com -IPL -BBL -CPL -PSL -BPL') }}&num=10&dateRestrict=y2<br>
Adjusting AI Models<br>
The workflow uses multiple AI models for redundancy and comprehensive analysis:<br>

AI Agent1: OpenAI GPT-4o + Google Gemini<br>
AI Agent2: Google Gemini + OpenAI GPT-4o<br>
AI Agent3: Google Gemini 2.5 Pro + OpenAI GPT-4o<br>
AI Agent (Final): Google Gemini 2.5 Pro + OpenAI GPT-4o<br>

You can modify model selection in each AI Agent node's settings.<br><br>
📊 Analysis Metrics<br>
The system evaluates players across multiple dimensions:<br>
Performance Metrics<br>

Last matches batting average<br>
Last matches bowling economy<br>
Strike rate<br>
Fielding accuracy score<br><br>

Physical & Mental Attributes<br>

Injury status and history<br>
Training attendance<br>
Training intensity score<br>
Estimated IQ level<br><br>

Career Statistics<br>

Number of matches in all ICC formats (Test, ODI, T20I)<br>
Best performances against specific teams<br>
Performance in similar conditions<br>
Recent form analysis<br><br>

Strategic Factors<br>

Suitability for match conditions<br>
Historical performance vs opponent<br>
Risk assessment<br>
Tactical value<br><br>

🛠️ Troubleshooting<br>
Common Issues<br>
Issue: Workflow fails at HTTP Request node<br>

Solution: Verify Google Custom Search API key and Custom Search Engine ID<br>

Issue: AI Agents return incomplete data<br>

Solution: Check API rate limits and ensure sufficient credits<br>

Issue: PDF not attached to email<br>

Solution: Verify Google Drive permissions and file conversion settings<br>

Issue: URLs not extracting properly<br>

Solution: Check if search results contain valid URLs from specified sites<br><br>



📊 System Requirements<br>

n8n Version: 1.0.0 or higher<br>
Node.js: 18.x or higher<br>
Memory: Minimum 2GB RAM<br>
Storage: 1GB for logs and cache<br><br>

🎓 Documentation<br>
For detailed documentation on each component:<br>

n8n Documentation<br>
OpenAI API Documentation<br>
Google Gemini Documentation<br>
Google Custom Search API<br>
Google Custom Search API<br><br>


Made with ❤️ for Cricket Analytics
