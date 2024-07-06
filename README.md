# Awesome-Attacks and Defenses on T2I Diffusion Models

This repository is a curated collection of research papers focused on $\textbf{Adversarial Attacks and Defenses on Text-to-Image Diffusion Models (AD-on-T2IDM)}$.

We will continuously update this collection to track the latest advancements in the field of AD-on-T2IDM.

Welcome to follow and star! If you have any relevant materials or suggestions, please feel free to contact us (zcy@tju.edu.cn) or submit a pull request.

For more detailed information, please refer to our survey papers: [coming soon]().



## Citation

```latex
Coming soon
```



## Abstract

Recently, the text-to-image diffusion model has gained considerable attention from the community due to its exceptional image generation capability. A representative model, Stable Diffusion, amassed more than 10 million users within just two months of its release. This surge in popularity has facilitated studies on the **robustness** and **safety** of the model, leading to the proposal of various adversarial attack methods.  Simultaneously, there has been a marked increase in research focused on defense methods to improve the robustness and safety of these models. In this survey, we provide a comprehensive review of the literature on adversarial attacks and defenses targeting text-to-image diffusion models. We begin with an overview of popular text-to-image diffusion models, followed by an introduction to a taxonomy of adversarial attacks and an in-depth review of existing attack methods. We then present a detailed analysis of current defense methods that improve model robustness and safety. Finally, we discuss ongoing challenges and explore promising future research directions.

## Overview of AD-on-T2IDM

### Two key concerns in T2IDM: Robustness and Safety

The **robustness** ensures that the model can generate images with consistent semantics in response to diverse prompts inputted by users in practice.

The **safety** prevents the misuse of the model in creating malicious images, such as sexual, violent, and political images, etc.

### Adversarial attacks

Based on the intent of the adversary, existing attack methods can be divided into two primary categories: untargeted and targeted attacks. 

- For untargeted attacks, consider a scenario with a prompt input by the user~($\textbf{clean prompt}$) and its corresponding output image~($\textbf{clean image}$). The objective of untargeted attacks is to subtly perturb the clean prompt to craft an $\textbf{adversarial prompt}$, further misleading the victim model to generate an $\textbf{adversarial image}$ with semantics different from the clean image. This type of attack is commonly used to uncover the vulnerability in **the robustness** of the victim model. Some untargeted attacks are shown as follows:

  ![untargeted attacks](./picture/untargeted_attacks.png)

- For targeted attacks, assumes that the victim model has built-in $\textbf{safeguards}$ to filter $\textbf{malicious prompts}$ and resultant $\textbf{malicious images}$. These prompts and images often explicitly contain $\textbf{malicious concepts}$, such as 'nudity', 'violence', and other predefined concepts. The objective of targeted attacks is to obtain an $\textbf{adversarial prompt}$, which can bypass these safeguards while inducing the victim model to generate $\textbf{adversarial images}$ containing malicious concepts. This type of attack is typically designed to reveal the vulnerability in the **safety** of the victim model. Some targeted attacks are shown as follows:

  ![targeted attacks](./picture/targeted_attacks.png)

### Defenses

Based on the defense goal, existing defense methods can be classified into two categories: 1) **improving model robustness** and 2) **improving model safety**. 

- The goal of robustness is to ensure that generated images have consistent semantics with diverse input prompts in practical applications. Specifically, according to the adversarial attack, the defense methods are asked to mitigate the robustness vulnerabilities in  two types of input prompts: 1) the prompt with multiple objects and attributes, and 2) the grammatically incorrect prompt with the subtle noise.
- The safety goal is to prevent the generation of malicious images in response to both malicious and adversarial prompts. Specifically, malicious prompts explicitly contain malicious concepts, while adversarial prompts cleverly omit these concepts. Moreover, based on the knowledge of the model, existing safety methods can be classified into two categories: external safeguards and internal safeguards. The external safeguards focus on detecting or correcting the malicious prompt before feeding the prompt into the text-to-image model. In contrast, internal safeguards aim to ensure that the semantics of output images deviate from those of malicious images by modifying internal parameters and features within the model.

