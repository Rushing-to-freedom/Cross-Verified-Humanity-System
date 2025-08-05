**Architecture of the Dojo Subnet in the Bittensor Ecosystem**

**I. Participant Registration and Access Economics**

**Miner Registration:**
*   A Miner is required to register on the subnet.
*   Registration is accompanied by a **burnable registration fee**.
*   **Dynamic Fee Pricing:** The registration cost correlates with the number of new Miners wishing to join. The price increases with rising demand and decreases with falling demand.
*   **Replacement Mechanism:** When a new Miner pays the fee and joins, the Miner with the lowest weight (the "weakest") is removed from the subnet.

**Contributor Registration:**
*   A Miner registers its Contributors through Validators.
*   The Validator performs the Contributor registration and binds the Contributor to the specific Miner who initiated the registration.
*   **Registration Functions:**
    *   Assigning the Contributor a unique identifier (conditional number) within the subnet.
    *   Ensuring the accounting of the Contributor's activity.
    *   Verification and calculation of the Contributor's rating.
*   **Sybil Attack Control:** A small fee is charged for registering each Contributor.
*   For newly registered Contributors, trust limitation mechanisms may be applied (e.g., limits on the number of tasks or rewards for the Contributor until they reach a minimum rating).

**Preservation of Contributor Rating:**
*   The Contributor's rating is preserved if their Miner leaves the subnet or if they change Miners. However, re-registration with a new Miner requires a repeated payment.
*   The Contributor's rating is public and visible to all subnet participants.

**Management of Contributor Transitions to Other Miners:**
*   **Dynamic Re-registration Fee:** The cost of rebinding a Contributor to a new Miner is tied to their current rating; the higher the rating, the higher the re-registration price.
*   **"Cooling-off" Mechanism:**
    *   A mandatory delay (e.g., 12-24 hours) is introduced between detaching a Contributor from the old Miner and the possibility of their registration with a new Miner.
    *   The frequency of re-registrations is limited (e.g., no more than 1-2 times per week).

**II. Task Generation, Interfaces, and Task Assignment**

**Task Source:** Tasks are generated according to the subnet's algorithms, created by the subnet developer. For example, all tasks in the subnet could be generated exclusively by Validators, or this work could be distributed between Miners and Validators across stages of the generation process.

**Interface Standardization:**
*   The Validator defines a standard interface for interacting with each type of task.
*   The Validator provides a ready-made implementation of this interface for Miners.
*   **Modification Prohibition:** Miners are not allowed to modify the provided task interface or its solutions.
*   The integrity of the interface is verified by the Validators' cryptographic signatures.

**Consequences of Standardization and Modification Prohibition:**
*   Eliminates the possibility for Miners to manipulate their own platform to gain unfair advantages.
*   Allows Validators to embed their standard bot protection mechanisms (anti-bots) or tests for AI agents directly into the task interface; Miners cannot remove or bypass them.

**Task Distribution and Solving:**
*   Validators transfer generated tasks to Miners and distribute them among them according to algorithms defined by the subnet developer.
*   For each task sent to each Miner, the Validator randomly assigns one or several Contributors (from among all Contributors registered on the subnet).

**Solving Process:**
1.  The assigned Contributor gains access to the platform of the Miner to whom they were assigned.
2.  The Contributor solves the assigned task on that Miner's platform.

**III. Participant Interaction and Transparency**

**Cross-Platform Task Solving:**
*   Contributors solve tasks both on the platform of their "home" Miner (to whom they are bound) and on the platforms of other ("foreign") Miners.
*   The interaction of Contributors with the platforms of any Miners (their own and others) makes the task-solving process transparent.
*   The entire process of task distribution, obtaining task solutions, their verification, and auditing by Validators can be observed by all participants of the decentralized interaction within the subnet, including auditors (after the completion of the current task generation and solving iteration).

**Traffic Anonymization:**
*   Validators function as proxy servers for all network traffic within the subnet.
*   Miners can also participate in the traffic anonymization process between two proxy-Validators.
*   A Contributor **should not know** for which specific Miner or whose task they are solving at a given moment.
*   A Miner **should not know** which specific Miner a Contributor working on their platform belongs to, or whose task they are solving.

**Audit:** All proxied traffic is audited by the Validator. The Validator records all steps of the interaction (request-response) between Miners and Contributors.

**IV. Incentive System, Weights, and Sanctions**

**Miner's Goal:** To increase their weight in the network by launching high-quality Contributors on the subnet and controlling the quality of their work, and by identifying dishonest Miners and Contributors using standardized anti-bots and AI tests from Validators.

**Miner Weight Calculation:** The primary weight of a Miner depends on:
1.  The total number of correctly solved tasks on their platform (by both their own Contributors and foreign Contributors).
2.  The overall average rating of all their Contributors bound to them (whom they registered with the Validator), considering that the rating of their Contributors depends on their task solutions on all platforms, both their own Miner's and foreign Miners'.

