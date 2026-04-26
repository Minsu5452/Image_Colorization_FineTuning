# DL Team Project — Image Colorization Fine-Tuning

> 2022-2학기 국민대학교 **딥러닝** 학부 수업 팀 프로젝트입니다. AI Hub 한국 음식 이미지 데이터셋을 사용해, **ChromaGAN / DeOldify / InstColorization** 세 가지 SOTA colorization 모델을 사전학습 → fine-tune 하고 한국 음식 이미지에서의 colorization 품질을 비교했습니다.

## Overview

| 항목 | 내용 |
| --- | --- |
| 수업 | 딥러닝 (국민대학교 학부 강의) |
| 기간 | 2022.09 ~ 2022.12 |
| 팀 구성 | 3인팀, 팀원 |
| 과제 | 한국 음식 이미지에 대한 colorization fine-tuning + 모델 비교 |
| 데이터 | AI Hub `한국 이미지(음식)` (150종 × 1,000장, 224×224 resize) |
| Train / Test | 12,922 / 2,465 |
| 평가지표 | PSNR, SSIM (정성 비교 병행) |
| 환경 | Google Colab Pro (GPU) |

## Approach

| 모델 | 결과 | 비고 |
| --- | --- | --- |
| ChromaGAN | **fine-tune 성공** (10 epochs / lr=2e-5 / bs=1) | 한국 음식 텍스처를 살린 정성 결과 확보. Discriminator loss 후반 발산, Generator loss -0.05 부근 안정. |
| DeOldify | pre-trained inference 만 성공 | fastai 1.x + 메모리 한계로 fine-tune 단계 진행 실패. |
| InstColorization | 학습 실패 | 원작자 pre-train weight 의 Google Drive URL 만료 — 일부 checkpoint 만 우회 다운로드 가능했고 완전한 weight set 은 미확보. |

### Stages

1. **데이터 준비** — AI Hub 한식 zip 들을 풀어 224×224 컬러/그레이 페어 생성, 12,922:2,465 split.
2. **ChromaGAN** — `superhighlevel/ChromaGan_Pytorch_Remake` (PyTorch 재구현) 을 clone, `config.py` 만 한국 음식 데이터셋 경로로 교체하여 학습.
3. **DeOldify** — `jantic/DeOldify` clone, Artistic 사전학습 weight 로 한국 음식 inference. fine-tune 코드는 노트북에 보존하되 주석 처리.
4. **InstColorization** — `ericsujw/InstColorization` clone, detectron2 0.1.2 + torch 1.5 환경 셋업. pre-train weight 다운로드 우회 시도 → 실패 케이스 그대로 기록.
5. **평가** — PSNR + SSIM 으로 모델별 평균값 비교 (PSNR/SSIM 은 perceptual quality 와 늘 일치하지는 않아 정성 비교를 병행).

## Repository Structure

```text
.
├── notebooks/
│   ├── 00_data_preparation.ipynb       # AI Hub 한식 → 224x224 컬러/그레이 페어 + train/test split
│   ├── 01_chromagan_pipeline.ipynb     # clone + fine-tune (10 epochs) + inference
│   ├── 02_deoldify_pipeline.ipynb      # clone + 사전학습 inference + fine-tune 시도
│   ├── 03_instcolorization_pipeline.ipynb  # clone + weight 우회 + inference 시도
│   └── 04_evaluation.ipynb             # PSNR / SSIM 모델별 비교
├── reports/
│   └── Deep-Learning-Project.pdf       # 발표 자료 (최종 제출본)
├── .gitignore
└── README.md
```

## Public Scope

이 저장소는 포트폴리오 공개용으로 정리한 버전입니다.

- 원본 저장소에는 `Chroma_gan/`, `DeOldify/`, `InstColorization/` 세 third-party 코드 (jantic/DeOldify, ericsujw/InstColorization, superhighlevel/ChromaGan_Pytorch_Remake) 가 그대로 들어가 있었습니다. 본 공개본에서는 third-party 코드 묶음을 제거하고, 노트북 안에서 `git clone` 으로 가져오는 형태로 정리했습니다.
- AI Hub 데이터, 학습된 모델 weight, fine-tune 산출물은 포함하지 않습니다 (`.gitignore` 로 차단).
- 보고서는 `reports/Deep-Learning-Project.pdf` 로 보존했습니다 (발표 최종본).
- 노트북 출력 결과와 실행 메타데이터는 포함하지 않은 상태로 작성했습니다.

## Links

- [AI Hub — 한국 이미지(음식)](https://www.aihub.or.kr/aihubdata/data/view.do?dataSetSn=79)
- [ChromaGAN (원본, TF)](https://github.com/pvitoria/ChromaGAN)
- [ChromaGan_Pytorch_Remake (사용한 PyTorch 재구현)](https://github.com/superhighlevel/ChromaGan_Pytorch_Remake)
- [DeOldify](https://github.com/jantic/DeOldify)
- [InstColorization](https://github.com/ericsujw/InstColorization)