Notably, although many methods are proposed to improve the model robustness against the prompt with multiple objects and attributes, this collection omits related papers on this part since there has been related surveys, such as controllable image generation [[PDF]](https://arxiv.org/pdf/2403.04279), the development and advancement of image generation capabilities [[PDF-1]](https://arxiv.org/pdf/2209.02646), [[PDF-2]](https://arxiv.org/pdf/2209.00796), [[PDF-3]](https://arxiv.org/pdf/2401.11631). Moreover, for ungrammatically incorrect prompts with subtle noise, mature solutions are still lacking. Therefore, this collection mainly focuses on the defense methods for improving model safety.

## :grinning:Paper List

- [Adversarial Attacks](#Adversarial-Attacks)
  - [Untargeted Attacks](#Untargeted-Attacks)
    - [White-Box](#White-Box)
    - [Black-Box](#Black-Box)
  - [Targeted Attacks](#Targeted-Attacks)
    - [Attack for External Safeguards](#Attack-for-External-Safeguards)
    - [Attack for Internal Safeguards](#Attack-for-Internal-Safeguards)
    - [Attack for Black-Box Safeguards](#Attack-for-Black-Box-Safeguards)
- [Defenses for Improving Safety](#Defenses-for-Improving-Safety)
  - [External Safeguards](#External-Safeguards)
    - [Prompt Classifier](#Prompt-Classifier)
    - [Prompt Transformation](#Prompt-Transformation)
  - [Internal Safeguards](#Internal-Safeguards)
    - [Model Editing](#Model-Editing)
    - [Inference Guidance](#Inference-Guidance)

### :imp:<a name="Adversarial-Attacks">Adversarial Attacks</a>

#### :collision:<a name="Untargeted-Attacks">Untargeted Attacks</a>

##### :pouting_cat:<a name="White-Box">White-Box</a>

**Stable diffusion is unstable** 

*Chengbin Du, Yanxi Li, Zhongwei Qiu, Chang Xu*

NeurIPS 2024. [[PDF]](https://proceedings.neurips.cc/paper_files/paper/2023/file/b733cdd80ed2ae7e3156d8c33108c5d5-Paper-Conference.pdf)



**A pilot study of query-free adversarial attack against stable diffusion**

*Haomin Zhuang, Yihua Zhang*

CVPRW 2023. [[PDF](https://openaccess.thecvf.com/content/CVPR2023W/AML/papers/Zhuang_A_Pilot_Study_of_Query-Free_Adversarial_Attack_Against_Stable_Diffusion_CVPRW_2023_paper.pdf)]



##### :see_no_evil:<a name="Black-Box">Black-Box</a>

**Evaluating the Robustness of Text-to-image Diffusion Models against Real-world Attacks**

*Hongcheng Gao , Hao Zhang , Yinpeng Dong, Zhijie Deng*

arxiv 2023. [[PDF](https://arxiv.org/pdf/2306.13103)]



#### :anger:<a name="Targeted-Attacks">Targeted Attacks</a>

##### :cyclone:<a name="Attack-for-External-Safeguards">Attack for External Safeguards</a>

**Red-Teaming the Stable Diffusion Safety Filter**

*Javier Rando, Daniel Paleka, David Lindner, Lennart Heim, Florian Tramèr*

arxiv 2022. [[PDF](https://arxiv.org/pdf/2210.04610)]



**Black Box Adversarial Prompting for Foundation Models**

*Natalie Maus, Patrick Chao, Eric Wong, Jacob Gardner*

arxiv 2023. [[PDF](https://arxiv.org/pdf/2302.04237)]



**SneakyPrompt: Evaluating Robustness of Text-to-image Generative Models' Safety Filters**

*Yuchen Yang, Bo Hui, Haolin Yuan, Neil Gong, Yinzhi Cao*

Proceedings of the IEEE Symposium on Security and Privacy 2024. [[PDF](https://arxiv.org/pdf/2305.12082)]



**Asymmetric Bias in Text-to-Image Generation with Adversarial Attacks**

*Haz Sameen Shahgir, Xianghao Kong, Greg Ver Steeg, Yue Dong*

arxiv 2023. [[PDF](https://arxiv.org/pdf/2312.14440)]



**Revealing vulnerabilities in stable diffusion via targeted attacks**

*Chenyu Zhang, Lanjun Wang, Anan Liu*

arxiv 2024. [[PDF](https://arxiv.org/abs/2401.08725)]



**Riatig: Reliable and imperceptible adversarial text-to-image generation with natural prompts**

*Han Liu, Yuhao Wu, Shixuan Zhai, Bo Yuan, Ning Zhang*

CVPR 2023. [[PDF](https://openaccess.thecvf.com/content/CVPR2023/papers/Liu_RIATIG_Reliable_and_Imperceptible_Adversarial_Text-to-Image_Generation_With_Natural_Prompts_CVPR_2023_paper.pdf)]



**Mma-diffusion: Multimodal attack on diffusion models**

*Yang, Yijun and Gao, Ruiyuan and Wang, Xiaosen and Ho, Tsung-Yi and Xu, Nan and Xu, Qiang*

CVPR 2024. [[PDF](https://openaccess.thecvf.com/content/CVPR2024/papers/Yang_MMA-Diffusion_MultiModal_Attack_on_Diffusion_Models_CVPR_2024_paper.pdf)]



##### :snake:<a name="Attack-for-Internal-Safeguards">Attack for Internal Safeguards</a>

**Ring-A-Bell! How Reliable are Concept Removal Methods for Diffusion Models?**

*Tsai, Yu-Lin and Hsu, Chia-Yi and Xie, Chulin and Lin, Chih-Hsun and Chen, Jia-You and Li, Bo and Chen, Pin-Yu and Yu, Chia-Mu and Huang, Chun-Ying*

ICLR 2024. [[PDF](https://arxiv.org/pdf/2310.10012)]



**To generate or not? safety-driven unlearned diffusion models are still easy to generate unsafe images... for now**

*Zhang, Yimeng and Jia, Jinghan and Chen, Xin and Chen, Aochuan and Zhang, Yihua and Liu, Jiancheng and Ding, Ke and Liu, Sijia*

arxiv 2023. [[PDF](https://arxiv.org/pdf/2310.11868)]



**Prompting4debugging: Red-teaming text-to-image diffusion models by finding problematic prompts**

*Chin, Zhi-Yi and Jiang, Chieh-Ming and Huang, Ching-Chun and Chen, Pin-Yu and Chiu, Wei-Chen*

ICML 2024. [[PDF](https://arxiv.org/pdf/2309.06135)]



**FLIRT: Feedback Loop In-context Red Teaming**

*Ninareh Mehrabi, Palash Goyal, Christophe Dupuy, Qian Hu, Shalini Ghosh, Richard Zemel, Kai-Wei Chang, Aram Galstyan, Rahul Gupta*

arxiv 2023. [[PDF](https://arxiv.org/pdf/2308.04265)]



**Jailbreaking Prompt Attack: A Controllable Adversarial Attack against Diffusion Models**

*Jiachen Ma, Anda Cao, Zhiqing Xiao, Jie Zhang, Chao Ye, Junbo Zhao*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2404.02928)]



##### :frog:<a name="Attack-for-Black-Box-Safeguards">Attack for Black-Box Safeguards</a>

**Exploiting cultural biases via homoglyphs in text-to-image synthesis**

*Struppek, Lukas and Hintersdorf, Dom and Friedrich, Felix and Schramowski, Patrick and Kersting, Kristian*

Journal of Artificial Intelligence Research 2023. [[PDF](https://www.jair.org/index.php/jair/article/view/15388)]



**Adversarial Attacks on Image Generation With Made-Up Words**

*Raphaël Millière*

arxiv 2022. [[PDF](https://arxiv.org/pdf/2208.04135)]



**SurrogatePrompt: Bypassing the Safety Filter of Text-To-Image Models via Substitution**

*Zhongjie Ba, Jieming Zhong, Jiachen Lei, Peng Cheng, Qinglong Wang, Zhan Qin, Zhibo Wang, Kui Ren*

arxiv 2023. [[PDF](https://arxiv.org/pdf/2309.14122)]



**Divide-and-Conquer Attack: Harnessing the Power of LLM to Bypass Safety Filters of Text-to-Image Models**

*Yimo Deng, Huangxun Chen*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2312.07130)]



**Groot: Adversarial Testing for Generative Text-to-Image Models with Tree-based Semantic Transformation**

Yi Liu, Guowei Yang, Gelei Deng, Feiyue Chen, Yuqi Chen, Ling Shi, Tianwei Zhang, Yang Liu

arxiv 2024. [[PDF](https://arxiv.org/pdf/2402.12100)]



**SneakyPrompt: Evaluating Robustness of Text-to-image Generative Models' Safety Filters**

*Yuchen Yang, Bo Hui, Haolin Yuan, Neil Gong, Yinzhi Cao*

Proceedings of the IEEE Symposium on Security and Privacy 2024. [[PDF](https://arxiv.org/pdf/2305.12082)]



**Mma-diffusion: Multimodal attack on diffusion models**

*Yang, Yijun and Gao, Ruiyuan and Wang, Xiaosen and Ho, Tsung-Yi and Xu, Nan and Xu, Qiang*

CVPR 2024. [[PDF](https://openaccess.thecvf.com/content/CVPR2024/papers/Yang_MMA-Diffusion_MultiModal_Attack_on_Diffusion_Models_CVPR_2024_paper.pdf)]



**Ring-A-Bell! How Reliable are Concept Removal Methods for Diffusion Models?**

*Tsai, Yu-Lin and Hsu, Chia-Yi and Xie, Chulin and Lin, Chih-Hsun and Chen, Jia-You and Li, Bo and Chen, Pin-Yu and Yu, Chia-Mu and Huang, Chun-Ying*

ICLR 2024. [[PDF](https://arxiv.org/pdf/2310.10012)]



### :pill:<a name="Defenses-for-Improving-Safety">Defenses for Improving Safety</a>

#### :surfer:<a name="External-Safeguards">External Safeguards</a>

##### :mountain_bicyclist:<a name="Prompt-Classifier">Prompt Classifier</a>

**Latent Guard: a Safety Framework for Text-to-image Generation**

*Runtao Liu, Ashkan Khakzar, Jindong Gu, Qifeng Chen, Philip Torr, Fabio Pizzati*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2404.08031)]



##### :horse_racing:<a name="Prompt-Transformation">Prompt Transformation</a>

**Universal Prompt Optimizer for Safe Text-to-Image Generation**

*Zongyu Wu, Hongcheng Gao, Yueze Wang, Xiang Zhang, Suhang Wang*

NAACL 2024. [[PDF](https://arxiv.org/pdf/2402.10882)]



**GuardT2I: Defending Text-to-Image Models from Adversarial Prompts**

*Yijun Yang, Ruiyuan Gao, Xiao Yang, Jianyuan Zhong, Qiang Xu*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2403.01446)]



#### :hamburger:<a name="Internal-Safeguards">Internal Safeguards</a>

##### :fries:<a name="Model-Editing">Model Editing</a>

**Erasing concepts from diffusion models**

*Gandikota, Rohit and Materzynska, Joanna and Fiotto-Kaufman, Jaden and Bau, David*

ICCV 2023. [[PDF](https://openaccess.thecvf.com/content/ICCV2023/papers/Gandikota_Erasing_Concepts_from_Diffusion_Models_ICCV_2023_paper.pdf)]



**Ablating concepts in text-to-image diffusion models**

*Kumari, Nupur and Zhang, Bingliang and Wang, Sheng-Yu and Shechtman, Eli and Zhang, Richard and Zhu, Jun-Yan*

ICCV 2023. [[PDF](https://openaccess.thecvf.com/content/ICCV2023/papers/Kumari_Ablating_Concepts_in_Text-to-Image_Diffusion_Models_ICCV_2023_paper.pdf)]



**Unified concept editing in diffusion models**

*Gandikota, Rohit and Orgad, Hadas and Belinkov, Yonatan and Materzy{\'n}ska, Joanna and Bau, David*

WACV 2024. [[PDF](https://openaccess.thecvf.com/content/WACV2024/papers/Gandikota_Unified_Concept_Editing_in_Diffusion_Models_WACV_2024_paper.pdf)]



**Editing implicit assumptions in text-to-image diffusion models**

*Orgad, Hadas and Kawar, Bahjat and Belinkov, Yonatan*

ICCV 2023. [[PDF](https://openaccess.thecvf.com/content/ICCV2023/papers/Orgad_Editing_Implicit_Assumptions_in_Text-to-Image_Diffusion_Models_ICCV_2023_paper.pdf)]



**Towards Safe Self-Distillation of Internet-Scale Text-to-Image Diffusion Models**

*Sanghyun Kim, Seohyeon Jung, Balhae Kim, Moonseok Choi, Jinwoo Shin, Juho Lee*

ICML 2023 Workshop on Challenges in Deployable Generative AI. [[PDF](https://arxiv.org/pdf/2307.05977)]



**ReFACT: Updating Text-to-Image Models by Editing the Text Encoder**

*Dana Arad, Hadas Orgad, Yonatan Belinkov*

NAACL 2024. [[PDF](https://arxiv.org/pdf/2306.00738)]



**Safe-CLIP: Removing NSFW Concepts from Vision-and-Language Models**

*Poppi, Samuele and Poppi, Tobia and Cocchi, Federico and Cornia, Marcella and Baraldi, Lorenzo and Cucchiara, Rita*

arxiv 2024.



**Degeneration-tuning: Using scrambled grid shield unwanted concepts from stable diffusion**

*Ni, Zixuan and Wei, Longhui and Li, Jiacheng and Tang, Siliang and Zhuang, Yueting and Tian, Qi*

ACM MM 2023. [[PDF](https://arxiv.org/pdf/2308.02552)]



**All but One: Surgical Concept Erasing with Model Preservation in Text-to-Image Diffusion Models**

*Hong, Seunghoo and Lee, Juhun and Woo, Simon S*

AAAI 2024. [[PDF](https://ojs.aaai.org/index.php/AAAI/article/view/30107)]



**Unlearning Concepts in Diffusion Model via Concept Domain Correction and Concept Preserving Gradient**

*Yongliang Wu, Shiji Zhou, Mingzhuo Yang, Lianzhe Wang, Wenbo Zhu, Heng Chang, Xiao Zhou, Xu Yang*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2405.15304)]



**R.A.C.E.: Robust Adversarial Concept Erasure for Secure Text-to-Image Diffusion Model**

*Changhoon Kim, Kyle Min, Yezhou Yang*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2405.16341)]



**Receler: Reliable Concept Erasing of Text-to-Image Diffusion Models via Lightweight Erasers**

*Chi-Pin Huang, Kai-Po Chang, Chung-Ting Tsai, Yung-Hsuan Lai, Fu-En Yang, Yu-Chiang Frank Wang*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2311.17717)]



**Defensive Unlearning with Adversarial Training for Robust Concept Erasure in Diffusion Models**

*Yimeng Zhang, Xin Chen, Jinghan Jia, Yihua Zhang, Chongyu Fan, Jiancheng Liu, Mingyi Hong, Ke Ding, Sijia Liu*

arxiv 2024. [[PDF](https://arxiv.org/pdf/2405.15234)]



##### :apple:<a name="Inference-Guidance">Inference Guidance</a>

**Safe Latent Diffusion: Mitigating Inappropriate Degeneration in Diffusion Models**

*Patrick Schramowski, Manuel Brack, Björn Deiseroth, Kristian Kersting*

CVPR 2023. [[PDF](https://openaccess.thecvf.com/content/CVPR2023/papers/Schramowski_Safe_Latent_Diffusion_Mitigating_Inappropriate_Degeneration_in_Diffusion_Models_CVPR_2023_paper.pdf)]



**Self-discovering interpretable diffusion latent directions for responsible text-to-image generation**

*Li, Hang and Shen, Chengzhi and Torr, Philip and Tresp, Volker and Gu, Jindong*

CVPR 2024. [[PDF](https://openaccess.thecvf.com/content/CVPR2024/papers/Li_Self-Discovering_Interpretable_Diffusion_Latent_Directions_for_Responsible_Text-to-Image_Generation_CVPR_2024_paper.pdf)]
