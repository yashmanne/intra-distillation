## Prerequisites
```
conda create -n ID python=3.8
conda activate ID
pip install -e ./
# NEW:
pip install torch==1.8.1+cu111 torchvision==0.9.1+cu111 torchaudio==0.8.1 -f https://download.pytorch.org/whl/torch_stable.html
pip install sentencepiece
pip install tensorboardX
pip install gdown
```

## Data Download and Preprocessing
We download and preprocess IWSLT'14 dataset for 8 language pairs here (XX->En):
```
bash scripts/preprocess_iwslt14.sh
```
## Train
To train the model, run:
```
bash scripts/train.sh true # with Intra-distillation
# or
bash scripts/train.sh false # without Intra-distillation
```
## Evaluate
To evaluate the model on the test set, run:
```
bash scripts/inference.sh ${MODEL_PATH} ${LANGUAGE}
```
where `${MODEL_PATH}` is your model path and `${LANGUAGE}` is the source language. SacreBLEU will be printed out at the end.
