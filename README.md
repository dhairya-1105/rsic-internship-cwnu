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
