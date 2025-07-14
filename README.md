# Cross-Verified Humanity (CVH) System
Cryptoeconomic protocol for human verification in decentralized networks.

## About the System

**Overall System Goal:** To create a resilient subnet where miners are economically incentivized to ensure tasks are performed exclusively by humans (contributors) and to interact honestly with network participants, minimizing the impact of bots and abuse.

**I. Core Architecture and Participant Registration**

1.  **Dynamic Miner Registration:**
    *   To join the subnet, a miner must register.
    *   Registration requires a **burned registration fee**.
    *   **Fee Price is Dynamic:** It increases when many new miners are registering and decreases when few are registering.
    *   **Eviction Mechanism:** When a new miner wishes to register, the miner with the **lowest weight** ("the weakest") is ejected from the subnet.

2.  **Contributor Registration and Identification:**

    *    The miner sends a contributor registration request to the validator and provides the contributor with a subscription key.
    *    **Validators** register contributors.
    *   Upon registration, a contributor is assigned a unique identifier (conditional number) within the subnet.
    *   **"Humanity" Verification at Registration:** The validator **cannot and should not** directly verify a contributor's humanity at the moment of registration. Humanity confirmation is the result of the system's comprehensive operation.
    *   **Client Application (Optional Enhancement):**
        *   The miner sends a contributor registration request to the validator and provides the contributor with a subscription key.
        *   The contributor uses a dedicated client application (authenticated via MetaMask) to register directly with the validator using the provided key.
        *   **Purpose:** To enable the validator to receive task completion data **directly from the contributor** via the client for subsequent comparison with data received from the miner (dual verification).

**II. Roles and Participant Interaction**

1.  **Validators (Generation, Assignment, Accounting):**
    *   **Tasks:** Each validator **independently generates tasks**.
    *   **Distribution:** Each validator broadcasts **its own generated task to all miners** in the subnet simultaneously.
    *   **Contributor Assignment:** For **each** of its tasks and **each** miner, the validator **randomly** assigns **one (or several)** contributor from the network.
    *   **Accounting and Rating:** Validators track contributor work, calculate, and maintain their **ratings** based on task-solving success.
    *   **Consensus:** Validators operate as a group and achieve consensus on key network decisions (assignments, ratings, weights).

