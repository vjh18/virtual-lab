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

To address the agenda questions effectively, we need to plan the iterative design process to maximize efficiency and ensure the best possible outcomes in terms of nanobody binding improvement while adhering to the time constraints. Here's a detailed response to each of the agenda questions:

1. **Order of Operations for Evaluating Mutations:**

   In each iteration, the order of operations for evaluating mutations should be:
   - **Step 1:** Use ESM to quickly evaluate all potential mutations to the nanobody. This will allow us to perform an initial, rapid screening to identify promising mutations.
   - **Step 2:** For the top mutations identified by ESM, use AlphaFold-Multimer to predict the nanobody-antigen complex structure and evaluate the mutation's effect on the interface confidence score.
   - **Step 3:** Finally, use Rosetta to perform detailed binding energy calculations on the structures predicted by AlphaFold-Multimer.

2. **Number of Mutations to Evaluate:**

   In each iteration, we will start with evaluating all potential mutations using ESM, since it takes only 5 minutes for this step. However, due to time constraints with AlphaFold-Multimer, we should limit the number of top mutations from the ESM evaluation to a manageable number, say **20 mutations**, to pass on for further evaluation with AlphaFold-Multimer and subsequently with Rosetta.

3. **Weighing the Scores to Rank Mutations:**

   To rank the mutations at the end of each iteration, we will use a weighted formula incorporating the scores from ESM, AlphaFold-Multimer, and Rosetta. A potential formula could be:

   \[
   \text{Composite Score} = w_1 \times \text{ESM Score} + w_2 \times (\text{AlphaFold-Multimer Score}) - w_3 \times (\text{Rosetta Score})
   \]

   Where \(w_1\), \(w_2\), and \(w_3\) are weights that should be determined based on the relative importance and reliability of each scoring metric. For example, initial weights might be set to \(w_1 = 1\), \(w_2 = 0.5\), \(w_3 = 0.2\), reflecting the rapid screening capability of ESM and the structural insights provided by AlphaFold and Rosetta.

4. **Top-Ranked Mutations to Keep:**

   At the end of each iteration, we will keep the **top 5 mutations** based on the composite score to carry forward to the next round. This number ensures diversity while maintaining focus on the most promising candidates.

5. **Deciding Number of Iterations:**

   The number of iterations will depend on the convergence of the composite scores. We can aim for approximately 3-5 iterations, monitoring the improvement in scores and assessing if improvements plateau.

6. **Selecting Final Set of 24 Modified Nanobodies:**

   - **Step 1:** Compile all mutations evaluated across iterations with their composite scores.
   - **Step 2:** Rank all the mutations globally based on their composite scores.
   - **Step 3:** Select the top 24 mutations with the highest composite scores for experimental validation, ensuring diversity by not choosing closely related mutations within the list.

This structured approach should facilitate the design of effective nanobody variants against the SARS-CoV-2 spike protein, leveraging computational resources efficiently while adhering to the project timeline.

