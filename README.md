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

<div style="display: flex; justify-content: space-between; gap: 40px;">

<!-- Metrics Table -->
<table>
  <thead>
    <tr><th colspan="2">🔹 Captioning Metrics</th></tr>
  </thead>
  <tbody>
    <tr><td><b>BLEU-1</b></td><td>36.27</td></tr>
    <tr><td><b>BLEU-2</b></td><td>17.60</td></tr>
    <tr><td><b>BLEU-3</b></td><td>8.41</td></tr>
    <tr><td><b>BLEU-4</b></td><td>4.34</td></tr>
    <tr><td><b>METEOR</b></td><td>10.56</td></tr>
    <tr><td><b>ROUGE-L</b></td><td>22.59</td></tr>
    <tr><td><b>CIDEr</b></td><td>15.19</td></tr>
  </tbody>
</table>

<!-- Model Info Table -->
<table>
  <thead>
    <tr><th colspan="2">🧠 Model Characteristics</th></tr>
  </thead>
  <tbody>
    <tr><td><b>Parameters</b></td><td>3.7B</td></tr>
    <tr><td><b>Trainable Params</b></td><td>188M</td></tr>
    <tr><td><b>GFLOPs</b></td><td>761.17</td></tr>
    <tr><td><b>Inference Time</b></td><td>844 ms</td></tr>
  </tbody>
</table>

</div>

## Visualizations

### 🔹 PureT Baseline Performance
![PureT Baseline](Plots/puret_baseline.png)

### 🔹 BLIP-2 Baseline Performance
![BLIP-2 Baseline](Plots/blip2_baseline.png)

### 🔹 PureT vs BLIP-2 – Metric Comparison
![PureT vs BLIP-2](Plots/puret_vs_blip2_baseline.png)

### 🔹 PureT vs BLIP-2 – Model Characteristics
![Model Characteristics](Plots/puret_vs_blip2_baseline_model_chars.png)
