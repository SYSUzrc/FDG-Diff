# FDG-Diff

This is the code repository for the paper:
> **FDG-Diff: Frequency-Domain-Guided Diffusion Framework for Compressed Hazy Image Restoration**
>
> [Ruicheng Zhang](https://github.com/SYSUzrc), Kanghui Tian, [Zeyu Zhang](https://steve-zeyu-zhang.github.io/), Qixiang Liu and [Zhi Jin](https://ieeexplore.ieee.org/author/37086340177)\*
>
> \*Corresponding author
>
> <em><b>ICME 2025</b></em>
> 
> **[[arXiv]](https://arxiv.org/abs/2501.12832)** **[[Paper with Code]](https://paperswithcode.com/paper/fdg-diff-frequency-domain-guided-diffusion)**
<center class ='img'>
<img title="Improvement of FDG-Diff over the SOTA approaches on I-Haze  dataset. The circle size represents the corresponding SSIM values. Higher PSNR and SSIM indicate better performance, while lower FID values are preferred." src="https://github.com/SYSUzrc/FDG-Diff/blob/main/insert/性能对比图.png" width="50%">
</center>



## Citation

If you use any content of this repo for your work, please cite the following our paper:
```
@article{zhang2025fdg,
  title={FDG-Diff: Frequency-Domain-Guided Diffusion Framework for Compressed Hazy Image Restoration},
  author={Zhang, Ruicheng and Tian, Kanghui and Zhang, Zeyu and Liu, Qixiang and Jin, Zhi},
  journal={arXiv preprint arXiv:2501.12832},
  year={2025}
}
```

## Introduction
In this study, we reveal that the interaction between haze degradation and JPEG compression introduces complex joint loss effects, which significantly complicate image restoration.
Existing dehazing models often neglect compression effects, which
limits their effectiveness in practical applications. To address
these challenges, we introduce three key contributions. First,
we design FDG-Diff, a novel frequency-domain-guided dehazing
framework that improves JPEG image restoration by leveraging
frequency-domain information. Second, we introduce the HighFrequency Compensation Module (HFCM), which enhances
spatial-domain detail restoration by incorporating frequencydomain augmentation techniques into a diffusion-based restoration framework. Lastly, the introduction of the DegradationAware Denoising Timestep Predictor (DADTP) module further enhances restoration quality by enabling adaptive regionspecific restoration, effectively addressing regional degradation
inconsistencies in compressed hazy images. Experimental results
across multiple compressed dehazing datasets demonstrate that
our method consistently outperforms the latest state-of-the-art
approaches.
<center class ='img'>
<img title="The track of the JPEG process. The colors in the loss map reflect the
magnitude of the loss, as the absolute loss is computed separately for each
of the three channels. Though compressed at a quite high QF of 80, the hazy
images still suffers severe information loss in hazy regions." src="https://github.com/SYSUzrc/FDG-Diff/blob/main/insert/loss_map.png" width="100%">
</center>

## Pipeline
<center class ='img'>
<img title="Architecture of the proposed network." src="https://github.com/SYSUzrc/FDG-Diff/blob/main/insert/pipeline.png" width="100%">
</center>

## Demo
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <th align="center">Input Condition</th>
    <th align="center">Restoration Process</th>
    <th align="center">Output</th>
  </tr>
  <tr>
    <td align="center"><img src="https://github.com/SYSUzrc/APDM/blob/main/insert/01.png" width="310" height="auto" alt="rd11"></td>
    <td align="center"><img src="https://github.com/SYSUzrc/APDM/blob/main/insert/02_demo.gif" width="310" height="auto" alt="rd12"></td>
    <td align="center"><img src="https://github.com/SYSUzrc/APDM/blob/main/insert/01_output.png" width="310" height="auto" alt="rd13"></td>
  </tr>
  <tr>
    <td align="center"><img src="https://github.com/SYSUzrc/APDM/blob/main/insert/02.png" width="310" height="auto" alt="rd11"></td>
    <td align="center"><img src="https://github.com/SYSUzrc/APDM/blob/main/insert/01_demo.gif" width="310" height="auto" alt="rd12"></td>
    <td align="center"><img src="https://github.com/SYSUzrc/APDM/blob/main/insert/02_output.png" width="310" height="auto" alt="rd13"></td>
  </tr>
</table>


## Installation
### Create a Virtual Environment
```
conda create --name FDG-Diff python=3.7.12
conda activate FDG-Diff
```

### Install Packages
```
pip install -r requirements.txt
```

## Evaluation
### Pre-trained Model Weights
&emsp;We have shared [a pre-trained model](https://pan.baidu.com/s/1zwSrDczDZCYqnGNZOJ7CKA?pwd=1234) on the NH-Haze dataset, with its configuration file designated as `nhaze.yml`. Please place it in the `./ckpts` folder. <br /> 
&emsp;If you wish to test our model on alternative datasets, please retrain the model and organize the datasets in the following manner:
```
|-- FDG-Diff-main
|  |-- dataset_name
|  |  |-- gt
|  |  |-- input
|  |  |-- dataset_name.txt
```

### Dataset Preparation
&emsp;We have prepared the [NH-haze](https://pan.baidu.com/s/1kjlPWNJuHgVXb8jk4nJ28w?pwd=1234)(Extraction Code : 1234), named in accordance with the code requirements. Please deposit it in the root directory of the project.
&emsp;
### Evaluating on the NH-haze Dataset

```bash
python eval_diffusion.py --config "test.yml" --resume 'Nhaze_ddpm.pth.tar' --sampling_timesteps 25 --grid_r 4
```

## Author
📧 : zhangrch23@mail2.sysu.edu.cn

## Acknowledgment
&emsp;This work was supported by the National Natural Science Foundation of China under Grant No.62071500; Supported by Supported by Shenzhen Science and Technology Program under Grant No. JCYJ20230807111107015. Supported by Fundamental Research Funds for the Central Universities, Sun Yat-sen University under Grant No. 241gqb015.
&emsp;*Zhi Jin is the corresponding author. <br />
&emsp;Portions of this code repository are derived from the following works: [WeatherDiffusion](https://github.com/IGITUGraz/WeatherDiffusion) and  [DDPM](https://github.com/ermongroup/ddim). Acknowledgement is extended to these seminal contributions.

<!-- links -->
[your-project-path]: https://github.com/SYSUzrc/FDG-Diff
[contributors-shield]: https://img.shields.io/github/contributors/SYSUzrc/FDG-Diff.svg?style=flat-square 
[contributors-url]: https://github.com/SYSUzrc/FDG-Diff/graphs/contributors 
[forks-shield]: https://img.shields.io/github/forks/SYSUzrc/FDG-Diff.svg?style=flat-square 
[forks-url]: https://github.com/SYSUzrc/FDG-Diff/network/members 
[stars-shield]: https://img.shields.io/github/stars/SYSUzrc/FDG-Diff.svg?style=flat-square 
[stars-url]: https://github.com/SYSUzrc/FDG-Diff/stargazers 
[issues-shield]: https://img.shields.io/github/issues/SYSUzrc/FDG-Diff.svg?style=flat-square 
[issues-url]: https://github.com/SYSUzrc/FDG-Diff/issues 
[license-shield]: https://img.shields.io/github/license/SYSUzrc/FDG-Diff.svg?style=flat-square 
