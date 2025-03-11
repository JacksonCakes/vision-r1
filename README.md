This is all the training files related to this [blog](https://jacksoncakes.com/2025/03/10/can-an-llm-learn-to-see-fine-tuning-qwen-05b-for-vision-tasks-with-sft-grpo/)
For integrate a pertrained vision encoder with language model refer [here](https://github.com/JacksonCakes/vision-r1/blob/main/merge_llm_into_vlm.ipynb) (Support Qwen 2.5) or you can download the integrated model at [huggingface](https://huggingface.co/jacksonkek/qwen-0.5-vl-custom)

## Requirements
use `uv` for faster installation.
```
python -m venv myenv
source myenv/bin/activate
uv pip install -r requirements.txt
```
### Inference
You can refer to `inference.ipynb` for model inference.

## Stage 1 SFT:
```
python stage1_instruct.py
```

## Stage 2 GRPO:
```
# modify the model name with your own chekcpoint
python stage2_grpo.py
```
This will also generate a `response_log.txt` to observe the response generated by the policy model.

## Track the experiment logs
```
mlflow ui
# then navigate to http://localhost:5000
```
## Evaluate on SuperCLEVR
You can evaluate OOD counting performance on a subset of SuperCLEVR
```
wget https://www.cs.jhu.edu/~zhuowan/zhuowan/SuperCLEVR/to_be_released/images.zip
unzip images.zip

## modify model path in the script
python eval_superclevr.py
```

## Acknowledgements
Special thanks [Deep-Agent/R1-V](https://github.com/Deep-Agent/R1-V) for open source the dataset. [Glows.ai](https://glows.ai/invite/Glows-3x23oo25?utm_source=Blog&utm_medium=KOL_Post&utm_campaign=Glows-3x23oo25&utm_content=AIengineer) for supporting the compute!
