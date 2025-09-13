# 翻譯伺服器

翻譯伺服器將您的 iOS 裝置轉變為本地翻譯 API 伺服器。基於 iOS 原生 Translation 框架，本應用程式提供完全離線的翻譯服務，支援自動語言偵測和多語言對翻譯。透過簡潔的 Web API 介面，開發者和使用者可以輕鬆整合高品質的翻譯功能到任何專案中，同時確保資料隱私和安全性。

[English](README.md) | [日本語](README.ja.md) | **繁體中文** | [简体中文](README.zh-CN.md) | [한국어](README.ko.md) | [Français](README.fr.md)

![image](image.jpg)

## 功能特色

- 自動偵測來源語言
- 支援多種翻譯語言對
- 簡潔易用的 Web API，方便整合
- 所有處理皆在裝置上進行，確保隱私與安全

## 使用方法

**透過 `translate` API 進行翻譯**

1. 在應用程式中下載所需的語言模型。
2. 自動偵測來源語言並指定目標語言：
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<您的IP>:8080/translate \
      -d '{ "target": "en", "text": "こんにちは、世界" }'
    ```

3. 指定來源語言和目標語言：
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<您的IP>:8080/translate \
      -d '{ "source": "zh-Hant", "target": "en", "text": "你好，世界" }'
    ```

4. Python 範例：
    ```python
    import requests

    url = "http://10.0.1.13:8080/translate"  # 替換為您的 IP 地址

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

5. JSON 回應格式如下：
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
    `translated` 欄位包含翻譯後的文字內容。

6. 語言清單：
    ```
    "en": "英文",
    "en-US": "英文（美國）",
    "en-GB": "英文（英國）",
    "zh": "中文",
    "zh-Hans": "中文（簡體）",
    "zh-Hant": "中文（繁體）",
    "zh-HK": "中文（香港）",
    "zh-TW": "中文（台灣）",
    "ja": "日文",
    "ko": "韓文",
    "fr": "法文",
    "fr-CA": "法文（加拿大）",
    "de": "德文",
    "es": "西班牙文",
    "es-ES": "西班牙文（西班牙）",
    "es-419": "西班牙文（拉丁美洲）",
    "pt": "葡萄牙文",
    "pt-PT": "葡萄牙文（葡萄牙）",
    "pt-BR": "葡萄牙文（巴西）",
    "it": "義大利文",
    "nl": "荷蘭文",
    "ru": "俄文",
    "uk": "烏克蘭文",
    "pl": "波蘭文",
    "cs": "捷克文",
    "sk": "斯洛伐克文",
    "sl": "斯洛維尼亞文",
    "hr": "克羅埃西亞文",
    "sr": "塞爾維亞文",
    "bg": "保加利亞文",
    "ro": "羅馬尼亞文",
    "hu": "匈牙利文",
    "el": "希臘文",
    "tr": "土耳其文",
    "he": "希伯來文",
    "ar": "阿拉伯文",
    "fa": "波斯文",
    "ur": "烏爾都文",
    "hi": "印地文",
    "bn": "孟加拉文",
    "ta": "泰米爾文",
    "te": "泰盧固文",
    "th": "泰文",
    "vi": "越南文",
    "id": "印尼文",
    "ms": "馬來文",
    "fil": "菲律賓文",
    "sv": "瑞典文",
    "no": "挪威文",
    "nb": "挪威文（巴克摩）",
    "da": "丹麥文",
    "fi": "芬蘭文"
    ```
