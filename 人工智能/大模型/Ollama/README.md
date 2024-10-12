# Ollama

curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "Why is the sky blue?"
}'


curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "word: live",
  "stream": false
}'


curl http://localhost:11434/api/generate -d '{
  "model": "llama3",
  "prompt": "vocabulary: broadcast",
  "params": {  
        "language": "zh"
    }  ,
  "stream": false
}'

curl http://localhost:11434/api/generate -d '{
  "model": "mistral",
  "prompt": "vocabulary: broadcast",
  "params": {  
        "language": "zh-cn"
    }  ,
  "stream": false
}'


curl http://localhost:11434/api/chat?language=zh-CN -d '{
  "model": "llama3",
  "messages": [
    {
      "role": "user",
      "content": "vocabulary: live"
    }
  ],
  "stream": false
}'

curl http://localhost:11434/api/chat -d '{
  "model": "llama3",
  "messages": [
    {
      "role": "user",
      "content": "message的英语解释、示例及其翻译"
    }
  ],
  "stream": false
}'


curl http://localhost:11434/api/chat -d '{
  "model": "mistral",
  "messages": [
    {
      "role": "user",
      "content": "vocabulary: live"
    }
  ],
  "stream": false
}'


curl http://localhost:11434/api/chat -d '{
  "model": "llama3",
  "messages": [
    {
      "role": "user",
      "content": "why is the sky blue?"
    }
  ],
  "stream": false
}'


curl http://localhost:11434/api/generate -d '{
  "model": "mistral",
  "prompt": "live",
  "stream": false
}'

