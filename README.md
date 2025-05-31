# [ICME2025 Oral] TSTMotion: Training-free Scene-aware Text-to-motion Generation

<p align="left">
    <a href='https://arxiv.org/abs/2505.01182'><img src='https://img.shields.io/badge/arxiv-arxiv-red' alt='youtube video'></a>
    <a href='https://tstmotion.github.io/'><img src='https://img.shields.io/badge/project-project-blue' alt='project page'></a>
</p>


This repository is an official implementation of [TSTMotion](https://TSTMotion.github.io/TSTMotion.github.io/) <b>BASELINE</b>. The <b>COMPLETE CODE</b> is being cleaned and will be released soon.


## Folder Structure
```
├── datasets
│   ├── demo_scene
│   │   ├── ScanNet0604
│   │   │   ├── detection_results.pkl
│   │   │   ├── scene0604_00_vh_clean.ply
│   ├── HumanML3D
│   │   ├── new_joint_vecs
│   │   ├── new_joints
│   ├── prompt
│   ├── smplx
│   │   ├── SMPLX_NEUTRAL.npz
│   │   ├── SMPLX_NEUTRAL.pkl
├── OmniControl
│   ├── glove
│   ├── t2m
│   ├── save
│   │   ├── omnicontrol_ckpt
│   │   │   ├── model_humanml3d.pt
├── scripts
├── utils
```

## Environment Setup

### 1. Setup Conda:
```
conda env create -f environment.yml
conda activate tstmotion
python -m spacy download en_core_web_sm
pip install git+https://github.com/openai/CLIP.git
```

### 2. Download Dependencies:
The results should be placed in OmniControl folder as shown in Folder Structure, including glove,t2m and smplx.
```
cd OmniControl
bash prepare/download_smpl_files.sh
bash prepare/download_glove.sh
bash prepare/download_t2m_evaluators.sh
```

### 3. Download HumanML3D Dataset:
Follow the instructions in [HumanML3D](https://github.com/EricGuo5513/HumanML3D), then copy the results as shown in Folder Structure.

### 4. Download Checkpoint:
The results should be placed as shown in Folder Structure, including [model_humanml3d.pt](https://drive.google.com/file/d/1oTkBtArc3xjqkYD6Id7LksrTOn3e1Zud/view).
```
cd /OmniControl/save
gdown --id 1oTkBtArc3xjqkYD6Id7LksrTOn3e1Zud
unzip omnicontrol_ckpt.zip -d .
```

### 5. Download SMPLX:
You can download the [SMPLX](https://smpl-x.is.tue.mpg.de/) for visualization, including SMPLX_NEUTRAL.npz and SMPLX_NEUTRAL.pkl.

### 6. Download Prepared Segmentation Results:
You can download the prepared segmentation results in folder demo_scene from [Google Drive](https://drive.google.com/file/d/18swtyToST19yO7J0thWE8zI_7Zz6R-oZ/view?usp=drive_link).

Notably, the pointcloud of scene0604_00_vh_clean.ply must download from [ScanNet](http://www.scan-net.org/).

## Motion Generation
You can change the scene and the caption of the motion in demo.sh.

Notably, before the motion generation, you must input your openai's api key.
```
cd /scripts
bash demo.sh
bash visualize.sh
```

## Acknowledgements

Some codes are borrowed from [MDM](https://github.com/GuyTevet/motion-diffusion-model?tab=readme-ov-file), [HUMANISE](https://github.com/Silverster98/HUMANISE), [OmniControl](https://github.com/neu-vi/OmniControl).

## Citation
If you find TSTMotion useful for your work please cite:
```
@misc{guo2025tstmotiontrainingfreesceneawaretexttomotion,
      title={TSTMotion: Training-free Scene-aware Text-to-motion Generation}, 
      author={Ziyan Guo and Haoxuan Qu and Hossein Rahmani and Dewen Soh and Ping Hu and Qiuhong Ke and Jun Liu},
      year={2025},
      eprint={2505.01182},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2505.01182}, 
}
```
