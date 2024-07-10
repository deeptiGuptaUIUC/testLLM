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

```
python test_selection/data_by_cluster.py \
    --pt_data_path alpaca_data_pre.pt \
    --json_data_path data/code_alpaca_2k.json \
    --json_save_path alpaca_data_pre.json \
    --sample_num 10 \
    --kmeans_num_clusters 100 \
    --low_th 25 \
    --up_th 75
```

```--pt_data_path```: The ```.pt``` file from previous step containing needed embeddings or scores
```--json_data_path```: The targeted dataset in the Alpaca format <br>
```--json_save_path```: The path to save the selected pre-experienced samples <br>
```--sample_num```: How many samples will be selected in each cluster <br>
```--kmeans_num_clusters```: How many clusters will be generated by K-Means <br>
```--low_th``` and ```--up_th```: The lower and Upper threshold for selecting samples within each cluster <br>


3. Train Pre-Experienced Model

4. Select Cherry Data

```
python test_selection/data_analysis.py \
    --data_path data/code_alpaca_2k.json \
    --save_path alpaca_data_cherry.pt \
    --model_name_or_path microsoft/Phi-3-mini-4k-instruct \
    --max_length 512 \
    --prompt alpaca \
    --mod cherry
```

```
python test_selection/data_by_IFD.py \
    --pt_data_path alpaca_data_cherry.pt \
    --json_data_path data/code_alpaca_2k.json \
    --json_save_path alpaca_data_cherry.json \
    --max_length 512 \
    --sample_rate 0.06 \
    --prompt alpaca
```

```--sample_rate```: How many cherry samples you would like to select? You can also use ```--sample_number``` to set the exact number of samples. 

6. Train Cherry Model

|         **Dataset**                 | **Power Consumed** | **Experiment Time** |
|--------------------------|:-----------:|:-------:|
| **Alpaca_2k**      |       |   | 
| **Alpaca_20k**     | |    | 