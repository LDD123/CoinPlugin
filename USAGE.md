# CoinPlugin 使用说明

## 功能概述

CoinPlugin 是一个 LangBot 插件，用于处理加密货币价格查询请求。当用户发送以 `/` 开头的消息时，插件会自动调用外部 API 并返回结果。

## 工作原理

1. **消息监听**：插件监听个人和群组消息
2. **命令识别**：当收到以 `/` 开头的消息时（如 `/btc`），插件会识别为命令
3. **API 调用**：插件将命令转发到外部 API `http://43.133.54.53:5000/processMsg`
4. **响应处理**：解析 API 返回的响应并发送给用户
5. **消息阻止**：阻止消息继续往下执行，避免重复处理

## 使用方法

### 在个人聊天中

直接发送命令，例如：
- `/btc` - 查询比特币价格
- `/eth` - 查询以太坊价格
- `/doge` - 查询狗狗币价格

### 在群组中

同样发送命令即可：
- `/btc` - 查询比特币价格
- `/eth` - 查询以太坊价格
- `/doge` - 查询狗狗币价格

## API 请求格式

插件会将命令转换为以下格式发送到外部 API：

```json
{
  "data": {
    "msg": {
      "content": "/btc"
    }
  }
}
```

## API 响应格式

外部 API 应返回以下格式的响应：

```json
{
  "content": "BTC_USDT, Last Price: $67363(1%)",
  "status": "success"
}
```

插件会提取 `content` 字段并发送给用户。

## 安装依赖

确保已安装以下依赖：

```bash
uv pip install -r requirements.txt
```

依赖包括：
- `langbot-plugin` - LangBot 插件 SDK
- `aiohttp` - 异步 HTTP 客户端

## 运行插件

使用以下命令运行插件：

```bash
lbp run
```

或者使用 uv：

```bash
uv run lbp run
```

## 项目结构

```
CoinPlugin/
├── main.py                      # 插件主文件
├── manifest.yaml                # 插件配置文件
├── requirements.txt             # 依赖文件
├── components/
│   ├── commands/                # 命令组件
│   │   └── info.py
│   └── event_listener/          # 事件监听器
│       └── default.py           # 默认事件监听器
└── assets/
    └── icon.svg
```

## 注意事项

1. 确保外部 API `http://43.133.54.53:5000/processMsg` 可以正常访问
2. API 返回的响应必须包含 `content` 字段
3. 插件会自动阻止消息继续往下执行，避免重复处理
4. 如果 API 调用失败，插件会发送错误信息给用户

## 故障排除

### API 调用失败

如果遇到 API 调用失败，请检查：
1. 网络连接是否正常
2. API 地址是否正确
3. API 服务是否正常运行

### 消息未被处理

如果消息未被处理，请检查：
1. 消息是否以 `/` 开头
2. 插件是否正在运行
3. LangBot 主程序是否正确配置了插件