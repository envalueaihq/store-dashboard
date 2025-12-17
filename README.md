# 🎯 LG전자 지점 평가 대시보드 자동 생성 시스템

**6개 CSV 파일만 업데이트하면 최신 대시보드가 자동 생성됩니다!**

[![Dashboard](https://img.shields.io/badge/Dashboard-Live-red?style=for-the-badge&logo=lg)](https://yourusername.github.io/lg-dashboard-auto/)
[![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

---

## 📌 주요 기능

✅ **6개 CSV 자동 처리** - 데이터만 붙여넣으면 끝  
✅ **AI 피드백 자동 생성** - 채널별 맞춤형 분석  
✅ **권한별 로그인** - 임원/관리자/매니저 구분  
✅ **실시간 진척률 평가** - 오늘 날짜 기준 자동 계산  
✅ **모바일 최적화** - 반응형 디자인  
✅ **GitHub Pages 자동 배포** - 별도 서버 불필요  

---

## 🚀 빠른 시작

### 1단계: 저장소 클론

```bash
git clone https://github.com/yourusername/lg-dashboard-auto.git
cd lg-dashboard-auto
```

### 2단계: CSV 파일 업데이트

**`data/` 폴더에 6개 CSV 파일을 복사하세요:**

```
data/
├── 인원.csv          # 사원 정보 (ID, 지점명, 사원명, 직책, 로그인)
├── Gross.csv         # 매출 실적 데이터
├── 경쟁력.csv        # 경쟁력 M/S 데이터
├── MB실판.csv        # Must&Best 제품 실판
├── MB총판.csv        # Must&Best 제품 총판
└── 구독.csv          # 구독 실적 데이터
```

### 3단계: 대시보드 자동 생성

```bash
python3 generate_final_dashboard.py
```

### 4단계: 결과 확인

```bash
# 생성된 파일 확인
ls -lh dashboard.html

# 브라우저에서 열기
open dashboard.html  # macOS
xdg-open dashboard.html  # Linux
```

---

## 📂 프로젝트 구조

```
lg-dashboard-auto/
│
├── generate_final_dashboard.py    # 🔥 핵심 자동 생성 스크립트
├── data/                           # 📊 CSV 데이터 폴더 (여기에 최신 파일 복사)
│   ├── 인원.csv
│   ├── Gross.csv
│   ├── 경쟁력.csv
│   ├── MB실판.csv
│   ├── MB총판.csv
│   └── 구독.csv
│
├── docs/                           # 🌐 GitHub Pages 배포 폴더
│   └── index.html                  # 자동 생성된 대시보드
│
├── README.md                       # 📖 이 파일
├── requirements.txt                # 📦 필요 패키지
└── .gitignore                      # 🚫 Git 무시 파일

```

---

## 🤖 AI 피드백 시스템

### 채널별 맞춤형 분석

| 채널 | 판매 패턴 | AI 피드백 특징 |
|------|----------|--------------|
| **이마트/홈플러스** | 월초 집중 (50% → 30% → 20%) | 월 진척률 대비 실적 분석 |
| **전자랜드/하이마트** | 균등 분산 (일 3.2%) | 일반적인 진척률 평가 |

### 피드백 예시

✅ **우수한 경우:**
> "전반적으로 우수한 실적을 보이고 있습니다. 매출 목표 달성률이 우수하며, 경쟁력 M/S가 개선되고 있습니다."

⚠️ **개선 필요:**
> "전반적인 실적 개선이 시급합니다. 대형마트 채널 특성상 월초 실적이 중요합니다. 월중 이후 추가 프로모션을 통한 만회가 필요합니다."

---

## 🔐 로그인 시스템

### 권한 구조

| 권한 | 인원 | 기능 |
|------|------|-----|
| **임원** | 18명 | 전체 147개 지점 선택 가능 |
| **관리자** | 60명 | 전체 147개 지점 선택 가능 |
| **매니저** | 265명 | 본인 지점만 고정 표시 |

### 로그인 방법

1. 브라우저에서 `dashboard.html` 열기
2. **사번(ID)** 입력
3. 임원/관리자: 지점 선택 드롭다운 사용
4. 매니저: 자동으로 본인 지점 표시

---

## 📊 대시보드 구성

### 8개 평가 테이블

| 번호 | 항목 | 가중치 |
|------|-----|--------|
| 1 | **Gross 실적** | 10% |
| 2 | **경쟁력 M/S** | 30% |
| 3-6 | **Must&Best 제품** (로봇청소기, 스타일러, 식기세척기, 스탠바이미) | 20% (각 5%) |
| 7-8 | **구독 실적** (목표 달성률 35%, 비중 5%) | 40% |

---

## 🌐 GitHub Pages 자동 배포

### GitHub 저장소 설정

1. **저장소 생성**
   ```bash
   # GitHub에서 새 저장소 생성: lg-dashboard-auto
   ```

2. **로컬 저장소 연결**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: Dashboard auto-generator"
   git branch -M main
   git remote add origin https://github.com/yourusername/lg-dashboard-auto.git
   git push -u origin main
   ```

3. **GitHub Pages 활성화**
   - 저장소 → Settings → Pages
   - Source: `main` 브랜치, `/docs` 폴더 선택
   - Save 클릭

4. **배포 URL 확인**
   ```
   https://yourusername.github.io/lg-dashboard-auto/
   ```

---

## 🔄 CSV 업데이트 워크플로우

### 매월 데이터 갱신 절차

```bash
# 1. 최신 CSV 파일을 data/ 폴더에 복사
cp /path/to/new/인원.csv data/
cp /path/to/new/Gross.csv data/
cp /path/to/new/경쟁력.csv data/
cp /path/to/new/MB실판.csv data/
cp /path/to/new/MB총판.csv data/
cp /path/to/new/구독.csv data/

# 2. 대시보드 자동 생성
python3 generate_final_dashboard.py

# 3. 생성된 dashboard.html을 docs/index.html로 복사
cp dashboard.html docs/index.html

# 4. GitHub에 푸시
git add .
git commit -m "Update: $(date +%Y-%m-%d) 데이터 반영"
git push origin main

# 5. 1~2분 후 자동 배포 완료!
```

---

## 📱 카카오톡 자동 배포

### 방법 1: 카카오톡 API 사용 (개발자용)

```python
# kakao_share.py
import requests

KAKAO_API_KEY = 'your_api_key_here'
DASHBOARD_URL = 'https://yourusername.github.io/lg-dashboard-auto/'

def send_kakao_message(user_ids, message):
    headers = {'Authorization': f'Bearer {KAKAO_API_KEY}'}
    data = {
        'receiver_uuids': user_ids,
        'template_object': {
            'object_type': 'feed',
            'content': {
                'title': '📊 LG전자 지점 평가 대시보드 업데이트',
                'description': message,
                'link': {'web_url': DASHBOARD_URL}
            }
        }
    }
    response = requests.post('https://kapi.kakao.com/v1/api/talk/friends/message/default/send', 
                             headers=headers, json=data)
    return response.json()

# 사용 예시
send_kakao_message(['uuid1', 'uuid2'], '12월 17일 최신 데이터가 반영되었습니다.')
```

### 방법 2: 카카오톡 링크 수동 공유

1. **대시보드 URL 복사**
   ```
   https://yourusername.github.io/lg-dashboard-auto/
   ```

2. **카카오톡에서 전송**
   - 임원/관리자 단체 채팅방에 링크 공유
   - 자동으로 프리뷰 카드 생성됨

---

## 🛠️ 기술 스택

| 항목 | 기술 |
|------|-----|
| **언어** | Python 3.8+ |
| **라이브러리** | pandas (데이터 처리) |
| **프론트엔드** | HTML5, CSS3, JavaScript (Vanilla) |
| **배포** | GitHub Pages |
| **디자인** | LG Red (#A50034, #E60028) |

---

## 📋 필수 조건

```bash
# Python 버전 확인
python3 --version  # Python 3.8 이상

# pandas 설치
pip install pandas

# 또는 requirements.txt 사용
pip install -r requirements.txt
```

---

## 🔧 커스터마이징

### AI 피드백 임계값 수정

`generate_final_dashboard.py` 파일의 142~159줄:

```python
# 종합 판단 (현재 기준)
if total_score >= 80:
    summary = "✅ 전반적으로 우수한 실적을 보이고 있습니다."
    level = "excellent"
elif total_score >= 60:
    summary = "🟢 양호한 수준의 실적을 유지하고 있습니다."
    level = "good"
# ... (필요시 수정)
```

### 채널별 판매 패턴 조정

`generate_final_dashboard.py` 파일의 185~195줄:

```python
# 대형마트 채널 인사이트
if is_hypermarket:
    if performance_gap < -20:  # 임계값 조정 가능
        channel_insight = "대형마트 채널 특성상 월초 실적이 중요합니다..."
```

---

## 📞 문제 해결

### 자주 묻는 질문 (FAQ)

**Q1: CSV 파일 인코딩 오류**
```bash
# UTF-8-BOM으로 저장되었는지 확인
file -I data/인원.csv

# 인코딩 변환 (필요시)
iconv -f EUC-KR -t UTF-8 data/인원.csv > data/인원_utf8.csv
```

**Q2: 대시보드가 빈 화면으로 표시됨**
```bash
# 브라우저 콘솔(F12)에서 오류 확인
# JSON 데이터가 올바르게 임베딩되었는지 확인
grep "ALL_BRANCHES_DATA" dashboard.html
```

**Q3: GitHub Pages 배포 후 404 오류**
```bash
# docs/index.html 파일이 존재하는지 확인
ls -la docs/index.html

# GitHub Pages 설정 확인 (저장소 설정 → Pages → /docs 폴더 선택)
```

---

## 📈 향후 계획

- [ ] GitHub Actions 자동화 (CSV 업로드 시 자동 생성)
- [ ] 카카오톡 자동 전송 API 통합
- [ ] 주간/월간 PDF 리포트 자동 생성
- [ ] 히스토리 기능 (과거 데이터 비교)
- [ ] 관리자 대시보드 (전체 지점 순위)

---

## 📄 라이선스

MIT License - 자유롭게 사용하세요!

---

## 👨‍💻 작성자

**LG Electronics Dashboard Team**  
📧 문의: your.email@example.com

---

## 🙏 감사의 말

이 프로젝트는 LG전자 지점 평가 시스템의 효율성을 높이기 위해 제작되었습니다.

---

**⭐ 이 프로젝트가 도움이 되셨다면 GitHub Star를 눌러주세요!**
