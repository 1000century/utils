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
