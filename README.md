# ArgoCD GitOps Repository

이 리포지토리는 ArgoCD를 사용하여 Kubernetes 클러스터에 배포되는 애플리케이션 및 인프라스트럭처 설정을 관리합니다.

[백엔드 타겟 레포지토리](https://github.com/SangYunLeee/blog-backend)  에서 소스 변경이 일어나면 해당 레포에서 github actions 를 이용하여 이 리포지토리의 Image Tag 를 변경하도록 구성하였습니다.

## 사용 방법
1. 이 리포지토리를 로컬 환경으로 복제합니다.

```bash
git clone https://github.com/SangYunLeee/argocd-enttolog.git
cd argocd-enttolog
```

2. enviroment 를 알맞게 변경한다.
```
cp entto/config/.example.env entto/config/.env
vim entto/config/.env
```
3. 쿠버네티스에 반영한다.
```bash
kubectl --kustomize .
```

## 폴더 구조

- `applications/`: 각 애플리케이션의 Kubernetes 리소스 정의 파일
- `argocd-bootstrap/`: argoCD 설치에 필요한 리소스 정의 파일

```
.
├── applications
│   ├── entto             : 백엔드 프로젝트 관련 폴더 (설정파일 및 리소스 파일)
│   │   ├── config
│   │   └── manifests
│   └── metric            : 메트릭 정보 관련 프로젝트 폴더
│       ├── config
│       └── manifests
├── argocd-bootstrap      : argoCD 설치에 필요한 리소스 정의 파일
│   └── argocd-ingress
│   └── argocd-install
├── kustomization.yaml
└── README.md
```
