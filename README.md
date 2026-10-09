# HLY Test Action
版本测试1
[![GitHub Actions](https://img.shields.io/badge/GitHub-Actions-blue)](https://github.com/features/actions)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

一个用于测试和演示的 GitHub Action，可以在 GitHub Workflows 中使用。

## 功能特性

- 📝 支持自定义消息输入
- 🔄 支持重复执行
- ⏰ 返回执行时间戳
- 🎯 简单易用的组合式 Action

## 快速开始

### 基础用法

```yaml
- uses: 649956073/HLYAction-test1@v1
  with:
    message: 'Your custom message'
```

### 完整示例

```yaml
name: Test HLY Action
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Run HLY Action
        id: hly_action
        uses: 649956073/HLYAction-test1@v1
        with:
          message: 'Hello, GitHub Actions!'
          count: '3'
      
      - name: Display outputs
        run: |
          echo "Result: ${{ steps.hly_action.outputs.result }}"
          echo "Timestamp: ${{ steps.hly_action.outputs.timestamp }}"
```

## 输入参数

| 参数 | 说明 | 必需 | 默认值 |
|------|------|------|--------|
| `message` | 要显示的消息 | 否 | `Hello from HLY Action!` |
| `count` | 消息重复次数 | 否 | `1` |

## 输出参数

| 输出 | 说明 |
|------|------|
| `result` | 处理后的结果消息 |
| `timestamp` | Action 执行时的时间戳 |

## 使用示例

### 示例 1：单次执行

```yaml
- uses: 649956073/HLYAction-test1@v1
  with:
    message: 'Building project...'
```

### 示例 2：重复执行

```yaml
- uses: 649956073/HLYAction-test1@v1
  with:
    message: 'Processing files'
    count: '5'
```

### 示例 3：使用输出结果

```yaml
- name: Run Action
  id: run
  uses: 649956073/HLYAction-test1@v1
  with:
    message: 'Test message'

- name: Echo result
  run: echo "${{ steps.run.outputs.result }}"
```

## 许可证

本项目采用 MIT 许可证，详见 [LICENSE](LICENSE) 文件。

## 贡献

欢迎提交 Issue 和 Pull Request！

## 作者

**Huliangyi** - [GitHub 主页](https://github.com/649956073)

---

**注意**：这是一个测试 Action，用于学习和演示 GitHub Actions 的开发流程。
