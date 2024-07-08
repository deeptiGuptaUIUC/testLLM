## Install

Install the dependencies with `pip install -r requirements.txt`

Note: This `requirements.txt` is originated from the [Stanford Alpaca](https://github.com/tatsu-lab/stanford_alpaca). If you are using a different code base with PyTorch installed, we recommend you manually install the below packages and do not need to install from `requirements.txt`

`pip install tqdm`

`pip install scikit-learn`

## Run Code


1. Select Pre-Experienced Data

```
python3 test_selection/data_analysis.py \
    --data_path data/code_alpaca_2k.json \
    --save_path alpaca_data_pre.pt \
    --model_name_or_path microsoft/Phi-3-mini-4k-instruct \
    --max_length 512 \
    --prompt alpaca \
    --mod pre
```

```--data_path```: The targeted dataset in the Alpaca format <br>
```--save_path```: The path to save the ```.pt``` file containing embeddings or scores <br>
```--prompt```: The prompt type used for training and selecting data, can choose between ```alpaca``` or ```wiz``` <br>
```--mod```: ```pre``` used for getting needed embeddings or scores on selecting pre-experienced samples 