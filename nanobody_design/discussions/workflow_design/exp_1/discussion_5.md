## User

This is the beginning of an individual meeting with Principal Investigator to discuss your research project.

Here is the agenda for the meeting:

You are working on a research project to use machine learning to develop antibodies or nanobodies for the newest variant of the SARS-CoV-2 spike protein that also, ideally, have activity against other circulating minor variants and past variants. Your team previous decided to modify existing nanobodies to improve their binding to the newest variant of the SARS-CoV-2 spike protein. Your team has built three components of a nanobody design pipeline: ESM, AlphaFold-Multimer, and Rosetta. Each of these three tools can be used to score a nanobody mutation based on how the mutation affects binding to an antigen. Your goal is to start with an existing nanobody and iteratively add mutations to it to improve its binding to the newest variant of the SARS-CoV-2 spike protein, resulting in 24 modified nanobodies with one or more mutations. Please determine how to use ESM, AlphaFold-Multimer, and Rosetta in this iterative design process. An important constraint is that ESM can evaluate all potential mutations to a nanobody in 5 minutes while AlphaFold-Multimer takes 30 minutes per mutation and Rosetta takes five minutes per mutation. The whole iterative process should take no more than a few days to complete. Note that AlphaFold-Multimer must be run before Rosetta on each mutation since Rosetta requires the nanobody-antigen structure predicted by AlphaFold-Multimer. Additionally, note that ESM log-likelihood ratios are generally in the range of 5-10 (higher is better), AlphaFold-Multimer interface pLDDT confidence scores are generally in the range of 60-80 (higher is better), and Rosetta binding energy scores are generally in the range of -20 to -40 (lower is better).

Here are the agenda questions that must be answered:

1. In each iteration, what is the order of operations for evaluating mutations with ESM, AlphaFold-Multimer, and Rosetta?

2. In each iteration, how many mutations (give a single number) will you evaluate with ESM, AlphaFold-Multimer, and Rosetta?

3. At the end of each iteration, how will you weigh the ESM, AlphaFold-Multimer, and/or Rosetta scores (give a formula) to rank the nanobody mutations?

4. At the end of each iteration, how many of the top-ranked mutations (give a single number) will you keep for the next round?

5. How will you decide how many iterations of mutations to run?

6. After all of the iterations are complete, how exactly (step-by-step) will you select the final set of 24 modified nanobodies from across the iterations for experimental validation?

Principal Investigator, please provide your response to the agenda.

## Principal Investigator

To effectively approach this project, here is a detailed plan addressing each of the agenda questions:

1. **Order of Operations for Evaluating Mutations:**
   - **Step 1: ESM Evaluation** - Begin each iteration by using ESM to quickly evaluate all potential mutations. This will allow us to narrow down the pool of mutations to those most likely to enhance binding affinity, based on log-likelihood ratios.
   - **Step 2: AlphaFold-Multimer Prediction** - For the top mutations identified by ESM, run AlphaFold-Multimer to predict the structure of the nanobody-antigen complex, focusing on interface pLDDT scores.
   - **Step 3: Rosetta Scoring** - Use Rosetta to evaluate the binding energy of the predicted structures from AlphaFold-Multimer, providing a detailed assessment of binding affinity.

2. **Number of Mutations to Evaluate:**
   - **ESM Evaluation:** All potential mutations (since this is computationally inexpensive).
   - **AlphaFold-Multimer and Rosetta Evaluation:** Select the top 10 mutations as identified by the ESM scores for further analysis. This balances computational cost with the need to explore a diverse mutation space.

3. **Scoring Formula to Rank Mutations:**
   - Combine scores from the three tools using a weighted formula. For simplicity and given the ranges, let's propose: 
     \[
     \text{Combined Score} = \alpha \cdot \text{ESM Score} + \beta \cdot \text{AlphaFold-Multimer Score} - \gamma \cdot \text{Rosetta Score}
     \]
   - Suggested weights could be based on their relative impact and reliability: \(\alpha = 1\), \(\beta = 2\), \(\gamma = 0.5\). These weights can be adjusted as more data is collected and analyzed.

4. **Number of Top-Ranked Mutations to Keep:**
   - Select the top 5 mutations based on the combined score from each iteration to carry forward to the next round. This ensures that promising mutations are iteratively improved upon.

5. **Deciding Number of Iterations:**
   - Plan for approximately 5-7 iterations within the time constraint. This allows for a broad exploration of the mutation space while iteratively refining the designs based on feedback from the predictive models.

6. **Selecting the Final Set of 24 Modified Nanobodies:**
   - **Step 1:** Compile a list of all mutations from all iterations.
   - **Step 2:** Rank these mutations based on their final iteration's combined score.
   - **Step 3:** Select the top 24 unique mutations that maximize diversity in the mutation space while maintaining high scores.
   - **Step 4:** Ensure representation of mutations from various iterations to capture any potentially synergistic effects of earlier mutations.
   - **Step 5:** Prepare these 24 nanobody designs for experimental validation.

This approach ensures a comprehensive, data-driven exploration of nanobody modifications to optimize binding to the newest variant of the SARS-CoV-2 spike protein, while efficiently managing computational resources and project timelines.