2.  **Miners (Platforms, Access, Reporting):**
    *   Receive tasks from validators and information about the contributor assigned to each task.
    *   Provide a platform/interface for the contributor to solve the assigned task.
    *   **Access Management Based on Rating:**
        *   Can view the rating of any contributor (data from validators).
        *   May **deny access** to the task for contributors with low ratings (if the contributor lacks "conditional immunity").
        *   **Are obligated to publicly announce** any access denial. The miner's total number of denials **affects its own weight**.
    *   **Reporting Obligation:** Send task responses obtained from contributors (both their own and others') to the validator.

3.  **Contributors (Task Solving):**
    *   Receive an assignment from the validator to solve a specific task for a specific miner.
    *   Access the assigned miner's platform and solve the task.
    *   Their reputation (rating) is formed by validators based on the success of solving tasks for *different* miners.

**III. Key "Humanity" Verification Mechanisms**

1.  **Cross-Interaction ("Foreign" Miners):**
    *   **Core Principle:** A contributor must solve tasks not only for "their own" miner (the one who registered them) but also for *randomly assigned* "foreign" miners.
    *   **Humanity Hypothesis:** A human can solve a task on any platform, including a "foreign" one. A bot configured for a specific platform will likely fail on an unfamiliar "foreign" miner's interface/protections.
    *   **Miner Motivation for Checks:** "Foreign" miners are incentivized to implement humanity checks (e.g., CAPTCHAs) on their platforms to filter out bots and protect their reputation/weight.
    *   **Dual Motivation for Access:** It is advantageous for a miner to allow a foreign contributor access to solve a task, as the miner gains weight for the **total number of correctly solved tasks** on its platform (including those by foreign contributors). Unjustified denial reduces its weight.

**IV. Economic Incentives and Sanctions for Miners**

The system creates interdependence between a miner and its contributors and penalizes dishonest behavior:

1.  **Impact of Contributor Reputation on Miner Weight:**
    *   If contributors registered through the miner's key (its "pool") successfully solve tasks (both their own and foreign ones), the miner gains **additional weight** due to the high rating of its contributors.
    *   If its contributors perform poorly (low rating), the miner **does not gain** this additional weight.

2.  **Sanctions for Response Manipulation:**
    *   **Concealment/Distortion of Foreign Contributor Responses:**
        *   If a miner sends the validator only *correct* responses from *its own* contributors, and does not send or distorts responses from *foreign* contributors:
        *   It will receive **less weight** because the total number of *correct* responses it sends will be lower than that of honest miners.
        *   An **additional small weight reduction** is imposed for the act of not sending/distorting foreign contributor responses.

3.  **Sanctions for Sabotaging Foreign Tasks:**
    *   **Contributors Evading Solving Foreign Tasks:**
        *   If a miner's contributors **deliberately fail to solve** or **solve poorly** tasks assigned to them on *foreign* miners:
        *   These contributors **lose rating** (because they are not solving tasks).
        *   The miner to whom these contributors are linked automatically receives **less weight** due to the declining rating of *its own* contributors.
        *   An **additional small weight reduction** is imposed on the miner itself because *its* contributors are not solving foreign tasks.

**V. Protection Against Abuse and Attacks**

1.  **Sybil Attack (Mass Bot Registration):**
    *   **Problem:** An attacker might attempt to register numerous bot-contributors.
    *   **Protection Measures:**
        *   **Burned Fee per Contributor Registration:** Each registration requires a fee payment that is burned.
        *   **"Seeding" Trust / Initial Limitations:** New contributors are subject to limits on the number of tasks they can solve or the rewards they can earn until they achieve a minimum rating based on data from *different* miners.

2.  **"False Humanity" and "False Bot Activity":**
    *   **Problem:** AI bots could become sophisticated enough to bypass checks and outperform incompetent humans in efficiency.
    *   **System Stance:** If an AI bot objectively performs tasks better than a human, this is considered an acceptable outcome ("this is also not bad").
    *   **Support for Human Contributors:** Training platforms ("sandboxes") and potential "immunity" mechanisms are provided for humans to gain experience without the risk of rapid ejection.

3.  **Managing Contributor Transfers:**
    *   **Rating Preservation:** A contributor's rating **does not burn** if their "home" miner is ejected from the subnet. The rating is preserved thanks to identification through validators.
    *   **Re-registration with a New Miner:**
        *   To attach to a new miner, the contributor requires re-registration through a validator.
        *   **Dynamic Re-registration Fee:** The re-registration cost **is tied to the contributor's rating** (e.g., higher rating could mean higher or lower cost, depending on the model).
        *   **"Cooling-off" Mechanism:**
            *   A **delay** (e.g., 12-24 hours) is enforced between the contributor detaching from the old miner and the possibility of re-registration with a new miner.
            *   The **frequency** of re-registrations is limited (e.g., no more than 1-2 times per week).
            *   **Goal:** To complicate schemes for instantly transferring contributors between miners for manipulation purposes.

**VI. Rating and Weight Management**

1.  **Contributor Rating Calculation:**
    *   **Sole Prerogative of Validators:** Only validators calculate and update contributor ratings based on received task completion data.
    *   **Role of Miners:** Miners merely relay contributor responses to validators; they **do not assign scores or ratings** themselves.

2.  **Miner Weight Allocation:**
    *   **Sole Prerogative of Validators:** Validators calculate and assign weight (influence, reward) to each miner based on:
        *   The quantity and correctness of responses sent by the miner (including responses from foreign contributors).
        *   The rating of contributors registered via the miner's key.
        *   Instances of unjustified denial of access to contributors.
        *   Instances of not sending/distorting foreign contributor responses.
        *   Instances of *its* contributors evading solving foreign tasks.

**Final System Effect:**

The complex interaction of the described mechanisms (dynamic registration, cross-task assignment, economic incentives and sanctions, attack protection, reputation management) creates powerful **economic and reputational incentives** for miners. Miners are compelled to:

1.  Carefully select and ensure the *humanity* of their contributors.
2.  Honestly provide access to *foreign* contributors.
3.  Diligently relay *all* responses (from their own and foreign contributors) to validators.
4.  Encourage their contributors to successfully solve tasks *on all platforms*.

Thus, the system achieves its primary goal: ensuring network tasks are performed by real humans by creating an environment where dishonest or inefficient behavior is economically disadvantageous.


## [Validator-Relayed Interaction Audit Architecture](Validator-Relayed_Interaction_Audit_Architecture.md)
*This document specifies the mechanisms for detecting, proving, and attributing fault in adversarial network interactions (ignored connections, task/response manipulation) within a distributed system architecture involving Miners, Contributors, and Validator-Relays. It enables cryptographically verifiable arbitration in "honest-but-curious" and Byzantine scenarios.*  



---------------------------------------------------------------------------

**Author**:Rushing_to_freedom

**Creation Date**: 2025-07-07 

**License**: [MIT License](LICENSE)


A comprehensive human verification system for Bittensor subnets, featuring:
- Cross-task assignment mechanics
- Economic incentive structures
- Sybil attack protection mechanisms

[Full System Documentation](subnet_logic.md)

## Use Cases
- Implementation in your project
- Reference architecture
- Academic research

## Contacts
- Discord: @Rushing_to_freedom
