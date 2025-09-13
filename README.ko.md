# 번역 서버

번역 서버는 iOS 기기를 로컬 번역 API 서버로 변환합니다. iOS 네이티브 번역 프레임워크를 기반으로 하여, 이 앱은 완전한 오프라인 번역 서비스를 제공하며 자동 언어 감지 및 다국어 번역 쌍을 지원합니다. 깔끔한 Web API 인터페이스를 통해 개발자와 사용자는 고품질 번역 기능을 모든 프로젝트에 쉽게 통합할 수 있으며, 동시에 데이터 개인정보 보호와 보안을 보장합니다.

[English](README.md) | [日本語](README.ja.md) | [繁體中文](README.zh-TW.md) | [简体中文](README.zh-CN.md) | **한국어** | [Français](README.fr.md)

![image](image.jpg)

## 기능

- 자동 소스 언어 감지
- 다중 번역 쌍 지원
- 쉬운 통합을 위한 간단하고 깔끔한 Web API
- 모든 처리가 기기에서 이루어져 개인정보 보호와 보안 보장

## 사용 방법

**`translate` API를 통한 번역**

1. 앱에서 필요한 언어 모델을 다운로드하세요.
2. 소스 언어를 자동 감지하고 대상 언어 지정:
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<귀하의IP>:8080/translate \
      -d '{ "target": "en", "text": "こんにちは、世界" }'
    ```

3. 소스 언어와 대상 언어 지정:
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<귀하의IP>:8080/translate \
      -d '{ "source": "zh-Hant", "target": "en", "text": "你好，世界" }'
    ```

4. Python 예제:
    ```python
    import requests

    url = "http://10.0.1.13:8080/translate"  # 귀하의 IP 주소로 교체하세요

    headers = {
        "Accept": "application/json",
        "Content-Type": "application/json"
    }
    data = {
        "target": "en",
        "text": "こんにちは、世界"
    }
    response = requests.post(url, headers=headers, json=data)

    print("status code:", response.status_code)
    print("json response:", response.json())
    ```

5. JSON 응답 형식:
    ```
    {
        "success":true,
        "message":"OK",
        "translated":"Hello, world",
        "source":"Japanese",
        "target":"English"
        "availability":"installed",
    }
    ```
    `translated` 필드에 번역된 텍스트 내용이 포함됩니다.

6. 언어 목록:
    ```
    "en": "영어",
    "en-US": "영어 (미국)",
    "en-GB": "영어 (영국)",
    "zh": "중국어",
    "zh-Hans": "중국어 (간체)",
    "zh-Hant": "중국어 (번체)",
    "zh-HK": "중국어 (홍콩)",
    "zh-TW": "중국어 (대만)",
    "ja": "일본어",
    "ko": "한국어",
    "fr": "프랑스어",
    "fr-CA": "프랑스어 (캐나다)",
    "de": "독일어",
    "es": "스페인어",
    "es-ES": "스페인어 (스페인)",
    "es-419": "스페인어 (라틴 아메리카)",
    "pt": "포르투갈어",
    "pt-PT": "포르투갈어 (포르투갈)",
    "pt-BR": "포르투갈어 (브라질)",
    "it": "이탈리아어",
    "nl": "네덜란드어",
    "ru": "러시아어",
    "uk": "우크라이나어",
    "pl": "폴란드어",
    "cs": "체코어",
    "sk": "슬로바키아어",
    "sl": "슬로베니아어",
    "hr": "크로아티아어",
    "sr": "세르비아어",
    "bg": "불가리아어",
    "ro": "루마니아어",
    "hu": "헝가리어",
    "el": "그리스어",
    "tr": "터키어",
    "he": "히브리어",
    "ar": "아랍어",
    "fa": "페르시아어",
    "ur": "우르두어",
    "hi": "힌디어",
    "bn": "벵골어",
    "ta": "타밀어",
    "te": "텔루구어",
    "th": "태국어",
    "vi": "베트남어",
    "id": "인도네시아어",
    "ms": "말레이어",
    "fil": "필리핀어",
    "sv": "스웨덴어",
    "no": "노르웨이어",
    "nb": "노르웨이어 (보크몰)",
    "da": "덴마크어",
    "fi": "핀란드어"
    ```
