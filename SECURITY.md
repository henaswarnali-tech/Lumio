# Security Policy

## Reporting a Vulnerability

If you find a security vulnerability in LUMIO — in the app code, the certificate system, the authentication logic, or anywhere else — please do not open a public GitHub issue. A public issue exposes the vulnerability to everyone before it can be fixed.

**Instead, report it privately:**

Go to the [Security tab](https://github.com/henaswarnali-tech/Lumio/security) of this repository and use the **"Report a vulnerability"** button. This sends a private report directly to the maintainer.

If you cannot use that method, contact the maintainer directly through GitHub.

---

## What to Include in Your Report

The more specific you are, the faster we can understand and fix the problem:

- What the vulnerability is and where you found it
- What an attacker could do if they exploited it
- Steps to reproduce it, if you can
- Whether you have any suggested fix (optional — helpful if you do)

---

## What Happens Next

You'll receive an acknowledgement within 72 hours. We'll keep you updated as the issue is assessed and addressed. If the vulnerability is confirmed, we'll work on a fix and credit you in the release notes when it's resolved — unless you'd prefer to stay anonymous.

---

## Our Priority Areas

Given what LUMIO is and who uses it, we take the following especially seriously:

**Student privacy.** LUMIO collects no personal identifying information. No names, no email addresses, no phone numbers. Any vulnerability that could expose a student's device ID, progress data, or location is high severity.

**The private journal.** Lesson content occasionally offers students a private journal — stored only on-device, never synced. Any vulnerability that could access or expose journal data is critical.

**Certificate integrity.** Certificates are blockchain-verified. Any vulnerability that could allow a fake certificate to pass verification undermines the trust that makes them useful to the students who earned them.

**Child safety content.** The app contains sensitive content about body safety and abuse recognition designed for children. Any vulnerability that could alter or tamper with this content is critical.

---

## Scope

This policy covers the LUMIO application code and infrastructure managed in this repository.

It does not cover third-party services (Firebase, Blockcerts, IPFS) — report vulnerabilities in those services to their respective maintainers.

---

*github.com/henaswarnali-tech/Lumio*
