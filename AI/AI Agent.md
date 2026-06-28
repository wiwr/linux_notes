# Architecture

```
                +----------------+
                | Receipt Image  |
                | JPG / PNG / PDF|
                +-------+--------+
                        |
                        v
                OCR (extract text)
          Tesseract or PaddleOCR
                        |
                        v
               Extracted Receipt Text
                        |
                        v
          Local LLM (Ollama + Llama3.1)
        Extract structured JSON fields
                        |
                        v
               Validate JSON (Pydantic)
                        |
                        v
                  PostgreSQL Database
                        |
                        v
              Search / Reports / Analytics
```
# Postgres db
	Database to store information
## Ubuntu / Debian

### 1. Update package lists

```
sudo apt update
```

### 2. Install PostgreSQL

```
sudo apt install postgresql postgresql-contrib -y
```

### 3. Start and enable the service

```
sudo systemctl enable postgresqlsudo systemctl start postgresql
```

### 4. Verify it's running

```
sudo systemctl status postgresql
```

You should see:

```
Active: active (running)
```

### 5. Switch to the PostgreSQL user

```
sudo -i -u postgres
```

### 6. Open the PostgreSQL shell

```
psql
```

### 7. Create a database

```
CREATE DATABASE myapp;
```

### 8. Create a user

```
CREATE USER myuser WITH ENCRYPTED PASSWORD 'mypassword';
```

### 9. Grant privileges

```
GRANT ALL PRIVILEGES ON DATABASE myapp TO myuser;
```

### 10. Exit

```
\q
```

Exit the `postgres` user:

```
exit
```

## Verify the installation

Check the version:

```
psql --version
```

Example:

```
psql (PostgreSQL) 17.x
```

List databases:

```
sudo -u postgres psql -c "\l"
```
# Python

## Project Structure
```
\receipt-ai/
│
├── app.py
├── config.py
├── database.py
├── models.py
├── schemas.py
│
├── receipts/
│      receipt1.jpg
│
├── ocr.py
├── extractor.py
├── agent.py
├── repository.py
│
├── prompts/
│      receipt_prompt.txt
│
├── requirements.txt
└── .env
```

# Step 1 Install Python Packages

```
pip install \sqlalchemy \psycopg2-binary \pydantic \python-dotenv \paddleocr \paddlepaddle \ollama \Pillow
```

---

# Step 2 Install Ollama

Install Ollama and download a model:

```
ollama pull llama3.1:8b
```

or

```
ollama pull qwen2.5:7b
```

Start it:

```
ollama serve
```

---

# Step 3 Database Schema

```
CREATE TABLE receipts (    id SERIAL PRIMARY KEY,    merchant TEXT,    receipt_date DATE,    total NUMERIC(10,2),    currency VARCHAR(5),    tax NUMERIC(10,2),    payment_method TEXT,    raw_text TEXT,    created_at TIMESTAMP DEFAULT NOW());
```

---

# Step 4 OCR

```
from paddleocr import PaddleOCRocr = PaddleOCR(use_angle_cls=True)result = ocr.ocr("receipt.jpg")text = "\n".join(    line[1][0]    for page in result    for line in page)print(text)
```

---

# Step 5 Prompt the LLM

```
Extract information from this receipt.Return ONLY valid JSON.{    "merchant":"",    "receipt_date":"",    "total":0,    "currency":"",    "tax":0,    "payment_method":""}Receipt:{{receipt_text}}
```

---

# Step 6 Python Extraction

```
import ollamaimport jsonresponse = ollama.chat(    model="llama3.1:8b",    messages=[        {            "role": "user",            "content": prompt        }    ])data = json.loads(response["message"]["content"])
```

---

# Step 7 Validate

```
from pydantic import BaseModelclass Receipt(BaseModel):    merchant: str    receipt_date: str    total: float    currency: str    tax: float    payment_method: str
```

---

# Step 8 Save to PostgreSQL

```
receipt = Receipt(**data)session.add(    ReceiptDB(        merchant=receipt.merchant,        receipt_date=receipt.receipt_date,        total=receipt.total,        currency=receipt.currency,        tax=receipt.tax,        payment_method=receipt.payment_method,        raw_text=text    ))session.commit()
```

Agent Flow