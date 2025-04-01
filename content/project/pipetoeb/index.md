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

---

## 주요 기능

### 1) PDE_HED 계산

수식:

$$
\text{PDE}_{\mathrm{HED}} \;=\; \frac{\bigl(\text{HED} \times \text{Weight}\bigr)}{\bigl(F2 \times F3 \times F4 \times F5 \times F6 \times a \times S\bigr)}
$$

- **HED** (Human Equivalent Dose)와 **Weight**(근로자 체중) 정보를 이용해 \(\text{PDE}\)를 구합니다.

### 2) PDE_F1 계산

수식:

$$
\text{PDE}_{F1} \;=\; \frac{\Bigl(\frac{\text{PoD}}{F1} \times \text{Weight}\Bigr)}
{\bigl(F2 \times F3 \times F4 \times F5 \times F6 \times a \times S\bigr)}
$$

- **PoD**(Point of Departure) 값을 **F1**으로 나누어 **HED**를 대체하는 방식으로 계산합니다.

### 3) OEB 등급 판정

- 계산된 \(\text{PDE}\)를 범위별로 나누어 **OEB 1 ~ 6**를 부여합니다.  
- 예를 들어,  
  - \( < 0.1\,\mu g/m^3 \) → OEB 6  
  - \( < 1\,\mu g/m^3 \) → OEB 5  
  - …  
  - \( 1,000 \sim 5,000 \,\mu g/m^3 \) → OEB 1  

---

## 사용 방법

1. **입력값 설정**  
   - **PoD (mg/day), HED (mg/day), Weight (kg)** 등을 연구나 문헌에 따라 입력합니다.  
   - **F1 ~ F6**: 물질 특이적 불확실성(종간 외삽, 개인차, 시험기간, 중대한 독성, NOEL 미확립, 추가 안전계수 등)을 고려하는 계수입니다.  
   - \(\alpha\)(a), **S**: 노출 경로 상이로 인한 흡수율 차이와 장기 노출 시 체내 축적을 고려하는 계수입니다.

2. **결과 확인**  
   - \(\text{PDE}_{\mathrm{HED}}\), \(\text{PDE}_{F1}\) 두 값이 동시에 산출되고, 해당 값에 따른 **OEB 등급**을 표로 확인할 수 있습니다.  
   - 값이 낮을수록 독성이 높거나 안전계수를 크게 적용했다는 뜻이므로, 작업장 안전수준을 더 강화해야 합니다.

---

## 참고 사항

- 본 **PIPET OEB Calculator**는 **잠정적 위험도 평가**를 위한 보조 도구이므로, 최종 의사결정 전에 반드시 전문 독성학자와 논의해야 합니다.  
- **F1 ~ F6** 설정은 물질별·시험별 특성을 고려해 신중히 결정해야 합니다.  
- **OEB 등급**은 **일반적 구간**에 기반하므로, 회사 내규나 국가별 규제와 함께 종합적으로 검토하시기 바랍니다.

