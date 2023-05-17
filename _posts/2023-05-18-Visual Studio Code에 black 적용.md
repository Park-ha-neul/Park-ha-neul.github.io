---
layout: post
title: Visual Studio Code에 black 적용
date: May 17, 2023
tags: [개념, python]
---

## 개요

---

- Pycharm으로 common-svc를 개발했을 때 code-formatter로 `black` 을 사용했었다.
- 통합으로 관리하면서 pycharm에서 vs-code 로 개발 툴을 변경하면서 vs-code에 `black`을 적용하는 것이 필요해졌다.

## vs-code black 적용

---

### 1. black 설치

```bash
pip install black 
```

### 2. VSCode 에서 formatting provider 설정

vscode setting에 들어가서 formatting provider를 검색하여 아래 기본값에서 black 으로 변경 

![Untitled](https://github.com/Park-ha-nule/Park-ha-nule.github.io/assets/52904676/a936d642-6eee-421b-9c7c-df5da5e78252)

### 3. VSCode 에서 settings.json 편집

- VSCode 에서 **‘Ctrl + Shift + P’** 를 눌러 명령 팔레트 열기
- **Preferences: Open Settings (JSON)** 검색

![Untitled 1](https://github.com/Park-ha-nule/Park-ha-nule.github.io/assets/52904676/6be33973-5ac5-473c-9fd4-432b3d44b9e6)

- settings.json 파일에 아래 코드 추가

```json
"python.formatting.provider": "black",
"python.formatting.blackArgs": ["--line-length", "100"],
"editor.formatOnSave": true,
```

### 4. 테스트

- 다른 python file에서 줄바꿈을 해서 저장을 하면 해당 줄바꿈이 적용안되는지 확인!