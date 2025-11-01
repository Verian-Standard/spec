<p align="center">
  <br />
  <h1 align="center">Verian Specification</h1>
  <p align="center">
    The Standard for Verifiable AI Certainty
  </p>
  <p align="center">
    <a href="#"><img src="https://img.shields.io/badge/status-pre--alpha-orange" alt="Status"></a>
    <a href="#"><img src="https://img.shields.io/badge/specification-draft-blue" alt="Specification"></a>
    <a href="#license--intellectual-property"><img src="https://img.shields.io/badge/license-Multiple-lightgrey" alt="License"></a>
    <a href="https://verian.org"><img src="https://img.shields.io/badge/website-verian.org-brightgreen" alt="Website"></a>
  </p>
</p>

---

This repository is the official home for the Verian Standard specification. It contains the technical documentation, core concepts, and protocols for implementing Verifiable AI.

## The Problem: The Crisis of Trust in AI

Generative AI holds immense promise, but its utility is critically undermined by a single, pervasive flaw: **hallucination**. An AI that confidently presents unverified or fabricated information is not just unhelpful; it's a liability. As AI becomes more integrated into high-stakes domains like healthcare, finance, and law, an unverified answer is an unacceptable risk that erodes trust and hinders adoption.

## The Solution: The Verian Standard

**Verian** is an open standard and verification protocol designed to ground generative AI in objective reality. Instead of treating an AI's output as an opaque, probabilistic black box, Verian provides a framework for making AI claims **transparent, auditable, and deterministically verifiable** against source documents.

## The Three Concepts of Verification

The Verian Standard is built on a foundation of three core concepts, which are applied in sequence to any AI-generated claim.

### 1. Does it exist? (Existence Verification)
This is the first and most fundamental check, designed to combat blatant hallucinations. The protocol uses deterministic tools (like literal text search) to answer a simple question: can the source for this claim be found in the provided content? This provides **Verifiable Certainty**.

### 2. Is the prediction in good faith? (Contextual Integrity)
A claim can be factually present but contextually wrong. This concept combats subtle hallucinations by analyzing the context of the verified information. For example, if a medical record from 10 years ago states a patient is "age 40," a good faith presentation would be "age 50," not "age 40." This ensures **Principled Context**.

### 3. Can the prediction be interpreted in bad faith? (Adversarial Resilience)
This final check addresses ambiguity that could be exploited through error or malice. For example, a date like "12/01/00" can be interpreted differently in the US vs. Europe. The protocol flags these ambiguities, which are then resolved and noted for user transparency. This provides an additional layer of **Principled Context** and robustness.

## How It Works: Visualizing Trust

The process is simple: an AI model generates text with a `<cite>` tag containing source metadata. The Verian Verification Protocol (VVP) then independently validates this claim against the source. The VVP corrects the text if necessary and renders the final, truthful statement with a styled citation marker that transparently indicates the verification status.

### Rendered User Experience:

The final output is always clean and correct. The citation's appearance provides at-a-glance confidence that every claim is verified, while transparently noting the journey.

> According to the file, the patient was admitted on **December 1, 2000<span style="color:#005595;">[1</span><span style="color:#B366B3;">*</span><span style="color:#005595;">]</span>**. The patient, now **aged 50<span style="color:#005595;">[2</span><span style="color:#D9A000;">*</span><span style="color:#005595;">]</span>**, originally presented with acute pharyngitis. The final invoice was **$450.00<span style="color:#005595;">[3]</span>**.

Progressive disclosure on hover or click reveals the details of any corrections or ambiguities.

*   <strong>[3] Blue</strong>: **Verified.** The claim was a direct, contextually-correct match with the source.
*   <strong>[2*] Blue, with Amber Asterisk</strong>: **Corrected.** The claim's source was found, but the VVP updated the text for contextual accuracy (e.g., calculated a current age). The asterisk invites the user to investigate.
*   <strong>[1*] Blue, with Purple Asterisk</strong>: **Ambiguity Resolved.** The source was ambiguous (e.g., unclear date format), and the VVP resolved it based on established rules. The asterisk invites the user to investigate.

## The Verian Trust Graph: A Chain of Verification

The power of Verian lies in its strict architectural separation between the **probabilistic act of generation** and the **deterministic act of verification**. The LLM's output is never blindly trusted; it is merely a proposal that must be rigorously validated by an independent, deterministic process.


