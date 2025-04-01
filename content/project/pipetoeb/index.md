+++
# Project title.
title = "PIPET OEB calculator"

# Date this page was created.
date = 2025-04-01T00:00:00

# Project summary to display on homepage.
summary = "PIPET OEB calculator"

# Tags: can be used for filtering projects.
# Example: `tags = ["machine-learning", "deep-learning"]`
tags = ["PK", "OEB", "toxicology"]

# Optional external URL for project (replaces project detail page).
#external_link = ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references 
#   `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
#slides = "example-slides"

# Links (optional).
url_pdf = ""
url_slides = ""
url_video = ""
url_code = "https://github.com/pipetcpt/pipetoeb"

# Custom links (optional).
#   Uncomment line below to enable. For multiple links, use the form `[{...}, {...}, {...}]`.
links = [{icon_pack = "fas", icon="tablet-alt", name="App", url = "https://hayoung98.shinyapps.io/pipetoeb"}]

# Featured image
# To use, add an image named `featured.jpg/png` to your project's folder. 
[image]
  # Caption (optional)
  caption = "Photo by PIPET"
  
  # Focal point (optional)
  # Options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
  focal_point = "Smart"
+++

<https://hayoung98.shinyapps.io/pipetoeb>


# PIPET OEB Calculator

이 웹 애플리케이션은 의약·바이오·화학 분야의 작업환경 위험도 평가를 위해 **PDE (Permitted Daily Exposure)** 값을 계산하고, 해당 수치에 따른 **OEB (Occupational Exposure Band)** 등급을 판정하는 도구입니다.  
\(\text{PDE}\)는 특정 물질이 인체에 노출되어도 무해하다고 간주되는 허용 범위를 의미하며, 이를 기반으로 작업환경에서의 안전조치를 결정하게 됩니다.

## 주요 기능

1. **PDE_HED** 계산  
   - \(\text{HED}\) (Human Equivalent Dose)와 작업자 체중(Weight)을 이용하여 산출합니다.  
   - 식:  
     \[
       \text{PDE}_{\mathrm{HED}} = \frac{\bigl(\text{HED} \times \text{Weight}\bigr)}
       {F2 \times F3 \times F4 \times F5 \times F6 \times \alpha \times S}
     \]
2. **PDE_F1** 계산  
   - \(\text{PoD}\) (Point of Departure)를 \(\text{F1}\)으로 나눈 값을 사용해 \( \text{HED} \)를 대체하고, 이를 통해 PDE를 구합니다.  
   - 식:  
     \[
       \text{PDE}_{F1} = \frac{\bigl(\frac{\text{PoD}}{F1} \times \text{Weight}\bigr)}
       {F2 \times F3 \times F4 \times F5 \times F6 \times \alpha \times S}
     \]
3. **OEB 등급 판정**  
   - 계산된 \(\text{PDE}\)를 구간별로 구분하고, “OEB 1”~“OEB 6” 등급을 부여합니다.  
   - 예:  
     - \(<0.1\) µg/m³ → **OEB 6**  
     - \(<1\) µg/m³ → **OEB 5**  
     - ...  
     - \(1,000 \sim 5,000\) µg/m³ → **OEB 1**  

## 사용 방법

1. **입력값 설정**  
   - **PoD (mg/day), HED (mg/day), Weight (kg)** 등을 본인의 실험 데이터나 문헌 결과에 맞춰 입력하세요.  
   - **F1 ~ F6**: 독성학적 불확실성을 고려하는 계수이며, 각 항목의 범위(1~10)와 기본값(1)을 조정해 보수적 수준을 선택할 수 있습니다.  
   - \(\alpha\)(a), **S**: 노출 경로가 달라서 흡수율이 달라지는 경우(예: 경구→흡입)나, 장기 노출로 인해 체내에 물질이 축적되는 경우에 대한 보정 계수입니다.

2. **결과 확인**  
   - \(\text{PDE}_{\mathrm{HED}}\)와 \(\text{PDE}_{F1}\) 두 값이 동시에 계산되며, 각 값에 대응되는 **OEB** 등급이 표로 제시됩니다.  
   - PDE 값이 낮을수록 위험도가 높으므로, 작업장 안전 수준을 강화해야 할 필요가 있습니다.

## 참고 사항

- 이 계산기는 **잠정적 위험도 평가**를 위한 보조도구일 뿐, 규제당국의 공식 가이드라인을 대체하지 않습니다.  
- **F1 ~ F5, F6**는 매우 물질 특이적인 요소로, 전문가의 판단과 **독성 데이터**(NOAEL, PoD, LD50, LOEL 등)를 종합해 결정해야 합니다.  
- **OEB** 등급은 **폭넓은 기준**을 참고하여 개발되었으며, 실제 산업현장 적용 시 회사 내규나 지역 규제기관의 정책을 병행 고려하길 권장합니다.  

---

*마지막으로, 본 **PIPET OEB Calculator**를 통해 도출된 값과 등급은 각 작업환경·물질에 따라 오차가 발생할 수 있으며, 전문 독성학자와 협의하여 최종 안전기준을 확정해야 합니다.*
