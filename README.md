# Virtual Lab

[Original README](README.orig.md)

## Getting Started

1. Install dependencies:
    ```bash
    uv sync
    ```

2. Create a `.env` file and configure your environment variables
   > OPENAI_API_KEY="YOUR_OPENAI_API_KEY"

3. Run the example script:
    ```bash
    uv run pip install -e .
    uv run pip install -e .[nanobody-design]
   
    # open `nanobody_design/run_nanobody_design.ipynb`   
    # for anyone encountering this project for the first time, 
    # I suggest reading the source code and running the notebook cell by cell to understand the code.
    ```

## Discussion

As with generative AI, the same inputs will almost certainly produce slightly different outputs each run. Therefore, by
nature, it is hard to replicate the exact same steps as described in the original paper due to stochasticity. In the
team selection step, my run suggested a structural biologist over an immunologist. When I ran it again, it recommended a
structural biologist again, this time keeping the immunologist on the team and replacing the machine learning specialist
described in the paper. There were similar differences throughout each of the project steps, each ballooning on the
prior difference, and I encountered some errors on my end when running the original code. Namely, I had trouble running
each of the 5 discussions in parallel, so I modified the code to run them sequentially. Additionally, I chose to sort
each of the discussion files when creating summaries to correct for the misattribution of certain opinions to certain
conversations. In addition to the original discussion files saved in the “original” folder, I added the discussion files
during my first run into the “exp_1” folder to highlight the variation one might encounter when running this project.

## Future Work

[TODO](TODO.md)
 