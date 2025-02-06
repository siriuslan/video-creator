# video-creator
# 文字转语音 (TTS) API 

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


# 上传示例视频 API 

## 端点
**POST** `/upload-sample-video`

## 描述
此 API 用于上传示例视频。

## 请求
### 请求头
- `Content-Type: multipart/form-data`
- `Accept: application/json`

### 请求体
**媒体类型:** `multipart/form-data`

#### 请求参数:
- `video` *(必填)*: `string($binary)` - 需要上传的视频文件。
- `user_id`: `string` - 用户唯一标识。

## 响应
### 200 - 成功响应
**媒体类型:** `application/json`

#### 示例响应:
```json
"上传成功"
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
      "loc": ["body", "video"],
      "msg": "视频文件是必需的",
      "type": "value_error.missing"
    }
  ]
}
```

## 备注
- `video` 字段必须是二进制格式的视频文件。
- `user_id` 是有效的字符串。
- 成功响应返回上传结果的字符串。
- 验证错误返回 `422` 状态码，并包含详细的错误信息。


# 请求生成视频 API 

## 端点
**POST** `/generate-video-url`

## 描述
此 API 用于生成带音频的视频 URL。

## 请求
### 请求头
- `Content-Type: application/json`
- `Accept: application/json`

### 请求体
**媒体类型:** `application/json`

#### JSON 模式:
```json
{
  "video_url": "string",
  "audio_url": "string"
}
```

#### 示例请求体:
```json
{
  "video_url": "https://example.com/sample-video.mp4",
  "audio_url": "https://example.com/sample-audio.mp3"
}
```

## 响应
### 200 - 成功响应
**媒体类型:** `application/json`

#### 示例响应:
```json
"https://example.com/generated-video.mp4"
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
      "loc": ["body", "video_url"],
      "msg": "视频 URL 是必需的",
      "type": "value_error.missing"
    }
  ]
}
```

## 备注
- `video_url` 和 `audio_url` 都是必填字段，必须是有效的 URL。
- 成功响应返回生成的视频文件的 URL。
- 验证错误返回 `422` 状态码，并包含详细的错误信息。

# 视频生成结果查询 API 

## 端点
**POST** `/result-query`

## 描述
此 API 用于查询视频处理结果。

## 请求
### 请求头
- `Content-Type: application/json`
- `Accept: application/json`

### 请求体
**媒体类型:** `application/json`

#### JSON 模式:
```json
{
  "video_id": "string"
}
```

#### 示例请求体:
```json
{
  "video_id": "abc123"
}
```

## 响应
### 200 - 成功响应
**媒体类型:** `application/json`

#### 示例响应:
```json
"处理完成"
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
      "loc": ["body", "video_id"],
      "msg": "视频 ID 是必需的",
      "type": "value_error.missing"
    }
  ]
}
```

## 备注
- `video_id` 是必填字段，必须是有效的字符串。
- 成功响应返回查询结果的字符串。
- 验证错误返回 `422` 状态码，并包含详细的错误信息。


