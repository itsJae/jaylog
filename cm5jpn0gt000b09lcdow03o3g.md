---
title: "[Project] Schedulize - 효율적이고 생산적인 근무 배정 프로그램"
seoTitle: "[Project] Schedulize - 효율적이고 생산적인 근무 배정 프로그램"
seoDescription: "이번에 새 프로젝트 Schedulize를 소개하게 되어서 굉장히 기쁩니다. 아직 제작 중이지만 현재 80% 완료된 상태이고 최적화를 위해 꾸준한 코드 리팩토링(Refactoring)을 거칠 예정입니다. Schedulize는 영어 Schedule과 Optimize를 합쳐 최적화된"
datePublished: Sun Jan 05 2025 14:30:43 GMT+0000 (Coordinated Universal Time)
cuid: cm5jpn0gt000b09lcdow03o3g
slug: project-schedulize
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1736084758155/4e5f452a-eeaa-425f-a385-a4264c6b13d2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1736087427121/d668e4a6-94fd-484e-a500-784a8a58e443.png
tags: python, projects, system-architecture, openpyxl, personal-project

---

---

## 소개

이번에 새 프로젝트 **Schedulize**를 소개하게 되어서 굉장히 기쁩니다. 아직 제작 중이지만 현재 80% 완료된 상태이고 최적화를 위해 꾸준한 코드 리팩토링(Refactoring)을 거칠 예정입니다. **Schedulize**는 영어 **Schedule**과 **Optimize**를 합쳐 최적화된 스케줄을 제공한다는 것에 초점을 두었습니다. 어떤 프로젝트를 시작하는 데에는 모두가 이유가 있다고 생각합니다. 개인적으로 저는 “혁신”을 위하여 개발합니다. 이번 제 프로젝트는 비효율적이고 비생산적이었던 군 부대의 근무 편성 방식을 해결하기 위하여 시작되었습니다.

군 부대에는 아주 많은 근무들이 있습니다. 예를 들면 CCTV영상 감시, 경계 근무, 불침번, 식기 세척, 분대장, 분리수거, 등등이 있겠습니다. 이런 근무들은 1달 31일 내내 병사들이 교대로 돌아가며 소화하게 됩니다. 지금까지 이 모든 근무들을 관리하는 근무표 작성은 모두 간부님께서 manual로 엑셀 파일에 타자를 치며 만들어야 했습니다. 비효율적인 것을 못 참는 저는 생각했습니다.

> 내가 프로그램 하나 만들어 놓으면 내 후임들, 그리고 다음에 오시는 간부님들은 스트레스 받지 않고 1분만에 근무표 작성을 완료하실 수 있지 않을까?

---

## 그래, 만들어보자

1. 거두절미하고 Notion부터 켜고 Github Repository를 만들었습니다.
    
2. Notion을 켜고 Use cases와 시스템 아키텍처를 설계했습니다.
    
3. 그 후, 어느 정도 프로그램의 방향성이 잡히고 코딩을 시작했습니다.
    
4. Python으로 사용자의 input을 받고, 사용자가 제공한 데이터를 기반으로 그 데이터들을 excel파일로 export합니다.
    
5. Excel 파일로 옮기기 위하여 파이썬의 openpyxl 라이브러리를 사용하였습니다.
    

---

## 결과물

Notion(document): [https://slender-pyroraptor-850.notion.site/Schedulize-169838a6b4e68091b16ff00be5aaae00](https://slender-pyroraptor-850.notion.site/Schedulize-169838a6b4e68091b16ff00be5aaae00)

Github(code): [https://github.com/itsJae/Schedulize](https://github.com/itsJae/Schedulize)

---

## 이번 프로젝트를 통하여 배운 것

기술 관련

1. 파이썬 라이브러리 openpyxl 사용법
    
2. 파이썬 Class 사용으로 코드 자체의 가독성과 유지보수 향상.
    
3. 파이썬 datetime 모듈 사용.
    
    * 각 달이 30일인지 31일인지 28일인지 계산 (예: 10월은 31일까지)
        
    * 주어진 년도와 월에 기반하여 그 달의 1일이 몇 요일인지 계산 (예시: 2025년 1월 1일은 수요일)
        

기술 관련 X

1. 아키텍처 설계의 중요성.
    
2. Use cases 조사의 중요성.
    
3. 실제 사용자와 커뮤니케이션의 중요성.
    
4. 어떻게 할지 고민하면서 미루지 말고 시작부터 하는 것의 중요성.
    
5. ChatGPT Prompt 사용법.
    

---

## 마치며

개발자를 시작하게 된 이유가 세상을 바꾸고 싶어서였습니다. 개발은 말 그대로 우리가 창조해 나가는 것입니다, 즉 세상에 존재하고 있지 않은 것들을 만들어 내는 일이죠. 이번 프로젝트를 통해 가장 크게 배운 것이 “불편한 것이 있으면 앞으로 직접 내가 만들어서 불편함을 해소하고 더 나은 솔루션으로 세상을 더 스마트하게 바꾸자”입니다. Schedulize는 아직 개발 단계이지만 주변 사람들에게 지금까지 만든 프로그램을 보여주며 그들이 놀라하며 감탄할 때 보람을 느끼곤 합니다. 지금 개발중인 Logic이 쉽지는 않습니다만 잘 마무리해서 다음 게시글에서는 완성된 프로젝트로 찾아뵙겠습니다.