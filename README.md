# NAVER_PROJECT : Sparse Matching for VO

This is README for handling sparse matching task.

# Environments

Tested on Ubuntu 18.04 CUDA-10.1 (10.2) with Python 3.6, Pytorch 1.6.0

Your main workspace will be "project_code".

<pre>
<code>
cd project_code
conda create -n naver_project python=3.6
conda activate naver_project
conda install cudatoolkit=10.1 pytorch=1.6.0 torchvision -c pytorch
pip install -r requirements.txt
</code>
</pre>

# Dataset Prepare

Scannet Dataset, please download dataset in this [page](http://www.scan-net.org/).
After that, training/validation split of unique scenes are provided in dataloader/scannet and please run "scannet_export.py" to prepare the dataset.

# Training / Testing

To train the model from scratch, please run this script. After running this, you can see your results and related files (checkpoints etc...) in your ./output/basic/scratch

<pre>
<code>
CUDA_VISIBLE_DEVICES [DEVICE TO RUN] python main.py --model basic --config config --workspace scratch
</code>
</pre>

You can change some hyperparameters/path information of your model and dataset at config.py and model/basic/config.json.

To test the model from pretrained weight, please run this script.

<pre>
<code>
CUDA_VISIBLE_DEVICES [DEVICE TO RUN] python main.py --model basic --config config_val --workspace validation --loadmodel ./pretrained/weight.ckpt --mode test
</code>
</pre>
