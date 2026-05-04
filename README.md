📌 Overview
This project automates the evaluation of the Pixelssuite Chat Translator, which converts chat-style Singlish (romanized informal Sinhala) into Sinhala script. Using Playwright for browser automation and openpyxl for Excel management, the script runs 50 negative test cases across 24 Singlish input types and records actual vs expected outputs.

✨ Features
FeatureDescription🤖 Browser AutomationPlaywright-powered Chrome automation📊 Smart Excel ParsingAuto-detects headers and columns🔄 Retry LogicConfigurable retries for slow networks💾 Progressive SavingSaves results after every N tests🧹 Overlay DismissalAuto-clicks cookie/consent popups🖥️ Headless SupportRun with or without browser GUI

🗂️ Project Structure
IT23242104/
├── test_automation.py        # Main Playwright automation script
├── IT23242104_Test_cases.xlsx # Excel file with 50 test cases
└── README.md                 # This file

⚙️ Prerequisites

Python 3.11 or 3.12
Google Chrome browser
pip package manager


🚀 Installation
Step 1 — Clone the repository
bashgit clone <your-repo-url>
cd IT23242104
Step 2 — Install Python dependencies
bashpip install playwright openpyxl
Step 3 — Install Playwright browser binaries
bashpython -m playwright install

▶️ Running the Tests
✅ Recommended Command (Interactive Testing)

python it23242104_test_automation.py --excel "D:\IT23242104\IT23242104_Test_cases.xlsx" --input-col "Input" --url "https://www.pixelssuite.com/chat-translator" --wait-ms 7000 --retry-wait-ms 1500 --retries 8 --type-delay-ms 50 --slow-mo-ms 200 --save-every 1


Or with line breaks for readability:

python it23242104_test_automation.py \
  --excel "D:\IT23242104\IT23242104_Test_cases.xlsx" \
  --input-col "Input" \
  --url "https://www.pixelssuite.com/chat-translator" \
  --wait-ms 7000 \
  --retry-wait-ms 1500 \
  --retries 8 \
  --type-delay-ms 50 \
  --slow-mo-ms 200 \
  --save-every 1
```

⚠️ Important: Close the Excel file before running the script!

🐢 Slow Connection
bashpython test_automation.py --excel "IT23242104_Test_cases.xlsx" --wait-ms 10000 --retry-wait-ms 2000 --retries 10
🔍 Manual Inspection Mode
bashpython test_automation.py --excel "IT23242104_Test_cases.xlsx" --slow-mo-ms 500 --keep-open

🧾 Command-Line Options
OptionDefaultDescription--excelIT23242104_Test_cases.xlsxPath to Excel test case file--sheet Test casesWorksheet name--input-colAuto-detectColumn name for Singlish input--expected-colAuto-detectColumn name for expected Sinhala output--actual-colAuto-detectColumn name for actual output--status-colAuto-detectColumn name for test status--urlhttps://www.pixelssuite.com/chat-translatorTarget application URL--wait-ms5000Wait time (ms) after input submission--retry-wait-ms1000Wait time (ms) between retries--retries8Number of retry attempts--type-delay-ms30Delay (ms) between keystrokes--slow-mo-ms0Slow-motion delay (ms) for all actions--timeout-ms60000Overall timeout (ms) for UI elements--save-every0Save after every N tests (0 = end only)--headlessfalseRun browser without GUI--keep-openfalseKeep browser open after tests

📋 Excel File Format
The script auto-detects headers. Your Excel file should contain these columns:
TC IDInput length typeInputExpected outputActual outputStatusSinglish input types coveredEvidence or rationaleNeg_0001Skoheda yanawa kiwwe oya?කොහෙද යනවා කිව්වේ ඔයා?(auto-filled)(auto-filled)Question formsRationale: ...
Input Length Categories
CodeRangeS≤ 30 charactersM31 – 299 charactersL300 – 450 characters
Status Values
StatusMeaningPASSActual output matches expectedFAILActual output does NOT match expectedCOLLECTEDOutput captured, no expected value providedUI ErrorElement not found or interaction failed

🧪 Singlish Input Types Covered
The 50 test cases cover all 24 Singlish input types from Appendix 1:

Question forms
Command forms
Greetings
Requests
Responses
Repeated Words
Inputs with Punctuation Marks
Romanization / Spelling Variants
Isolated English Word Insertions in Singlish
Multi-Word English Phrases in Singlish
English Digital Terms in Singlish
Platform/App Names in Singlish
English Abbreviations/Acronyms in Singlish
English Clipped Forms in Singlish
Place Names Embedded in Singlish
Person Names Embedded in Singlish
Inputs with Numbers and Numeric Suffixes
Inputs with Currency
Inputs with Time Formats
Inputs with Dates
Inputs with Unit of Measurements
Inputs with Slang and Casual Phrasing
Online Identifiers in Singlish
Inputs Containing Emojis


Each type has at least 2 test cases. Total: 50 Negative test cases (Neg_0001 – Neg_0050).


🔧 Troubleshooting
Excel file is locked
Make sure the Excel file is closed before running the script.
Output not captured

Increase --wait-ms (try 10000)
Increase --retries (try 10)
Check network connection

Chrome not found
bashpython -m playwright install chromium
Elements not found on page

Verify the URL is correct
Increase --timeout-ms (try 90000)


👤 Student Information
FieldDetailsNamePARINDA A V V SRegistration NumberIT23242104CourseIT3040 – ITPMAssignmentAssignment 1 – Option 1Target URLhttps://www.pixelssuite.com/chat-translator