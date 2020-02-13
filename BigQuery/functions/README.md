# Functions

Some useful functions defined as [persistent UDFs](https://cloud.google.com/bigquery/docs/reference/standard-sql/data-definition-language#create_function_statement).

## Traffic / Channel Grouping

`channel_grouping.sql`

Create a channel grouping compatible with Google Analytics.

### arguments

- `source` (STRING) utm_source value in the landing page. In Ingestly log, column `campaign_source` corresponds.
- `medium` (STRING) utm_medium value in the landing page. In Ingestly log, column `campaign_medium` corresponds.
- `name` (STRING) utm_campaign value in the landing page. In Ingestly log, column `campaign_name` corresponds.
- `referrer` (STRING) referrer value in the landing page.

### Output

- channel group (STRING)

### Notes

#### Differneces from original Google Analytics specs:

- Ingestly cannot refer to Google Ads-Analytics link(gclid), so detailed Google-ads variables like adNetworkType are not available.
- If the referrer is of the same website, treat as 'Self' that means 'self referrals'. (You can specify the domain in line 2 of the function code)
