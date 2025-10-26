### 파일 업로드
```python
for file_info in uploader.value:
    filename = file_info['name']
    content = file_info['content']

    # memoryview → bytes 변환
    if isinstance(content, memoryview):
        content = content.tobytes()

    # 파일 저장
    with open(filename, 'wb') as f:
        f.write(content)

    print(f"{filename} 저장 완료!")

print(uploader.value)
```


### 이미지 curl
```python
import requests
from PIL import Image
from io import BytesIO

# 이미지 URL
image_url = "https://.....webp"

# 1️⃣ URL에서 이미지 데이터를 바이트로 가져오기
response = requests.get(image_url)
image_bytes = response.content  # raw bytes

# 2️⃣ Bytes를 PIL Image 객체로 변환
image = Image.open(BytesIO(image_bytes)).convert("RGB")  # RGB로 변환 (투명도 제거)

# 3️⃣ PNG로 저장
output_path = "output.png"
image.save(output_path, format="PNG")

print(f"✅ PNG로 저장 완료: {output_path}")
```
