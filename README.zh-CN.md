# 翻译服务器

翻译服务器将您的 iOS 设备转变为本地翻译 API 服务器。基于 iOS 原生 Translation 框架，本应用程序提供完全离线的翻译服务，支持自动语言检测和多语言对翻译。通过简洁的 Web API 接口，开发者和用户可以轻松将高质量的翻译功能集成到任何项目中，同时确保数据隐私和安全性。

[English](README.md) | [日本語](README.ja.md) | [繁體中文](README.zh-TW.md) | **简体中文** | [한국어](README.ko.md) | [Français](README.fr.md)

![image](image.jpg)

## 功能特色

- 自动检测源语言
- 支持多种翻译语言对
- 简洁易用的 Web API，方便集成
- 所有处理均在设备上进行，确保隐私与安全

## 使用方法

**通过 `translate` API 进行翻译**

1. 在应用程序中下载所需的语言模型。
2. 自动检测源语言并指定目标语言：
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<您的IP>:8080/translate \
      -d '{ "target": "en", "text": "こんにちは、世界" }'
    ```

3. 指定源语言和目标语言：
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<您的IP>:8080/translate \
      -d '{ "source": "zh-Hant", "target": "en", "text": "你好，世界" }'
    ```

4. Python 示例：
    ```python
    import requests

    url = "http://10.0.1.13:8080/translate"  # 替换为您的 IP 地址

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

5. JSON 响应格式如下：
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
    `translated` 字段包含翻译后的文本内容。

6. 语言列表：
    ```
    "en": "英语",
    "en-US": "英语（美国）",
    "en-GB": "英语（英国）",
    "zh-Hans": "中文（简体）",
    "zh-Hant": "中文（繁体）",
    "ja": "日语",
    "ko": "韩语",
    "fr": "法语",
    "de": "德语",
    "es": "西班牙语",
    "pt": "葡萄牙语",
    "it": "意大利语",
    "nl": "荷兰语",
    "ru": "俄语",
    "uk": "乌克兰语",
    "pl": "波兰语",
    "tr": "土耳其语",
    "ar": "阿拉伯语",
    "hi": "印地语",
    "th": "泰语",
    "vi": "越南语",
    "id": "印尼语",
    ```

7. 为确保应用程序持续运行不中断，请启用 iOS [引导式访问](https://support.apple.com/zh-cn/111795)模式并保持屏幕开启。