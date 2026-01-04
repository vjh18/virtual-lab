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

To address the agenda for the meeting, here's a structured plan for utilizing the ESM, AlphaFold-Multimer, and Rosetta tools within the constraints provided:

### 1. Order of Operations for Evaluating Mutations

**Step 1: ESM Scoring**
- Evaluate all potential mutations of the starting nanobody using ESM. This step is crucial for a rapid first pass to filter mutations with promising binding potentials.

**Step 2: AlphaFold-Multimer Prediction**
- Select the top mutations from the ESM scoring (see the number in the next section) and predict their structures using AlphaFold-Multimer. This will provide detailed structural predictions necessary for further analysis.

**Step 3: Rosetta Scoring**
- Use the structures predicted by AlphaFold-Multimer and assess the binding energy of each mutation using Rosetta. This step refines the selection by evaluating the likely binding efficiency.

### 2. Number of Mutations Evaluated

- **ESM:** Evaluate all potential single-point mutations for the nanobody in parallel. This is feasible given its rapid evaluation time.
- **AlphaFold-Multimer:** Select the top 10 mutations based on ESM scores for further evaluation, given the longer computation time required.
- **Rosetta:** Evaluate these same 10 mutations since they depend on the AlphaFold-Multimer predictions.

### 3. Formula for Weighing Scores

To rank the nanobody mutations after each iteration, use a weighted scoring formula that balances the strengths and weaknesses of each tool:

\[ \text{Score} = w_1 \times \text{normalized ESM score} + w_2 \times \text{normalized AlphaFold-Multimer pLDDT} + w_3 \times \text{normalized Rosetta binding energy} \]

- Suggested weights: \( w_1 = 0.3 \), \( w_2 = 0.3 \), \( w_3 = 0.4 \) (adjust based on pilot results)

### 4. Number of Top-Ranked Mutations Kept

- Keep the top 3 mutations from each iteration for the next round. These mutations will be used to generate further derivative mutations in the subsequent iteration.

### 5. Deciding the Number of Iterations

- Run a sufficient number of iterations until a saturation point is reached, where additional iterations do not significantly improve the top scores. Initial target: 5-7 iterations, adjusted based on observed convergence of scores.

### 6. Final Selection of 24 Modified Nanobodies

**Step-by-Step Selection Process:**

1. **Compile Results:** Gather all evaluated mutations and their scores across all iterations.
2. **Rank Mutations:** Sort all mutations based on their weighted scores.
3. **Diversity Check:** Ensure coverage of diverse mutations by considering both sequence diversity and structural diversity (assessed by predicted structures).
4. **Select Top 24:** Choose the top 24 mutations, ensuring a mix of high scores and diversity to maximize potential for broad-spectrum efficacy.
5. **Review with Team:** Conduct a final review with the team to assess any additional insights or considerations before experimental validation.

This plan ensures efficient use of computational resources while maximizing the likelihood of identifying high-affinity nanobodies against the SARS-CoV-2 spike protein variant.

