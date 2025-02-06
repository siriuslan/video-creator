# video-creator
# 文字转语音 (TTS) API 文档

## 端点
**POST** `/tts`

## 描述
此 API 根据提供的文本内容生成一个文字转语音 (TTS) URL。

## 请求
### 请求头
- `Content-Type: application/json`
- `Accept: application/json`

### 请求体
**媒体类型:** `application/json`

#### JSON 模式:
```json
{
  "content": "string"
}
```

#### 示例请求体:
```json
{
  "content": "你好，这是一个测试消息。"
}
```

## 响应
### 200 - 成功响应
**媒体类型:** `application/json`

#### 示例响应:
```json
"https://example.com/generated-tts-url.mp3"
```

### 422 - 验证错误
**媒体类型:** `application/json`

#### JSON 模式:
```json
{
  "detail": [
    {
      "loc": [
        "string",
        0
      ],
      "msg": "string",
      "type": "string"
    }
  ]
}
```

#### 示例响应:
```json
{
  "detail": [
    {
      "loc": ["body", "content"],
      "msg": "字段是必需的",
      "type": "value_error.missing"
    }
  ]
}
```

## 备注
- `content` 字段是必填的，必须是包含要转换为语音的文本的字符串。
- 成功响应返回一个字符串，表示生成的 TTS 音频文件的 URL。
- 验证错误返回 `422` 状态码，并包含详细的错误信息。

