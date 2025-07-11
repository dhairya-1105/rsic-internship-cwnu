# CWNU Research Internship

This repo contains the evaluation and optimization of vision-language models (PureT, BLIP-2) on the RSICD dataset. The work includes:
- Baseline evaluation of PureT and BLIP-2 using metrics and model characteristics
- LoRA-based fine-tuning of BLIP-2 for remote sensing captioning
- Structural pruning of Q-Former and LLM layers to improve inference speed
- Metric-based evaluation of tradeoffs (BLEU, CIDEr, ROUGE, METEOR)


## Pure T

1. Clone the official [PureT](https://github.com/232525/PureT) repository and set up the model weights as instructed.
2. Run the VisualisationDemo notebook in the provided PureT folder to generate and save a dictionary of predicted captions as a JSON file. This notebook also provides the average inference time, GFLops and number of parameters.
3. Use the generated JSON file as input to the Inference notebook provided in the folder (make sure to replace with your JSON path) and run the notebook to generated BLEU (b1-b4), METEOR, ROUGE and CIDEr scores.

**NOTE:** Caption generation for PureT follows Beam Search with Num_Beams=5

### Baseline Results: PureT on RSICD

| Metric              | Value        |
|---------------------|--------------|
| **BLEU-1**          | 30.009       |
| **BLEU-2**          | 13.440       |
| **BLEU-3**          | 6.577        |
| **BLEU-4**          | 3.670        |
| **METEOR**          | 8.60         |
| **ROUGE-L**         | 21.06        |
| **CIDEr**           | 15.49        |
| **Parameters**      | 229.41M      |
| **Trainable Params**| 34.16M       |
| **GFLOPs**          | 105.48       |
| **Avg Inference Time** | 416 ms   |

## BLIP-2

- For baseline results, run the blip2-inference notebook under the BLIP-2 folder to generate metrics and model characteristics.

### Baseline Results : BLIP-2 on RSICD

| Metric                  | Value        |
|-------------------------|--------------|
| **BLEU-1**              | 36.27        |
| **BLEU-2**              | 17.60        |
| **BLEU-3**              | 8.41         |
| **BLEU-4**              | 4.34         |
| **METEOR**              | 10.56        |
| **ROUGE-L**             | 22.59        |
| **CIDEr**               | 15.19        |
| **Parameters**          | 3.7B         |
| **Trainable Params**    | 188M         |
| **GFLOPs**              | 761.17    |
| **Avg Inference Time**  | 844 ms       |

## Visualizations

### 🔹 PureT Baseline Performance
![PureT Baseline](Plots/puret_baseline.png)

### 🔹 BLIP-2 Baseline Performance
![BLIP-2 Baseline](Plots/blip2_baseline.png)

### 🔹 PureT vs BLIP-2 – Metric Comparison
![PureT vs BLIP-2](Plots/puret_vs_blip2_baseline.png)

### 🔹 PureT vs BLIP-2 – Model Characteristics
![Model Characteristics](Plots/puret_vs_blip2_baseline_model_chars.png)


As for the LoRA fine-tuning, I've uploaded the template notebooks under the BLIP-2 folder:
1. The blip2-lora-finetuning notebook contains the template for using LoRA with various configurations. To try a different config, simply edit the LoraConfig block by adding or removing target_modules or modifying rank or alpha or dropout values. Just make sure to use your own HF token and change model name before pushing to the hub.
2. The blip2-lora-inference notebook contains the evaluation pipeline for pruned models. Just replace the model name with your own model from the hub and run the notebook.
3. If you want to check out all the different LoRA configs, check out the [Finetuning](https://www.kaggle.com/code/bladesofchaos11/blip-2-finetuned) and [Inference](https://www.kaggle.com/code/bladesofchaos11/blip-2-final) notebooks on my Kaggle.

   