**Phase 1: Ground Truth Creation (Deterministic)**
The process begins with trusted, deterministic tools. Any source document (PDF, image, etc.) is converted into a structured, searchable text format. This output is the immutable **Ground Truth**, the single source of fact for the entire system.

**Phase 2: Claim Generation (Probabilistic & Untrusted)**
The Ground Truth is fed to the LLM. The LLM's only job is to perform a creative task: generate a human-readable summary and embed the raw `<cite>` tags pointing to what it *believes* is the source. Its output is always treated as an **untrusted claim**.

**Phase 3: Verification & Reconciliation (Deterministic & Trusted)**
This is the heart of the standard. The **Verian Verification Protocol (VVP)** acts as an independent reconciliation engine. It receives two critical inputs: the **untrusted claim** from the LLM and the original **Ground Truth** from Phase 1. The VVP deterministically compares the two, applies the Three Concepts of Verification, corrects any errors or contextual inaccuracies, and resolves ambiguities.

**Phase 4: Final Presentation**
The text shown to the end user is **always the output of the trusted VVP**, never the raw output from the LLM. The VVP renders the final, corrected statement with the appropriately styled citation marker, ensuring the user only ever interacts with verified information.

## 🛡️ Inherent Resistance to Prompt Injection

This "chain of verification" architecture also provides inherent resilience against **prompt injection attacks.** An attack might trick an LLM into generating a malicious claim. However, the VVP acts as a safety checkpoint. It will independently validate the LLM's claim against the Ground Truth. When the malicious claim inevitably fails this deterministic check, the VVP will either flag it as an error or, better yet, replace it with the correct information. The attack is not only blocked; it's corrected.

---

## 📜 Project Status

This repository and the Verian Standard are in a **pre-alpha, foundational stage.**

*   ✅ The core concepts and technical approach have been defined.
*   📝 The formal specification is in an early draft stage.
*   ⚖️ The governance and intellectual property framework has been established (see below).
*   🌱 This GitHub repository is the designated public home for the standard's future development.

## 🏛️ Governance and Participation

The Verian Standard is developed within the **Verian Special Interest Group (SIG)**, a program managed and operated by **Verian SIG, Inc.**

The SIG's technical work is driven by its members in **Technical Working Groups (TWGs)**. The foundational intellectual property that enables the standard is owned by **FileLasso, Inc.** and is licensed to the SIG.

This structure provides a stable, long-term foundation for the standard while allowing for a member-driven, collaborative process for its technical evolution.

To learn more about becoming a member and participating in the development of the standard, please visit our main website.

➡️ **[Learn About Membership at verian.org](https://verian.org)**

---

## 🚀 Specification Roadmap

Our goal is to evolve this specification into the universal standard for reliable AI.

*   **Phase 1 (Current):** Form the founding members of the Verian SIG to ratify the charter and IPR policy. Refine the v0.1 draft specification.
*   **Phase 2:** Establish initial Technical Working Groups (TWGs) to expand the protocol. Publish the v1.0 specification for public comment.
*   **Phase 3:** Release an open-source reference implementation of the Verian Verification Protocol (VVP). Launch the official "Verian Certified" qualification program.
*   **Phase 4:** Expand the standard to new data types and use cases, driven by member-led working groups.

---

## ⚖️ License & Intellectual Property

The Verian ecosystem operates under a multi-part IP framework. Participation in the SIG requires agreement with the Verian SIG IPR Policy.

### 1. Specification License
The documentation and formal specifications contained **within this repository** are made available under the **Apache 2.0 License**. This allows for broad public access, review, and discussion. See the `LICENSE` file for details.

### 2. Patent License
Implementation of the Verian Standard requires a license to essential patent claims.

*   **Ownership:** The technology essential to implementing the standard is covered by **pending patent applications** owned by **FileLasso, Inc.**
*   **License Grant:** A license to any resulting patents is granted to members of Verian SIG, Inc. on **Fair, Reasonable, and Non-Discriminatory (FRAND)** terms. This is a royalty-bearing license.

### 3. Trademark License
The **"Verian Verified"™** name and associated logos are trademarks of **FileLasso, Inc.** The right to use these marks on compliant products that have passed official qualification is a benefit granted to members under the terms of the SIG.

## Contact
For all inquiries regarding membership, licensing, and media, please visit **[verian.org](https://verian.org)**.
