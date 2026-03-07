```bash
pip install requests pillow pandas
```

```bash
ollama pull llava
```

```bash
import requests
import base64
import json
import os
import pandas as pd

OLLAMA_URL = "http://localhost:11434/api/generate"
MODEL = "llava"

PROMPT = """
You are a receipt parser.

From the receipt image extract ALL line items.

Return JSON in this format:

{
  "store": "store name",
  "date": "YYYY-MM-DD",
  "items": [
    {
      "name": "item name",
      "quantity": number,
      "price": number,
      "total": number,
      "group": "category"
    }
  ]
}

Possible groups:
- groceries
- restaurant
- office
- electronics
- transport
- household
- other

Only return valid JSON.
"""


def encode_image(path):
    with open(path, "rb") as f:
        return base64.b64encode(f.read()).decode("utf-8")


def process_receipt(image_path):

    image_base64 = encode_image(image_path)

    payload = {
        "model": MODEL,
        "prompt": PROMPT,
        "images": [image_base64],
        "stream": False
    }

    response = requests.post(OLLAMA_URL, json=payload)
    result = response.json()["response"]

    try:
        parsed = json.loads(result)
        return parsed
    except:
        print("Failed to parse JSON")
        print(result)
        return None


def process_folder(folder):

    results = []

    for file in os.listdir(folder):

        if file.lower().endswith((".jpg", ".jpeg", ".png")):

            path = os.path.join(folder, file)
            print("Processing:", file)

            data = process_receipt(path)

            if not data:
                continue

            store = data.get("store")
            date = data.get("date")

            for item in data.get("items", []):

                results.append({
                    "file": file,
                    "store": store,
                    "date": date,
                    "name": item.get("name"),
                    "quantity": item.get("quantity"),
                    "price": item.get("price"),
                    "total": item.get("total"),
                    "group": item.get("group")
                })

    return pd.DataFrame(results)


if __name__ == "__main__":

    df = process_folder("receipts")

    print(df)

    df.to_csv("parsed_receipts.csv", index=False)
    df.to_json("parsed_receipts.json", orient="records")
```

alternative. However, when category doesn't match AI should be use
```bash
RULES = {
    "milk": "groceries",
    "bread": "groceries",
    "diesel": "transport",
    "gasoline": "transport",
    "printer": "office"
}

def classify_item(name):

    name = name.lower()

    for key in RULES:
        if key in name:
            return RULES[key]

    return "other"
```