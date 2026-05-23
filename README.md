# KQL-Toolbox
A collection of KQL queries and analytic rules I have used to reduce investigation times and proactively catch IOCs.

## External-Helpdesk-Impersonator
This analytic rule is designed to combat the recent uptick in external threat actors contacting internal users over Teams and impersonating Helpdesk to gain unauthorized access to machines. It is designed to be configured as a Near-Real-Time rule to detect the activity within five minutes of it being logged, and to expose the relevant entities so that an analyst can understand the scenario at a glance.

## Get-Email-From-URLClick
This query is for edge cases where you have already discovered the payload URL, but need to quickly find and purge the email of origin. It combats the fragmented nature of default Azure Sentinel tables by joining EmailUrlInfo and UrlClickEvents to identify where the URL came from. This is handy in environments where a third-party log normalization product is not currently in use.

## Malicious-IP-Activity-From-TI
This analytic rule explicitly leverages ThreatIntelligence to provide additional visibility on top of Sentinel's out-of-the-box alerts for IoCs in ThreatIntelligence. Useful for custom threat intelligence feeds that have been integrated into Sentinel to tailor specific alerts for IoCs relevant to your space.

## New-Inbox-Rule-Following-Login-From-New-IP
This rule addresses a very common TTP for Business Email Compromise, where a threat actor will gain access to a user's account and immediately set up an Inbox Rule to obfuscate their activity, usually by hiding incoming emails from the originally compromised external user or based on keywords like "hacked", "spam", "Do not open", etc. This enables the SOC team to detect and immediately remediate the compromised account prior to actions on objective.
