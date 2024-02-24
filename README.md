# Luck of the Draw III: Code & Data

Repo to accompany Sean Rehaag, "Luck of the Draw III: Using AI to Extract Data About Decision-Making in Federal Court Stays of Removal" (forthcoming) 49(2) Queen's Law Journal, draft available online: SSRN <https://ssrn.com/abstract=4322881>.

To be cited as: Sean Rehaag, "Luck of the Draw III: Code & Data" (2024), online: GitHub <https://github.com/Refugee-Law-Lab/luck-of-the-draw-iii>.

Data is available here: https://huggingface.co/datasets/refugee-law-lab/luck-of-the-draw-iii

The data can be downloaded like this:


    ## Install needed libraries if not yet installed
    # !pip install datasets
    # !pip install pandas
    
    # Load data
    from datasets import load_dataset
    dataset = load_dataset("refugee-law-lab/luck-of-the-draw-iii", split="train")

    # Convert to DataFrame
    import pandas as pd
    df = pd.DataFrame(dataset)
    df

Code is in Jupyter Notebooks:

- [1_fc_stays_prepare_dockets.ipynb](https://github.com/Refugee-Law-Lab/luck-of-the-draw-iii/blob/main/1_fc_stays_prepare_dockets.ipynb) This notebook takes downloaded Federal Court dockets and puts them into the cleaned format made publicly available on HuggingFace
- [2_fc_stays_gpt_training.ipynb](https://github.com/Refugee-Law-Lab/luck-of-the-draw-iii/blob/main/2_fc_stays_gpt_training.ipynb) This notebook takes human coded data in Excel files, converts them into the appropriate JSONL format for fine-tuning OpenAI models, and provides instructions about submitting fine-tuning jobs to OpenAI
- [3_fc_stays_apply_gpt.ipynb](https://github.com/Refugee-Law-Lab/luck-of-the-draw-iii/blob/main/3_fc_stays_apply_gpt.ipynb) This notebook takes Federal Court docket data and parses that data using OpenAI fine-tuned models to produce a table with docket entry level information about dockets
- [4_fc_stays_final_parsing.ipynb](https://github.com/Refugee-Law-Lab/luck-of-the-draw-iii/blob/main/4_fc_stays_final_parsing.ipynb). This notebook takes the docket entry level table produced in the prior notebook and applies logic to infer data at the docket level producing a table with data on outcomes and judges in all stay applications.
- [5_fc_stays_analyze.ipynb](https://github.com/Refugee-Law-Lab/luck-of-the-draw-iii/blob/main/5_fc_stays_analyze.ipynb) This notebook takes the table of outcomes of all Federal Court stay applications and undertakes statistical analysis for the article


Note: The initial article used a small OpenAI model, ada, that as of January 2024 has been deprecated and is no longer available. The code provides a process to obtain similar (but slightly different) data using a model currently available (GPT3.5 Turbo). The data obtained 
using the deprecated model remains available, and both the 4th and 5th notebook allow users to use either the deprecated data or current data.


Acknowledgements:

- This article draws on research supported by the Social Sciences and Humanities Research Council, the Law Foundation of Ontario and the Digital Research Alliance of Canada.
- The Federal Court data used for this articled was gathered with the assistance of Jacob Danovitch
- Human coded training data was prepared with the assistance of Krystyna Jones
- The author is grateful for feedback on an earlier draft from Simon Wallace and from the anonymous reviewers at the Queen's Law Journal.