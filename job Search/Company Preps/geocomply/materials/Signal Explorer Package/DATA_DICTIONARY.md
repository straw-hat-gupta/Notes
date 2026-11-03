# Signal Explorer sandbox: data dictionary

**SYNTHETIC.** Every person, account, device, network and number in these files is invented for an interview exercise. Two fictional operators, one week (Mon Oct 5 to Sun Oct 11, 2026).

## Files

| File | One row is | Rows |
| --- | --- | --- |
| `transactions.csv` | One location check | 9,120 |
| `users.csv` | One account at one operator | 605 |
| `devices.csv` | One device, as our software identifies it | 629 |
| `operators.csv` | One operator | 2 |
| `operator_flagged_accounts.csv` | One account an operator has flagged or suspended and sent to us | 83 |

## transactions.csv

| Column | Meaning |
| --- | --- |
| transaction_id | Unique check ID |
| datetime_utc | When the check happened, in UTC. Ohio is UTC-4 in October (6 pm in Ohio = 22:00 UTC) |
| operator | Which operator called the check |
| user_id | The operator's ID for the account |
| device_id | The device, as our software identifies it. iPhones show an uppercase ID, Android phones a 16-character code, browsers a long code joined by a dash |
| status | `Pass`, or the reason the check failed |
| solution, solution_version | Which of our products ran the check: the iOS app, the Android app, or the Web SDK in a browser |
| device_model, os | Phone or computer model and operating system |
| ip_address, isp | The internet address and the company providing it |
| connection_type | `static` (home or office internet) or `mobile` (phone network) |
| data_type | Which signals were available: GPS, Wi-Fi, Cellular, IP. More signals means a more precise location |
| trigger | What made the operator ask for a check: `app_opened`, `app_reopened`, `periodic_check`, `login`, `wager`, and for GreenTeam `view_records` and `withdrawal_request` (see operators.csv) |
| wifi_ssid | The Wi-Fi network name, if connected |
| wifi_bssid | The ID of the specific Wi-Fi router or access point. One network name can have many access points |
| is_trusted, trusted_reason | Our confidence flag. A check can pass and still be marked not trusted. Reasons: `Trusted`, `Low location confidence`, `Low device confidence` |
| lat, lon, city, state | Where the check placed the person |
| location_accuracy_m | How precise the location was, in metres |
| action, amount_usd | GreenTeam only: what the member was doing, and the amount for withdrawals |

## Status values

| Status | Meaning |
| --- | --- |
| Pass | Location confirmed inside the permitted area |
| Too Close to Border | Too close to the state line to confirm, given how precise the location was |
| Out of Jurisdiction | Confirmed outside the permitted area |
| Insufficient Location Data | Not enough signal to place the person |
| Location Services Disabled | The person has location turned off |
| VPN/Proxy Detected | The connection is being routed through a VPN or proxy |
| Remote Desktop Detected | Someone is controlling the device remotely |
| Mock Location Detected | An app or setting is faking the GPS position |
| Shared Device Limit | More accounts on one device than the operator allows |
| Impossible Travel | The device moved further than is physically possible in the time between checks |

## operator_flagged_accounts.csv

What operators send us when they suspend or review accounts. The labels are the operator's, and describe the reason they acted on that account.
