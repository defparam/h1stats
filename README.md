# h1stats - h1 Program Stats Scraper
This python3 script will call out to HackerOne's graphql API and scrape all currently active programs for information and stats on every h1 program. All programs and their stats get tabulated into a generated CSV file. From here you can compare and contrast all program stats to pick high fidelity targets. Furthermore, you can supply your h1 session cookie to the script to also compile in all private programs to the CSV.

## Thanks
@pmnh -- for maintaining a compatability fork

# Data Collected:
 - Program Name
 - Program URL
 - Program Type (Public or Private)
 - Clear Program (Yes/No)
 - Offers Bounties (Yes/No)
 - Bounty Splitting (Yes/No)
 - Max Critical (USD)
 - Max High (USD)
 - Max Medium (USD)
 - Max Low (USD)
 - Average Bounty Max (USD)
 - Average Bounty Min (USD)
 - Top Bounty Max (USD)
 - Top Bounty Min (USD)
 - Resolved Reports
 - Reports Received in 90 Days
 - Total Bounties Paid (USD)
 - Total Bounties Paid in 90 Days (USD)
 - Avg Time to First Response (Hours)
 - Avg Time to Triage (Hours)
 - Avg Time to Bounty (Hours)
 - Avg Time to Resolution (Hours)
 - Progam Age (Months)
 - Days Since Last Report

## Install
Due to HackerOne API changes requiring a CSRF token to make GraphQL API requests, this tool now uses BeautifulSoup 4 to parse the HTML and retrieve the CSRF token. To install this dependency:

```
pip install -r requirements.txt
```

## Usage
normal usage (public programs): (Note: As of the end of 2022, this no longer works - you _must_ supply a valid token of an authenticated session)
**python3 h1stats**

authenticated usage (public and private programs):
**python3 h1stats [\<Your HackerOne __Host-session Token\>]**



## WARNING (Authenticated Usage)
**THIS SCRIPT HANDLES YOUR H1 SESSION TOKEN WHICH CONTAINS YOUR HACKERONE PRIVATE DATA AND THE PRIVATE DATA OF YOUR HACKERONE PROGRAMS. BECAREFUL WHEN HANDLING THIS TOKEN. THE AUTHORS ARE NOT LIABLE FOR ANY MISUSE OF THIS SCRIPT OR YOUR HACKERONE SESSION TOKEN. PLEASE USE AT YOUR OWN RISK. DO NOT PUBLISH ANY CSVs WITH HACKERONE PRIVATE PROGRAM DATA.**

For authenticated usage It is suggested that you assign your token into a variable once using `export` and pushing the env variable into the script's argument list (as shown in the examples).


## Examples
Authenticated Flow (Public and Private):
```
bash> export H1CRED="JGH92kd9...b5e" # HackerOne session cookie
bash> python3 h1stats $H1CRED
  _     _ ____  _        _
 | |__ / / ___|| |_ __ _| |_ ___
 | '_ \| \___ \| __/ _` | __/ __|
 | | | | |___) | || (_| | |_\__ \
 |_| |_|_|____/ \__\__,_|\__|___/

                      defparam

[+] Using specified session cookie
[+] Collecting public and private data...
[+] Please wait... (this may take several minutes)
[+] Collecting... (400 programs)
[+] Wrote all data to: h1stats-PRIVATE-2021-4-24.csv
[+] Warning: this data contains private information under NDA, do not publish!
[+] Done!
```


