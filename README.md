# 🎨 Image Colorization Fine-Tuning — SOTA 모델 파인튜닝

![Year](https://img.shields.io/badge/2022-학회%20프로젝트-blue)
![Task](https://img.shields.io/badge/Task-Computer%20Vision%20%7C%20Colorization-purple)
![Models](https://img.shields.io/badge/Models-DeOldify%20%7C%20ChromaGAN%20%7C%20InstColorization-orange)

> **흑백 이미지 컬러화(Colorization) SOTA 모델 3종 Fine-Tuning 비교 실험** — DeOldify · ChromaGAN · InstColorization. 2022년 D&A 학회 DL 기수 팀 프로젝트.

---

## 🔍 Overview

- **배경**: 흑백 사진·영상 컬러화는 생성형 CV의 대표 응용. 프리트레인된 SOTA 모델을 특정 도메인에 fine-tune하는 실험.
- **범위**: 3개 SOTA 모델 적용·비교 실험.

## 🧠 Approach — 3-Model Benchmark

| 모델 | 특성 |
|------|------|
| **DeOldify** | GAN 기반, NoGAN 학습, 노이즈·색재현 우수 |
| **ChromaGAN** | Perceptual loss + class distribution 활용 |
| **InstColorization** | 인스턴스 단위 컬러화 (detection + colorization) |

## 📁 Structure

```
Image_Colorization_FineTuning/
├── DeOldify/
├── Chroma_gan/
├── InstColorization/
├── Deep-Learing-Project.pdf        # 프로젝트 리포트
└── README.md
```

## 🛠 Tech Stack

- Python · PyTorch · Computer Vision · GAN · Transfer Learning · Jupyter

## 👤 Role

- **역할**: 팀원
- **기여**: SOTA 모델 fine-tuning 실험 · 결과 비교

---

> 🔗 Portfolio: [Minsu5452](https://github.com/Minsu5452)
