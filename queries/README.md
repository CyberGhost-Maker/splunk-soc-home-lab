
# SPL Query Documentation

## 1. Authentication Event Overview

**Purpose:** Summarize successful and failed authentication events.

**SPL file:** `01_event_overview.spl`

**Expected result:** Two event categories with counts of 10 successes and 12 failures.

**SOC relevance:** Establishes a basic view of authentication activity.

## 2. Failed Login Analysis

**Purpose:** Count failed attempts by user and source IP.

**SPL file:** `02_failed_logins.spl`

**SOC relevance:** Helps prioritize accounts and sources for investigation.

## 3. Brute-Force Threshold Detection

**Purpose:** Flag three or more failed attempts for a user/source IP combination in a five-minute time bin.

**SPL file:** `03_bruteforce_detection.spl`

**SOC relevance:** Identifies repeated failures that may warrant investigation.

## 4. Failures and Successful Logins

**Purpose:** Find user/source IP combinations with at least three failures and at least one success.

**SPL file:** `04_success_after_failures.spl`

**SOC relevance:** Highlights combinations for timeline review.

**Limitation:** This aggregation does not prove that the successful login occurred after the failures. Review raw event timestamps to establish order.

**Demonstrated Skills** 

Splunk SPL searching and filtering.

Authentication event analysis.

Aggregation and time-window analysis.

Basic detection logic.

Security investigation documentation


