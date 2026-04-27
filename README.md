# 딥러닝 수업 프로젝트: 이미지 컬러화

국민대학교 딥러닝 수업에서 한국 음식 이미지 colorization을 주제로 ChromaGAN, DeOldify, InstColorization을 비교한 팀 프로젝트입니다.

## 개요

| 항목 | 내용 |
| --- | --- |
| 수업 | 딥러닝 |
| 기간 | 2022.09 - 2022.12 |
| 데이터 | AI Hub 한국 음식 이미지 |
| 과제 | grayscale image colorization fine-tuning과 모델 비교 |
| 평가 | PSNR, SSIM, 정성 비교 |

## 접근

- AI Hub 음식 이미지를 224x224 컬러/그레이 페어로 변환하고 train/test split을 구성했습니다.
- ChromaGAN PyTorch remake를 한국 음식 데이터에 맞게 fine-tuning했습니다.
- DeOldify는 pretrained inference를 수행하고 fine-tuning 제약을 기록했습니다.
- InstColorization은 weight 확보 실패 등 재현 과정의 한계를 노트북에 남겼습니다.
- PSNR/SSIM과 정성 결과를 함께 비교했습니다.

## 저장소 구성

```text
.
├── notebooks/
│   ├── 00_data_preparation.ipynb
│   ├── 01_chromagan_pipeline.ipynb
│   ├── 02_deoldify_pipeline.ipynb
│   ├── 03_instcolorization_pipeline.ipynb
│   └── 04_evaluation.ipynb
└── reports/
    └── Deep-Learning-Project.pdf
```

## 공개 범위

AI Hub 원본 데이터, clone한 third-party model repository, 학습 weight, 생성 이미지는 포함하지 않았습니다. 노트북에는 재현 흐름과 실험 제약을 정리했습니다.

## 링크

- [AI Hub 한국 음식 이미지 데이터](https://www.aihub.or.kr/aihubdata/data/view.do?dataSetSn=79)
- [ChromaGAN](https://github.com/pvitoria/ChromaGAN)
- [DeOldify](https://github.com/jantic/DeOldify)
- [InstColorization](https://github.com/ericsujw/InstColorization)
