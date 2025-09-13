# Serveur de Traduction

Le Serveur de Traduction transforme votre appareil iOS en serveur d'API de traduction local. Basé sur le framework de traduction natif d'iOS, cette application fournit des services de traduction complètement hors ligne avec prise en charge de la détection automatique de langue et des paires de traduction multilingues. Grâce à une interface Web API claire, les développeurs et utilisateurs peuvent facilement intégrer des capacités de traduction de haute qualité dans n'importe quel projet tout en garantissant la confidentialité et la sécurité des données.

[English](README.md) | [日本語](README.ja.md) | [繁體中文](README.zh-TW.md) | [简体中文](README.zh-CN.md) | [한국어](README.ko.md) | **Français**

![image](image.jpg)

## Fonctionnalités

- Détection automatique de la langue source
- Support pour plusieurs paires de traduction
- API Web simple et claire pour une intégration facile
- Tout le traitement reste sur l'appareil, garantissant confidentialité et sécurité

## Utilisation

**Traduire via l'API `translate`**

1. Téléchargez le modèle de langue requis dans l'application.
2. Détection automatique de la langue source et spécification de la langue cible :
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<VOTRE IP>:8080/translate \
      -d '{ "target": "en", "text": "こんにちは、世界" }'
    ```

3. Spécifier les langues source et cible :
    ```
    curl -H "Accept: application/json" \
      -H "Content-Type: application/json" \
      -X POST http://<VOTRE IP>:8080/translate \
      -d '{ "source": "zh-Hant", "target": "en", "text": "你好，世界" }'
    ```

4. Exemple Python :
    ```python
    import requests

    url = "http://10.0.1.13:8080/translate"  # Remplacez par votre adresse IP

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

5. Format de réponse JSON :
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
    Le champ `translated` contient le contenu textuel traduit.

6. Liste des langues :
    ```
    "en": "Anglais",
    "en-US": "Anglais (États-Unis)",
    "en-GB": "Anglais (Royaume-Uni)",
    "zh": "Chinois",
    "zh-Hans": "Chinois (Simplifié)",
    "zh-Hant": "Chinois (Traditionnel)",
    "zh-HK": "Chinois (Hong Kong)",
    "zh-TW": "Chinois (Taïwan)",
    "ja": "Japonais",
    "ko": "Coréen",
    "fr": "Français",
    "fr-CA": "Français (Canada)",
    "de": "Allemand",
    "es": "Espagnol",
    "es-ES": "Espagnol (Espagne)",
    "es-419": "Espagnol (Amérique Latine)",
    "pt": "Portugais",
    "pt-PT": "Portugais (Portugal)",
    "pt-BR": "Portugais (Brésil)",
    "it": "Italien",
    "nl": "Néerlandais",
    "ru": "Russe",
    "uk": "Ukrainien",
    "pl": "Polonais",
    "cs": "Tchèque",
    "sk": "Slovaque",
    "sl": "Slovène",
    "hr": "Croate",
    "sr": "Serbe",
    "bg": "Bulgare",
    "ro": "Roumain",
    "hu": "Hongrois",
    "el": "Grec",
    "tr": "Turc",
    "he": "Hébreu",
    "ar": "Arabe",
    "fa": "Persan",
    "ur": "Ourdou",
    "hi": "Hindi",
    "bn": "Bengali",
    "ta": "Tamoul",
    "te": "Telugu",
    "th": "Thaï",
    "vi": "Vietnamien",
    "id": "Indonésien",
    "ms": "Malais",
    "fil": "Filipino",
    "sv": "Suédois",
    "no": "Norvégien",
    "nb": "Norvégien (Bokmål)",
    "da": "Danois",
    "fi": "Finnois"
    ```
