# Google Hotels Scraper

[![Promo](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.co.kr/products/serp-api/google-search/hotels)

Google은 가장 큰 여행 데이터 집계 서비스 중 하나이며, 여기에서 실시간 호텔 데이터를 スクレイピング하는 방법을 안내합니다. 두 가지 방법을 다룹니다:

1. **무료 스크레이퍼**: 소규모 요구 사항에 이상적입니다.
2. **Bright Data Google Hotels API**: 단일 API 호출로 대규모로 공개 Google Hotels 데이터를 수집하기 위한 엔터프라이즈급 솔루션입니다([SERP Scraping API](https://brightdata.co.kr/products/serp-api)의 일부).


## Table of Contents
- [Free Scraper](#free-scraper)
  - [Setup](#setup)
  - [Usage](#usage)
  - [Sample Output](#sample-output)
  - [Limitations](#limitations)
- [Bright Data Google Hotels API](#bright-data-google-hotels-api)
  - [Key Features](#key-features)
  - [Prerequisites](#prerequisites)
  - [Direct API Access](#direct-api-access)
  - [Native Proxy-Based Access](#native-proxy-based-access)
- [Advanced Features](#advanced-features)
  - [Localization Parameters](#localization-parameters)
  - [Booking Parameters](#booking-parameters)
  - [Device Type Parameters](#device-type-parameters)
  - [Response Format](#response-format)
- [Alternative Solutions](#alternative-solutions)
- [Support & Resources](#support--resources)

## Free Scraper

소규모로 Google Hotels 데이터를 추출하기 위한 빠르고 간단한 스크레이퍼입니다.

<img width="800" alt="free-google-hotels-scraper" src="https://github.com/bright-kr/google-hotels-api/blob/main/images/421713152-9e86aabe-c8b7-4286-946a-378cd98c81b3.png" />

### Setup

**요구 사항:**

- [Python 3.9+](https://www.python.org/downloads/)
- 브라우저 자동화를 위한 [Selenium](https://pypi.org/project/selenium/)
- HTML 파싱을 위한 [BeautifulSoup](https://pypi.org/project/beautifulsoup4/)
- `pandas`, `tqdm`, `webdriver-manager` 같은 기타 보조 라이브러리

**설치:**

```bash
pip install pandas tqdm selenium beautifulsoup4 webdriver-manager
```

**참고**: Webスクレイピング이 처음이시라면, [초보자를 위한 Python web scraping 튜토리얼](https://brightdata.co.kr/blog/how-tos/web-scraping-with-python) 또는 [Selenium으로 Web Scraping 하는 방법 가이드](https://brightdata.co.kr/blog/how-tos/using-selenium-for-web-scraping)부터 시작하시는 것을 권장합니다.

### **Usage**
필수 파라미터와 함께 [google-hotels-scraper.py](https://github.com/bright-kr/google-hotels-api/blob/main/google-hotels-scraper/google-hotels-scraper.py) 스크립트를 실행합니다:
```bash
python3 google-hotels-scraper.py --location "Dubai" --max_hotels 200
```
_파라미터:_
- `location` – 호텔 데이터의 대상 위치
- `max_hotels` – スクレイピング할 호텔 수

💡 **Pro Tip:** Google의 スクレイピング 방지 시스템(アンチボット)에 의한 탐지를 줄이려면, 스크립트에서 `options.add_argument("--headless=new")` 라인을 주석 처리하십시오.

### Sample Output
<img width="800" alt="google-hotels-scraper-csv-output" src="https://github.com/bright-kr/google-hotels-api/blob/main/images/421731827-633afbf9-204e-444a-ac0f-23b8b72c5813.png" />


### Limitations

무료 스크레이퍼에는 여러 제약 사항이 있습니다:

- IPアドレス 차단 위험이 높습니다
- リクエスト 볼륨이 제한됩니다
- CAPTCHA가 자주 발생합니다
- 대규모 スクレイピング에는 신뢰성이 떨어집니다

더 크고 신뢰할 수 있는 데이터 수집을 위해 아래의 Bright Data 전용 솔루션을 고려해 보십시오 👇


## Bright Data Google Hotels API
[Bright Data의 Google Hotels API](https://brightdata.co.kr/products/serp-api/google-search/hotels)는 [SERP Scraping API](https://brightdata.co.kr/products/serp-api)의 일부이며, 고급 [proxy network](https://brightdata.co.kr/proxy-types)를 사용합니다. 이를 통해 CAPTCHA나 IPアドレス 차단을 걱정하지 않고 공개 Google Hotels 데이터를 대규모로 수집할 수 있습니다.

### Key Features
- **글로벌 위치 정확도**: 특정 위치에 맞추어 결과를 조정합니다
- **성공 기준 과금 모델**: 성공한 リクエスト에 대해서만 비용을 지불합니다
- **실시간 데이터**: 최신 호텔 정보를 수 초 내로 가져옵니다
- **확장성**: 볼륨 제한 없이 무제한 リクエスト를 처리합니다
- **비용 효율성**: 인프라 및 유지보수 비용을 절감합니다
- **높은 신뢰성**: 내장된 차단 방지(アンチボット) 조치로 일관된 성능을 제공합니다
- **24/7 지원**: 필요할 때 언제든 전문가의 도움을 받을 수 있습니다


### Prerequisites

1. [Bright Data account](https://brightdata.co.kr/)를 생성합니다(신규 사용자는 $5 크레딧 제공)
2. [API key](https://docs.brightdata.com/general/account/api-token)를 생성합니다
3. [단계별 가이드](https://github.com/bright-kr/google-hotels-api/blob/main/setup-serp-api-guide.md)를 따라 SERP API 및 접근 자격 증명을 구성합니다
4. Google Hotels API를 사용하려면 쿼리하려는 호텔의 entity ID가 필요합니다. 다음과 같이 찾을 수 있습니다:
	1. Google에서 호텔 이름을 검색합니다
	2. 마우스 오른쪽 버튼을 클릭하고 "View page source"를 선택합니다
	3. 페이지에서 "/entity"를 검색하여 entity ID를 찾습니다

### Direct API Access

API エンドポイント로 직접 リクエスト를 보냅니다.

**cURL Example:**

```bash
curl https://api.brightdata.com/request \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer API_TOKEN" \
  -d '{
        "zone": "ZONE_NAME",
        "url": "https://www.google.com/travel/hotels/entity/CgoIyNaqqL33x5ovEAE/prices?brd_json=1",
        "format": "raw"
      }'
```

**Python Example:**

```python
import requests
import json

url = "https://api.brightdata.com/request"
headers = {"Content-Type": "application/json", "Authorization": "Bearer API_TOKEN"}

payload = {
    "zone": "ZONE_NAME",
    "url": "https://www.google.com/travel/hotels/entity/CgoIyNaqqL33x5ovEAE/prices?brd_json=1",
    "format": "raw",
}

response = requests.post(url, headers=headers, json=payload)

with open("serp-direct-api.json", "w") as file:
    json.dump(response.json(), file, indent=4)

print("Response saved to 'serp-direct-api.json'.")
```

👉 [전체 JSON 출력](https://github.com/bright-kr/google-hotels-api/blob/main/google-hotels-api-results/serp-direct-api.json)을 확인하십시오.

**참고:** 파싱된 JSON에는 `brd_json=1`을, 파싱된 JSON + 전체 중첩 HTML에는 `brd_json=html`을 사용하십시오.

### Native Proxy-Based Access

Bright Data의 プロキシ 라우팅 방식도 사용할 수 있습니다:

**cURL Example:**

```bash
curl -i \
  --proxy brd.superproxy.io:33335 \
  --proxy-user "brd-customer-<customer-id>-zone-<zone-name>:<zone-password>" \
  -k \
  "https://www.google.com/travel/hotels/entity/CgoIyNaqqL33x5ovEAE/prices?brd_json=html"
```

**Python Example:**

```python
import requests
import urllib3

urllib3.disable_warnings(urllib3.exceptions.InsecureRequestWarning)

host = "brd.superproxy.io"
port = 33335
username = "brd-customer-<customer-id>-zone-<zone-name>"
password = "<zone-password>"
proxy_url = f"http://{username}:{password}@{host}:{port}"

proxies = {"http": proxy_url, "https": proxy_url}
url = "https://www.google.com/travel/hotels/entity/CgoIyNaqqL33x5ovEAE/prices?brd_json=html"
response = requests.get(url, proxies=proxies, verify=False)

with open("serp-native-proxy.html", "w", encoding="utf-8") as file:
    file.write(response.text)

print("Response saved to 'serp-native-proxy.html'.")
```

👉 [전체 JSON 출력](https://github.com/bright-kr/Google-Hotels-API/blob/main/google-hotels-api-results/serp-native-proxy.html)을 확인하십시오.

**참고:** 프로덕션 환경에서는 [SSL Certificate Guide](https://docs.brightdata.com/general/account/ssl-certificate)에 설명된 대로 Bright Data의 SSL 인증서를 로드하십시오.

## Advanced Features

Bright Data의 API는 Google Hotels 데이터 추출을 세밀하게 조정하기 위한 다양한 고급 파라미터를 지원합니다. 아래 예시는 **Native Proxy-Based Access**를 사용하지만, Direct API Access에서도 동일하게 적용할 수 있습니다.

### Localization Parameters

<img width="800" alt="bright-data-google-hotels-scraper-api-localization" src="https://github.com/bright-kr/google-hotels-api/blob/main/images/422299775-d47254c1-0c7f-4572-bf54-f3f55cf66908.png" />


이 파라미터는 검색의 국가와 언어를 정의합니다:

| Parameter | Description | Example |
| --- | --- | --- |
| gl | 두 글자 국가 코드 | `gl=us` (United States) |
| hl | 두 글자 언어 코드 | `hl=en` (English) |

**예시:** 미국에서 호텔을 검색하고 결과는 영어로 표시합니다:

```bash
curl --proxy brd.superproxy.io:33335 --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
"https://www.google.com/travel/hotels/entity/CgoI4NzJmsPmkpU6EAE/prices?gl=us&hl=en"
```

### Booking Parameters

<img width="800" alt="bright-data-google-hotels-scraper-api-booking-params" src="https://github.com/bright-kr/google-hotels-api/blob/main/images/422303757-74faadf7-218b-4fa3-b2d9-d0cecf8e23e6.png" />

이 파라미터는 날짜, 투숙객 수, 무료 취소 가능 여부, 숙소 유형에 따라 결과를 정교하게 필터링하는 데 도움이 됩니다:

| Parameter | Description | Format | Example |
|-----------|-------------|--------|---------|
| brd_dates | 체크인 및 체크아웃 날짜 | YYYY-MM-DD,YYYY-MM-DD | `brd_dates=2025-08-15,2025-08-20` |
| brd_occupancy | 투숙객 수(성인 + 어린이) | `<adults>,<child1_age>,<child2_age>` | `brd_occupancy=3,6,9` (성인 3명, 6세/9세 어린이 2명) |
| brd_free_cancellation | 환불 가능한 예약만 표시 | true or false | `brd_free_cancellation=true` |
| brd_accomodation_type | 숙박 유형 | hotels or vacation_rentals | `brd_accomodation_type=vacation_rentals` |
| brd_currency | 가격 표시 통화 | 3-letter currency code | `brd_currency=GBP` (British Pounds) |


**예시:** 특정 파라미터로 호텔 숙박을 검색합니다:
```bash
curl --proxy brd.superproxy.io:33335 \
  --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
  "https://www.google.com/travel/hotels/entity/CgoIyNaqqL33x5ovEAE/prices\
?brd_dates=2025-04-15,2025-04-20\
&brd_occupancy=3,6,9\
&brd_free_cancellation=true\
&brd_currency=GBP"
```


### Device Type Parameters
기본적으로 リクエスト는 데스크톱 user-agent를 모방하지만, 모바일로 변경할 수 있습니다:

| Parameter | Description | 
|-----------|-------------|
| `brd_mobile=0` | 무작위 데스크톱 user-agent (기본값) | 
| `brd_mobile=1` | 무작위 모바일 user-agent |
| `brd_mobile=ios` | iPhone user-agent |
| `brd_mobile=android` | Android phone user-agent |
| `brd_mobile=ipad` | iPad user-agent |
| `brd_mobile=android_tablet` | Android tablet user-agent |

**예시:** Android phone user-agent로 호텔 데이터를 가져옵니다:

```bash
curl --proxy brd.superproxy.io:33335 --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
"https://www.google.com/travel/hotels/entity/CgoIyNaqqL33x5ovEAE/prices?brd_mobile=android"
```

### Response Format
기본적으로 レスポンス는 HTML이지만, JSON レスポンス를 요청할 수 있습니다:

| Parameter | Description |
|-----------|-------------|
| `brd_json=1` | HTML 대신 JSON レスポンス를 반환합니다 |
| `brd_json=html`	| JSON + 전체 중첩 HTML |

**예시:** JSON 형식으로 호텔 가격 데이터를 가져옵니다:

```bash
curl --proxy brd.superproxy.io:33335 --proxy-user brd-customer-<customer-id>-zone-<zone-name>:<zone-password> \
"https://www.google.com/travel/hotels/entity/CgoIyNaqqL33x5ovEAE/prices?brd_json=1"
```

## Alternative Solutions

[Web Scraper APIs](https://brightdata.co.kr/products/web-scraper) 외에도, Bright Data는 여행 업계 요구에 맞춘 즉시 사용 가능한 [datasets](https://brightdata.co.kr/products/datasets)도 제공합니다:

- [Hotel Datasets](https://brightdata.co.kr/products/datasets/travel/hotels)
- [Airbnb Dataset](https://brightdata.co.kr/products/datasets/airbnb)
- [Expedia Datasets](https://brightdata.co.kr/products/datasets/travel/expedia)
- [Tourism Datasets](https://brightdata.co.kr/products/datasets/tourism)
- [Booking.com Datasets](https://brightdata.co.kr/products/datasets/booking)
- [TripAdvisor Datasets](https://brightdata.co.kr/products/datasets/tripadvisor)


## Support & Resources

- **Documentation**: [SERP API Docs](https://docs.brightdata.com/scraping-automation/serp-api/)
- **Explore Related Guides**: 
  - [Web Unlocker API](https://github.com/bright-kr/web-unlocker-api)
  - [SERP API](https://github.com/bright-kr/serp-api)
  - [Google Search API](https://github.com/bright-kr/google-search-api)
  - [Google News Scraper](https://github.com/bright-kr/Google-News-Scraper)
  - [Google Trends API](https://github.com/bright-kr/google-trends-api)
  - [Google Reviews API](https://github.com/bright-kr/google-reviews-api)
- **Helpful Articles**:
  - [Best SERP APIs](https://brightdata.co.kr/blog/web-data/best-serp-apis)
  - [Build a RAG Chatbot with SERP API](https://brightdata.co.kr/blog/web-data/build-a-rag-chatbot)
- **Use Cases**:
	- [SEO Applications](https://brightdata.co.kr/use-cases/serp-tracking)
	- [Travel Industry Uses](https://brightdata.co.kr/use-cases/travel)
- **Contact**: 도움이 필요하십니까? support@brightdata.com으로 이메일을 보내주십시오