# Markdown

Markdownis a lightweight markup language for creating formatted text using a plain-text editor.

Markdown 是一种轻量级标记语言，用于使用纯文本编辑器创建格式化文本。

## 推荐工具

* VS Code + 插件

    非常好用，超越目前我使用的其他所有工具。可以边写边预览，自动生成目录等，我就用它:smile:。

    推荐插件：

  * Markdown All in One
  * Markdown Preview Enhanced
  * Markdown PDF
    * 同时支持html，png，jpeg的格式导出。
  * Markdown Emoji
  * markdownlint
    * 是个帮助你写好markdown的工具
      * <https://github.com/DavidAnson/vscode-markdownlint>
      * <https://github.com/DavidAnson/markdownlint>
      * 我的.markdownlint.json（在根目录下）配置如下：

          ```json
          {
              "MD004": false,
              "MD013": {
                  "line_length": 1000
              },
              "MD025": false,
              "MD033": false,
              "MD052": false
          }
          ```

* MacDown

    [MacDown](https://macdown.uranusjr.com) is an open source Markdown editor for macOS, released under the MIT License.

    MacDown是开源 Markdown 编辑器，使用MIT许可证发布。

* Typora

    [Typora](https://typora.io) is a Markdown editor, markdown reader.

    Typora是个 Markdown 编辑器和阅读器。

## 参考文献

1. [https://www.markdownguide.org](https://www.markdownguide.org)
2. [Basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
