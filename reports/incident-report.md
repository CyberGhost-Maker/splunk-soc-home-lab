# SOC Authentication Investigation Report

## 1. Project Overview

For this project, I used Splunk Enterprise to analyze authentication logs and look for login activity that could potentially be suspicious.

I created a sample dataset with 22 authentication events and uploaded it into Splunk. From there, I used SPL queries to look at successful and failed logins, identify accounts with repeated login failures, and check for patterns that could be worth investigating further.

I also built a dashboard to make the results easier to understand and monitor.

The main goal of this project was to get hands-on experience with Splunk and learn how security analysts use log data to investigate authentication activity.

## 2. What I Investigated

I focused on a few things during my investigation:

- The number of successful and failed login attempts.
- Which users had the most failed logins.
- Whether any users had multiple failed attempts within a short period.
- Whether the same user and source IP appeared in both failed and successful login events.

I used SPL queries to filter the data, count events, and identify patterns that might need further investigation.

## 3. What I Found

### Authentication Activity

The dataset contained 22 events in total:

- 12 failed login attempts.
- 10 successful login attempts.

This gave me a starting point for understanding the authentication activity in the dataset before looking more closely at individual accounts.

### Failed Login Attempts

When I broke down the failed logins by user, I found the following:

| User | Failed Login Attempts |
|---|---:|
| Alice | 5 |
| Bob | 3 |
| Carol | 3 |
| Erin | 1 |

Alice had the highest number of failed login attempts, with five. Bob and Carol each had three, while Erin had one.

In a real security environment, I would want to investigate why these attempts failed and whether the activity was normal for those accounts.

### Potential Brute-Force Activity

Next, I created a query to identify users with three or more failed login attempts within a five-minute window.

The results flagged Alice, Bob, and Carol.

Repeated login failures can sometimes indicate a brute-force attempt, where someone repeatedly tries different passwords to gain access to an account. However, failed logins can also happen for legitimate reasons, such as a user entering the wrong password several times.

Because this project uses sample data, I cannot confirm that an actual attack occurred. The results show how I can use Splunk to identify activity that may deserve a closer look.

### Failed and Successful Login Activity

I also created a query to find user and source IP combinations that had at least three failed logins and at least one successful login.

This helped me identify activity that could be useful to investigate further. However, the query does not confirm whether the successful login happened after the failed attempts.

To establish that, I would need to review the individual event timestamps and put the events in chronological order.

## 4. What I Would Do Next

If I were investigating these events in a real SOC environment, I would take a closer look at the following:

1. **Review the timeline:** Check whether any successful logins happened shortly after repeated failures.
2. **Investigate the source IPs:** Determine whether the login sources are expected for the users involved.
3. **Check for unusual activity:** Look for unexpected login times, unfamiliar devices, or unusual authentication methods.
4. **Review other logs:** Compare the authentication events with available endpoint or identity-provider logs to see whether there is additional evidence.
5. **Document the findings:** Record what I found and escalate any suspicious activity according to the organization's incident response procedures.

I would not assume that an account had been compromised based on failed login attempts alone. I would need more evidence before reaching that conclusion.

## 5. Limitations

One limitation of this project is that the dataset is synthetic, so the results do not represent a real security incident.

The brute-force detection rule also uses a basic threshold of three or more failures within five minutes. This is useful for learning how detection logic works, but it could flag legitimate activity or miss attacks that happen more slowly.

The analysis would be more useful in a real environment with additional log sources and more context about normal user behavior.

The IP addresses used in the dataset are reserved for documentation and example purposes.

## 6. What I Learned

This project gave me practical experience using Splunk Enterprise to work with authentication logs and investigate potentially suspicious activity.

I learned how to:

- Ingest a CSV dataset into Splunk.
- Write SPL queries to filter and analyze authentication events.
- Count failed logins by user and source IP.
- Use time-based grouping to identify repeated failures.
- Correlate failed and successful authentication events.
- Build a dashboard to display security-related findings.
- Document an investigation and explain the limitations of my results.

It also helped me understand that identifying a suspicious pattern is only the beginning of an investigation. More context and evidence are needed before deciding whether something is actually malicious.

## 7. Conclusion

Overall, this project helped me develop my understanding of how Splunk can be used for security monitoring and basic authentication investigations.

By working through the dataset, writing SPL queries, and building a dashboard, I was able to take raw authentication events and turn them into information that could help an analyst decide what to investigate next.

This home lab is a starting point for me to continue developing my cybersecurity skills, particularly in security operations, log analysis, and threat detection.