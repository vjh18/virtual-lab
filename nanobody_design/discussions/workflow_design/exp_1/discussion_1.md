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

To address the agenda for optimizing the nanobody design process using ESM, AlphaFold-Multimer, and Rosetta, here is a detailed plan that aligns with the constraints and goals of the project:

1. **Order of Operations in Each Iteration:**
   - **Step 1:** Use ESM to evaluate all potential mutations to the nanobody. This step is computationally efficient and will allow us to rapidly screen for promising mutations.
   - **Step 2:** Select a subset of the highest-scoring mutations from the ESM evaluation for further analysis.
   - **Step 3:** Use AlphaFold-Multimer to predict the nanobody-antigen structure for each selected mutation. This step considers structural accuracy and binding prediction.
   - **Step 4:** Use Rosetta to refine the structure predicted by AlphaFold-Multimer and calculate the binding energy for each mutation. This step provides a detailed assessment of binding affinity changes.

2. **Number of Mutations Evaluated in Each Iteration:**
   - Start with evaluating all potential mutations using ESM. After obtaining ESM scores, select the top 20 mutations for evaluation with AlphaFold-Multimer and Rosetta to manage computational resources efficiently.

3. **Formula to Weigh Scores:**
   - Develop a composite score (CS) for each mutation using the formula:
     \[
     \text{CS} = w_1 \cdot \text{ESM Score} + w_2 \cdot \text{(AlphaFold-Multimer Interface pLDDT)} - w_3 \cdot |\text{Rosetta Binding Energy}|
     \]
   - Choose weights \(w_1, w_2, w_3\) based on the relative importance of prediction accuracy (AlphaFold-Multimer), computational efficiency (ESM), and refinement precision (Rosetta). For instance, initial weights could be \(w_1 = 0.2\), \(w_2 = 0.4\), \(w_3 = 0.4\).

4. **Number of Top-Ranked Mutations to Keep:**
   - Keep the top 5 mutations based on the composite score for the next iteration. This allows for a focused exploration of promising mutations while maintaining diversity.

5. **Decision on Number of Iterations:**
   - Continue iterations until the improvement in the composite score across mutations plateaus or starts to decrease. Set an upper limit of 3-5 iterations to balance computational time with potential gains in binding affinity.

6. **Selection of the Final Set of 24 Modified Nanobodies:**
   - **Step 1:** Compile all mutations evaluated in each iteration.
   - **Step 2:** Rank all mutations based on their final composite score.
   - **Step 3:** Select the top 24 unique mutations with the highest composite scores for experimental validation, ensuring coverage of a range of structural and sequence diversity.
   - **Step 4:** Confirm that the selected nanobodies span a broad spectrum of mutations affecting different regions of the nanobody to maximize the likelihood of broad-spectrum activity against various spike protein variants.

By following this plan, we can efficiently explore the mutation landscape and identify nanobody candidates with optimal binding characteristics for experimental validation.

