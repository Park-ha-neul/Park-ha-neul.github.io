---
layout: post
title: Jekyll font 변경하는 방법
date: July 3, 2022
tags: [Blog]
---

## intro

---

- vscode로 jekyll 테마 블로그 작업을 진행하던 중 기존 font가 마음에 들지않아서 폰트를 변경하는 작업을 진행하려고 한다.
- 그 중에서도 구글 폰트로 변경하는 방법을 진행하려고 한다.

## process

---

**STEP1. 어떤 파일을 수정해야할지 확인**

- 기존 font를 F12로 확인해본다.
    
    ![Untitled](https://user-images.githubusercontent.com/52904676/177034663-1e329ac0-b9e6-4873-a061-963e819a6222.png)
    
- text-font로 묶여있는걸 확인할 수 있다.
- vscode에 text-font를 검색한다. (ctrl + shift + f)
    - _variables.scss에 text-font가 지정되어 있는걸 확인할 수 있음

**STEP2. 구글 폰트에서 원하는 글꼴 선택**

- text-font를 구글 폰트에 있는 폰트로 변경하려고 한다.

1. [구글 폰트](https://fonts.google.com/?subset=korean)에서 원하는 글꼴 찾기
    
    ![Untitled 1](https://user-images.githubusercontent.com/52904676/177034689-a4df6b65-cf61-4a3a-b9f8-1e799450bd93.png)

 
2. 원하는 폰트의 **+ Select this style** 클릭
    
    ![Untitled 2](https://user-images.githubusercontent.com/52904676/177034702-d6715ef3-bdb6-4df8-b498-f71fc09bf958.png)
    
3. 선택한 글꼴의 @import 코드 생성 확인

![Untitled 3](https://user-images.githubusercontent.com/52904676/177034709-74fb1072-5a5e-4eea-a0d6-93b1a00b2919.png)

**STEP3. 파일에 구글 폰트 적용**

- 선택한 구글 폰트를 scss에 적용하는 작업을 진행한다.
- 파일은 크게 styles.scss, _variables.scss 수정 작업을 진행했다.
    - styles.scss
    
    ```scss
    @import url('https://fonts.googleapis.com/css2?family=Jua&display=swap');
    ```
    
    - _variables.scss
    
    ```scss
    // --text-font: Times, "Times New Roman", "Free Serif", "Noto Serif", TimesNewRomanPSMT, "Droid Serif";
    --text-font: 'Gothic A1', sans-serif;
    
    // --code-font: SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono", "Courier New", monospace;
    --code-font: 'Nanum Gothic Coding', sans-serif;
    ```
    
    - 주석 처리는 기존 font이다.

## result

---

- 폰트 변경 before/after 비교
    - before (text-font)
    
    ![Untitled 4](https://user-images.githubusercontent.com/52904676/177034713-9f0d9d03-4853-4d6e-a817-26fb43b05bac.png)
    
    - after (text-font)
        
    ![Untitled 5](https://user-images.githubusercontent.com/52904676/177034720-6b3999b8-c798-4ac1-9709-2c2386a246f3.png)

        

## reference

---

1. [구글 폰트 적용 방법](https://imweb.me/faq?mode=view&category=29&category2=38&idx=71695)
2. [jekyll font 변경 방법](https://codesyun.tistory.com/116)