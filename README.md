# Translation Server

Translation Server transforms your iOS device into a local translation API server. Based on iOS's native Translation framework, this app provides completely offline translation services with support for automatic language detection and multilingual translation pairs. Through a clean Web API interface, developers and users can easily integrate high-quality translation capabilities into any project while ensuring data privacy and security.

![image](image.jpg)

## Features:

- Automatic source language detection
- Support for multiple translation pairs
- Simple and clean Web API for easy integration
- All processing stays on-device, ensuring privacy and security

## How to Use

**Translate via translate API**

1. Download the required language model in the app.
2. Automatically detect the source language and specify the target language:
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<YOUR IP>:8080/translate \
      -d '{ "target": "en", "text": "こんにちは、世界" }'
    ```

3. Specify source and target languages:
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<YOUR IP>:8080/translate \
      -d '{ "source": "zh-Hant", "target": "en", "text": "你好，世界" }'
    ```

4. Python example:
    ```python
    import requests

    url = "http://10.0.1.13:8080/translate"  # Replace with your IP address

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

5. The JSON response looks like this:
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
    The "translated" field contains the translated text content.

6. Language list:
    ```
    "en": "English",
    "en-US": "English (United States)",
    "en-GB": "English (United Kingdom)",
    "zh": "Chinese",
    "zh-Hans": "Chinese (Simplified)",
    "zh-Hant": "Chinese (Traditional)",
    "zh-HK": "Chinese (Hong Kong)",
    "zh-TW": "Chinese (Taiwan)",
    "ja": "Japanese",
    "ko": "Korean",
    "fr": "French",
    "fr-CA": "French (Canada)",
    "de": "German",
    "es": "Spanish",
    "es-ES": "Spanish (Spain)",
    "es-419": "Spanish (Latin America)",
    "pt": "Portuguese",
    "pt-PT": "Portuguese (Portugal)",
    "pt-BR": "Portuguese (Brazil)",
    "it": "Italian",
    "nl": "Dutch",
    "ru": "Russian",
    "uk": "Ukrainian",
    "pl": "Polish",
    "cs": "Czech",
    "sk": "Slovak",
    "sl": "Slovenian",
    "hr": "Croatian",
    "sr": "Serbian",
    "bg": "Bulgarian",
    "ro": "Romanian",
    "hu": "Hungarian",
    "el": "Greek",
    "tr": "Turkish",
    "he": "Hebrew",
    "ar": "Arabic",
    "fa": "Persian",
    "ur": "Urdu",
    "hi": "Hindi",
    "bn": "Bengali",
    "ta": "Tamil",
    "te": "Telugu",
    "th": "Thai",
    "vi": "Vietnamese",
    "id": "Indonesian",
    "ms": "Malay",
    "fil": "Filipino",
    "sv": "Swedish",
    "no": "Norwegian",
    "nb": "Norwegian Bokmål",
    "da": "Danish",
    "fi": "Finnish"
    ```