**Miner Incentives:**
*   Creating high-quality Contributors is economically beneficial, as it increases the chances of correct task solutions and weight growth.
*   **Counteracting bots on their platform:** Miner (M1) is incentivized to block bots launched by another Miner (M2) on M1's platform, because bots provide incorrect answers, reducing the total number of correct solutions for M1.
*   **Attracting real Contributors:** Miner (M1) is incentivized to have real human Contributors from other Miners (M2) solve tasks on M1's platform, as this increases the number of correct answers and M1's weight.

**Sanctions for Dishonest Miner Behavior:**
*   **Incomplete/Distorted Answer Submission:** If a Miner sends the Validator only good answers from their own Contributors, and does not send or distorts answers from foreign Contributors:
    *   They receive less weight due to a lower total number of submitted correct answers compared to Miners who do not do this.
    *   Additionally, a small weight reduction is imposed as a sanction for non-submission/distortion of foreign answers (detected during auditing of anonymized traffic).

**Impact of Contributors on Miner Weight:**
*   **Positive:** The Miner receives additional weight for the high rating of their Contributors, if they solve tasks well (both their own and others').
*   **Negative:** The Miner does not receive additional weight (or receives reduced weight) due to the low rating of their Contributors, if they solve tasks poorly.

**Sanction for Contributor Inaction:** If a Miner's Contributors intentionally do not solve or solve poorly tasks on foreign platforms:
*   Their rating decreases, which negatively affects their Miner's weight.
*   Additionally, a small weight reduction is imposed on their Miner itself because its Contributors do not solve foreign' tasks.

**Contributor Incentives:** Rating, influencing the cost of re-registration and, indirectly, demand on this contributor (a reputation market for Contributors is created).
*   The Contributor's rating is preserved if their Miner leaves the subnet or if they change Miners. However, re-registration with a new Miner requires payment.
*   **Dynamic Re-registration Fee:** The cost of rebinding a Contributor to a new Miner corresponds to their current rating; the higher the rating, the higher the re-registration price.
*   **"Cooling-off" Mechanism:**
    *   A mandatory delay (e.g., 12-24 hours) is introduced between detaching a Contributor from the old Miner and the possibility of their registration with a new Miner.
    *   The frequency of re-registrations is limited (e.g., no more than 1-2 times per week).

**V. Handling AI Agents**

**AI Agent Registration:** A Miner can register two types of Contributors through a Validator: **Human Contributor** and **AI-Agent Contributor**.

**Anti-Bot Adaptation:**
*   For officially registered and declared AI agents, standard human anti-bot tests (captchas) are disabled and adapted for generative AI tests.
*   Instead, AI-specific tests are applied:
    *   Checking creativity/unconventionality of solutions.
    *   Analysis of consistency in reasoning chains.
    *   Tests for understanding context and depth of analysis.
    *   Tasks with traps targeting known AI weaknesses.

**Miner Bonuses:** A Miner receives additional weight bonuses for registering efficiently working, officially declared AI agents.

**Ratio Regulation:** The Validator can determine the ratio of the number of Human Contributors to AI-Agent Contributors in the subnet (e.g., a limit on the number of AI agents per Miner).

**AI Agent Admissibility:** The architecture allows and encourages the work of AI agents as Contributors who were openly registered as AI-contributors, if they can solve tasks on par with or better than humans. The system creates an environment for the development of such AIs.

**VI. Verification and Control Mechanisms (Sources of Truth)**

Validators ensure the verification of Miner and Contributor work through:
1.  **Anti-bots** installed on competing Miners' platforms.
2.  The work of **foreign Contributors** on a Miner's platform and, conversely, observation on one's own platform of the activity of Contributors from other Miners.
3.  **Control software Contributors from Validators:** Validators send control queries to Miners disguised as Contributors, indistinguishable from real ones.
4.  **Control software Miners from Validators:** Validators send control tasks to Contributors, indistinguishable from real ones.
5.  **Benchmark control tasks:** Validators generate tasks with pre-known answers.
6.  **Trusted benchmark teams:** Human Contributors and Miners from the developer team or trusted partners who have a high level of competence and trust.
7.  **Behavior pattern analysis:** The Validator identifies statistical anomalies in the actions of Miners and Contributors.

**VII. Role of Validators (Summary of Key Functions)**

*   Generating tasks according to a given algorithm.
*   Defining and providing standard interfaces for tasks (including built-in anti-bots and AI tests).
*   Registering Contributors and binding them to the registering Miners.
*   Assigning Contributors to tasks for all Miners randomly.
*   Calculating Contributor ratings.
*   Calculating and distributing Miner weights.
*   Proxying and anonymizing all network traffic.
*   Auditing interactions.
*   Implementing control mechanisms (Section VI).
*   Regulating the ratio of Human/AI Contributors.
*   Generating tests for AI agents.

**Final System Effect:**
The Dojo subnet architecture creates a complex set of conditions that compel Miners to ensure tasks are solved either exclusively manually by Human Contributors or by officially registered AI agents capable of solving tasks on par with humans. This is achieved through economic incentives (weight), sanctions, process transparency, mutual control among participants, and strict interface standardization managed by Validators. The system simultaneously stimulates the development of effective AI agents and provides protection against abuse.
