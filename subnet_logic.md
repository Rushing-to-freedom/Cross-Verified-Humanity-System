---
title: Distributed-Human-Verification-System
author: Rushing_to_freedom
date: 2025-07-07
---


## Structured Representation of the System Logic

**I. Key Roles and Functions:**
1.  **Validators:**
    *   Generate tasks (multiple validators, task-level consensus).
    *   Register **Contributors** (only the fact of registration, NOT humanity verification).
    *   Assign a unique ID to the contributor within the subnet.
    *   Randomly **assign** a contributor to a specific task for a specific **Miner** in each task round.
    *   Calculate and maintain the **rating (R)** of each contributor.
    *   Calculate and assign a **weight (Weight, W)** to each miner.
    *   Receive and compare task completion reports from Miners and (optionally) from the Contributor Client application.

2.  **Miners:**
    *   Register in the subnet (with a burnable fee, dynamic price depending on demand; the weakest is displaced upon new entry).
    *   Receive tasks from Validators.
    *   Receive from Validators the **assigned contributor** for each of their tasks.
    *   Provide a platform/access for the assigned contributor to solve the task.
    *   Transmit contributors' answers to the Validator (both their own and others').
    *   Can view the rating `R` of any contributor (from the Validator).
    *   Can **refuse to issue a task** to a contributor with low `R` (must declare the refusal).
    *   Receive `W` based on their own work and the work of *their own* and *others'* contributors.

3.  **Contributors:**
    *   Register with a Validator (through a Miner: Miner → application to Validator + subscription key → Contributor → registration with Validator; optionally via client application with MetaMask).
    *   Have a unique ID and rating `R` (maintained by the Validator).
    *   Receive **assigned tasks** from the Validator (via the platform of a specific Miner).
    *   Solve tasks on the platform of the assigned Miner.
    *   (Optionally) Report directly to the Validator via the client application.

**II. Key Interaction Mechanisms and Logical Sequences:**

1.  **Registration and Start of Work:**
    *   `Validator registers a Contributor` (fact, without verification) → Assigns ID.
    *   `Miner registers a Contributor with a Validator` → Gives subscription key to Contributor → `Contributor completes registration` with Validator (possibly via client application/MetaMask).
    *   **Sybil protection at startup:**
        *   Limit tasks/rewards for new contributors (until reaching min `R`).
        *   Small registration fee for each Contributor.
    *   `Validator generates a task` (consensus with other validators) → `Sends task to all Miners`.
    *   `Validator randomly assigns a Contributor` for this task to each Miner → `Informs Miner which Contributor to expect`.

2.  **Task Solving and Cross-Verification ("Humanity Mechanism"):**
    *   `Contributor accesses the platform of the assigned Miner` → `Solves the assigned task`.
    *   **Key Logic:** A human will solve the task on *any* (own/other) Miner's platform. A bot configured for a *specific* Miner will likely **fail** to solve tasks on *foreign*, unpredictably assigned Miners' platforms.
    *   `Miner transmits Contributor's answer to Validator`.

3.  **Record Keeping and Contributor Rating (`R`) Calculation:**
    *   `Validator maintains records` of all solved/unsolved tasks by each Contributor.
    *   `Validator calculates rating R` based on:
        *   Correctness of solutions (data from *different* Miners).
        *   Number of successfully solved tasks (especially on *foreign* platforms).
    *   `R` **persists** when Miner exits subnet. Contributor retains `R`.

4.  **Impact on Miner Weight (`W`):**
    Miner weight (`W`) depends **comprehensively** on Miner behavior and Contributors' performance:
    *   **A. Sending Answers:**
        *   `W(+)`: For total **correct** answers sent (own + others' contributors).
        *   `W(-)`: If Miner **withholds** or **distorts** others' contributors' answers → Fewer correct answers → `W↓`.
        *   `W(-)`: Additional penalty for **non-transmission** of answers.
    *   **B. Behavior of *Own* Contributors:**
        *   `W(+)`: High `R` of contributors → Bonus `W↑` for Miner.
        *   `W(-)`: Low `R` of contributors → No bonus → `W↓` relative to others.
    *   **C. Work of *Own* Contributors on *Others'* Platforms:**
        *   `W(-)`: Intentional failure on foreign tasks → Contributors' `R↓` → `W↓` for Miner.
        *   `W(-)`: Systematic refusal/failure → Additional `W` penalty.
    *   **D. Refusal to Issue Tasks:**
        *   Miner **may refuse** tasks to low-`R` contributors (must declare refusal).
        *   Total refusals **affect `W`** (negatively if excessive/unjustified).

5.  **Economic Incentives and Miner Balancing:**
    *   **Verification incentive:** Foreign Miners implement humanity checks (CAPTCHA, etc.).
    *   **Admission dilemma:**
        *   Admit foreign contributor → Potential correct answer → `W(+)`
        *   Block contributor → Risk missing correct answer → `W↓`
    *   **Forced honesty:** Combined `W` effects compel Miners to:
        *   Ensure contributors are human and competent.
        *   Process foreign contributors' answers honestly.
        *   Encourage their contributors to solve foreign tasks.

6.  **Additional Mechanisms and Clarifications:**
    *   **Contributor Client App:**
        *   Direct Validator registration via Miner's key (MetaMask integration).
        *   Direct task reports to Validator.
        *   `Validator cross-checks` Miner and Contributor reports.
    *   **Contributor Re-registration:**
        *   Fee **scaled with contributor's `R`**.
        *   **Cooldown mechanism:** 12-24h delay between Miner detachment and new registration.
        *   Frequency limit: 1-2 changes/week.
    *   **"False Humanity" (AI):** Advanced bots surpassing humans acquire high `R` → Treated as legitimate participants.
    *   **Bittensor Integration:**
        *   Miner registration with burnable fee (price adjusts with demand).
        *   Weakest Miner evicted when new Miners join.
        *   Contributor `R` preserved across Miner changes.

**III. Core Logical Sequences (Cause-Effect Chains):**

1. **Registration → Assignment → Task Solving → Reporting → R Calculation**  
   `Validator` → `Contributor` → `Miner Platform` → `Validator`

2. **High Contributor R → High Miner W**  
   Good contributor performance → Miner bonus

3. **Low R → Task Refusal → W Impact**  
   Poor R → Miner refusal → W adjustment

4. **Withholding Foreign Answers → W Reduction**  
   Non-transmission → Fewer correct answers + penalty → W↓↓

5. **Sabotage of Foreign Tasks → W Penalties**  
   Intentional failure → R↓ + sabotage penalty → W↓↓

6. **Cross-Verification → Humanity Assurance**  
   Random assignments + Economic incentives → Bot detection

**Conclusion:**  
The system uses **random cross-assignment** of Contributors to Miners for bot detection, reinforced by **economic incentives/sanctions** based on Contributor ratings (`R`) and Miner weights (`W`). This creates a self-regulating ecosystem where Miners are compelled to ensure human participation and honest processing. Integration with Bittensor provides additional security through dynamic fees and reputation persistence.
