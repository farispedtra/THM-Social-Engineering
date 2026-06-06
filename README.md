## Assignment Details

| Field | Info |
|-------|------|
| **Subject** | Social Engineering |
| **Type** | TryHackMe Writeup |
| **Rooms Completed** | 2 |
| **Platform** | [TryHackMe](https://tryhackme.com) |

---

## Rooms Completed

| # | Room | Link | Status |
|---|------|------|--------|
| 1 | Phishing Emails in Action | [tryhackme.com/room/phishingemails2rytmuv](https://tryhackme.com/room/phishingemails2rytmuv) | Completed |
| 2 | The Phishing Pond | [tryhackme.com/room/phishingpond](https://tryhackme.com/room/phishingpond) | Completed |

---

## Room 1 — Phishing Emails in Action

> Learn the different indicators of phishing attempts by examining actual phishing emails.

### Answer Summary

| Task | Question | Answer |
|------|----------|--------|
| Task 1 | Read the above | No answer needed |
| Task 2 | What phrase does the gibberish sender email start with? | `noreply` |
| Task 3 | What is the root domain for each URL? Defang the URL. | `devret[.]xyz` |
| Task 4 | What other company name was used in this phishing email? | `citrix` |
| Task 5 | What should users do with suspicious Netflix emails? | `forward the message to phishing@netflix.com` |
| Task 6.1 | What does BCC mean? | `Blind Carbon Copy` |
| Task 6.2 | What technique was used to persuade the victim to act swiftly? | `Urgency` |
| Task 7 | What is the name of the executable the Excel attachment attempts to run? | `regasms.exe` |
| Task 8 | Read the above | No answer needed |

### Task Analysis

<details>
<summary><b>Task 2 — Cancel Your PayPal Order</b></summary>

This email impersonates a PayPal notification. The display name appears legitimate, but the actual sender address starts with `noreply` followed by random gibberish characters — a common tactic to bypass basic spam filters.

**Red Flag:** Sender email address does not match PayPal's legitimate domain.

</details>

<details>
<summary><b>Task 3 — Track Your Order</b></summary>

The email contains a URL that looks trustworthy at a glance but redirects to a malicious domain, `devret.xyz`. During analysis, the URL is defanged (`devret[.]xyz`) to prevent accidental clicks.

**Red Flag:** Third-party domain with no relation to the company being impersonated.

</details>

<details>
<summary><b>Task 4 — Select Your Email Provider</b></summary>

This email incorporates logos and names of well-known companies — OneDrive, Adobe, and Citrix — to appear credible. This technique is known as **brand impersonation**, exploiting the trust users place in recognizable brands.

**Red Flag:** Multiple unrelated company logos used together without a clear legitimate reason.

</details>

<details>
<summary><b>Task 5 — Netflix Payment Phishing</b></summary>

The email requests payment information and claims to be from Netflix. Netflix provides an official reporting channel at `phishing@netflix.com` for users who receive suspicious emails.

**Red Flag:** Request to update payment information via a link embedded in an email.

</details>

<details>
<summary><b>Task 6 — Your Recent Purchase</b></summary>

The attacker applies an **urgency** technique to pressure the victim into acting quickly without thinking critically. BCC is used to conceal the full recipient list, which is typical in mass phishing campaigns.

**Red Flag:** Urgent language demanding immediate action (e.g., "act within 24 hours").

</details>

<details>
<summary><b>Task 7 — Malicious Excel Attachment</b></summary>

A seemingly legitimate Excel attachment contains a macro that attempts to execute `regasms.exe` on the victim's machine. This is a classic **malicious macro attack**, widely used in phishing campaigns targeting corporate environments.

**Red Flag:** Any attachment that prompts the user to enable macros.

</details>

---

## Room 2 — The Phishing Pond

> Catch the phish before the phish catches you.

**Format:** 10 realistic email scenarios | 30 seconds per email | 3 lives

### Result

<div align="center">

| Score | Lives Remaining | Time |
|:-----:|:---------------:|:----:|
| 10 / 10 | 3 | 2m 14s |

**Flag: `THM{i_phish_you_not}`**

</div>

---

### Level Analysis

#### Level 1 — PHISHING

| Field | Detail |
|-------|--------|
| **From** | CEO Office `<ceo@tryhackme-support.com>` |
| **To** | Finance Team `<finance@tryhackme.com>` |
| **Subject** | Urgent wire transfer — confidential |
| **Technique** | CEO Fraud / Business Email Compromise (BEC) |

The email requests an immediate wire transfer of $25,000 for a confidential acquisition, impersonating the company's CEO.

> **Red Flag:** Sender domain `tryhackme-support.com` does not match the legitimate domain `tryhackme.com`.

---

#### Level 2 — NOT PHISHING

| Field | Detail |
|-------|--------|
| **From** | Jane Doe `<jane.doe@tryhackme.com>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | Lunch Plans for Tomorrow |

A casual lunch invitation between colleagues. The domain is legitimate, there are no links or attachments, and the content raises no concern.

---

#### Level 3 — NOT PHISHING

| Field | Detail |
|-------|--------|
| **From** | IT Notices `<notices@tryhackme.com>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | Planned maintenance this weekend |

A routine IT maintenance notification. Sent from a legitimate internal domain with no suspicious links or attachments.

---

#### Level 4 — NOT PHISHING

| Field | Detail |
|-------|--------|
| **From** | HR Department `<hr@tryhackme.com>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | Reminder: Annual HR Policy Review Meeting |

A standard internal HR reminder. Legitimate domain, no indicators of phishing.

---

#### Level 5 — PHISHING

| Field | Detail |
|-------|--------|
| **From** | Invoice Team `<invoices@vendor-example.com>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | Invoice_9392.zip (password: 1234) |
| **Technique** | Malicious Macro Attack |

The email delivers a password-protected ZIP file containing a Word document that instructs the recipient to enable macros to view the invoice.

> **Red Flag:** Password-protected ZIP combined with a request to enable macros is a high-confidence phishing indicator.

---

#### Level 6 — PHISHING

| Field | Detail |
|-------|--------|
| **From** | Customer Support `<support@survey-feedback.example>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | We value your feedback — quick survey |
| **Technique** | Malicious URL |

The email directs the recipient to click `http://survey-feedback.shadylink.fake` to complete a survey.

> **Red Flag:** Sender domain and embedded URL have no association with any legitimate organization.

---

#### Level 7 — PHISHING

| Field | Detail |
|-------|--------|
| **From** | Rewards `<offers@bigprize.example.net>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | You've been selected! Claim your $2,000 refund now |
| **Technique** | Financial Phishing |

The email claims the recipient has been randomly selected for a $2,000 refund and requests their full name, address, and bank details to process the payment.

> **Red Flag:** Unsolicited prize combined with a request for banking information.

---

#### Level 8 — PHISHING

| Field | Detail |
|-------|--------|
| **From** | Social Updates `<no-reply@social.example.com>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | Reset your password to secure your account |
| **Technique** | Credential Harvesting |

The email claims suspicious activity was detected and instructs the recipient to reset their password via `https://social.example-security.com/reset`.

> **Red Flag:** The link domain (`example-security.com`) differs from the sender domain (`social.example.com`).

---

#### Level 9 — PHISHING

| Field | Detail |
|-------|--------|
| **From** | Accounts `<accounts@vendor-payments.com>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | Invoice INV-2025-334 (Action required) |
| **Technique** | Payment Portal Spoofing |

The email requests payment for an invoice via `https://pay.vendor-payments-secure.com/invoice/INV-2025-334`.

> **Red Flag:** `vendor-payments-secure.com` is not the same as `vendor-payments.com` — an extra subdomain segment is used to deceive at a glance.

---

#### Level 10 — PHISHING

| Field | Detail |
|-------|--------|
| **From** | HR Team `<hr@external-hr-provider.com>` |
| **To** | Peter Smith `<peter.smith@tryhackme.com>` |
| **Subject** | Updated benefits package (open to review) |
| **Technique** | Malicious Document |

The email instructs the recipient to open an attached benefits document and enable macros if it appears blank.

> **Red Flag:** No legitimate HR document should ever require macros to be enabled.

---

## Phishing Techniques Identified

| Technique | Description | Found In |
|-----------|-------------|----------|
| CEO Fraud / BEC | Impersonating an executive to authorize a wire transfer | Level 1 |
| Domain Spoofing | Using a look-alike domain to deceive the recipient | Level 1, 8, 9 |
| Brand Impersonation | Borrowing logos and names of trusted companies | Task 4 |
| Urgency | Pressuring the victim to act without thinking | Task 6 |
| Malicious Macros | Delivering malware through macro-enabled documents | Level 5, 10 |
| Credential Harvesting | Redirecting victims to fake login or reset pages | Level 8 |
| Financial Phishing | Soliciting banking or personal financial details | Level 7 |
| Payment Portal Spoofing | Mimicking a legitimate payment domain | Level 9 |
| Malicious URL | Embedding links to attacker-controlled domains | Level 6, Task 3 |
| Gibberish Sender Address | Using a randomized sender address to bypass filters | Task 2 |

