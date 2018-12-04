# <a name="metadata-and-markdown-template"></a>元数据和 Markdown 模板

此核心文档模板包含 Markdown 语法的示例以及有关设置元数据的指南。 若要充分利用此模板，必须同时查看[原始 Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)和[呈现的视图](https://github.com/dotnet/docs/blob/master/styleguide/template.md)（例如，原始 Markdown 显示元数据块，而呈现的视图不显示）。

创建 Markdown 文件时，应将此模板复制到新文件中，按下面的指定填写元数据，将上面的 H1 标题设置为本文的标题，并删除内容。

## <a name="metadata"></a>元数据

完整的元数据块如上所示（在[原始 Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) 文件中），分为必填字段和可选字段。 一些重要说明：

- 元数据元素的冒号 (:) 和值之间**必须**有空格。
- 如果某个可选的元数据元素没有值，则使用 # 号注释掉或删除它（请勿将其保留为空或使用“na”）；如果向注释掉的元素添加值，请务必删除 # 号。
- 值（例如标题）中的冒号会中断元数据解析器。 在此情况下，使用双引号将标题括起来（例如， `title: "Writing .NET Core console apps: An advanced step-by-step guide"`）。
- **title**：此标题将显示在搜索引擎结果中。 你还可以添加竖杠 (|) 后跟产品名称（例如，`title: Developing Libraries with Cross Platform Tools | .NET Core`）。 此标题不需要与 H1 标题相同，并且包含的字符数不超过 65 个（包括 | 产品名）。
- **author**、**manager**、**ms.reviewer**：作者字段应包含作者的 **GitHub 用户名**，而不是其别名。  另一方面，“manager”和“ms.reviewer”字段应包含 Microsoft 别名。 ms.reviewer 指定与文章或功能相关联的 PM/开发人员的姓名。
- **ms.devlang** 定义技术。 部分支持值为：`dotnet`、`cpp`、`csharp`、`fsharp`、`vb` 和 `xml`。
- **ms.assetid**：文章的 GUID，用于内部跟踪，例如商业智能 (BI)。 新建 Markdown 文件后，可以通过[联机 GUID 生成器](https://www.guidgenerator.com/)获取 GUID。

## <a name="basic-markdown-gfm-and-special-characters"></a>基本 Markdown、 GFM 和特殊字符

支持所有基本 Markdown 和 GitHub Flavored Markdown (GFM)。 有关这些主题的更多信息，请参阅：

- [Markdown 基本语法](https://daringfireball.net/projects/markdown/syntax)
- [GFM 文档](https://guides.github.com/features/mastering-markdown)

Markdown 使用特殊字符如 \*、\` 和 \# 进行格式化。 如果要在内容中包括一个特殊字符，必须执行以下两个操作之一：

- 在特殊字符前面放置一个反斜杠来“转义”它（例如，将 \* 写为 `\*`）
- 对字符使用 [HTML 实体代码](https://www.ascii.cl/htmlcodes.htm)（例如，将 &#42; 写为 `&#42;`）。

## <a name="markdown-editing-tools"></a>Markdown 编辑工具

可使用 [Visual Studio Code](https://code.visualstudio.com/) 编辑 Markdown 文档。 VS Code 提供许多实用的 Markdown 扩展，如：

- Microsoft 提供的 [docs-markdown](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-markdown)
- [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint)

## <a name="file-name"></a>文件名

文件名使用以下规则：

- 只包含小写字母、数字和连字符。
- 不包括空格或标点字符。 在文件名中使用连字符分隔单词和数字。
- 使用具体的动作动词，例如 develop、buy、build、troubleshoot。 不使用带 -ing 的单词。
- 不使用小单词 - 不包含 a、and、the、in、or 等。
- 必须为 Markdown 格式，使用 .md 文件扩展名。
- 保持文件名简短。 它们是文章 URL 的一部分。  

## <a name="headings"></a>标题

使用句式单词首字母大写。 以下单词的第一个字母始终为大写：

- 标题的首个单词。
- 标题中冒号后面的首个单词（例如，“How to: Sort an array”）。

标题使用 atx 样式，即在行的开头使用 1-6 个哈希字符 (#) 来表示标题，对应于 HTML 标题级别 H1 到 H6。 上面使用的是第一和第二级别标题示例。

主题中**必须**只有一个第一级别标题 (H1)，此标题显示为页面上的标题。

如果标题以 `#` 字符结束，则需要在末尾额外添加一个 `#` 字符，以便正确呈现此标题。 例如 `# Async Programming in F# #`。

标题（一级标题除外）前后应始终有一个空行。

第二级标题生成页面 TOC，显示在“In this article”部分的页面标题下方。

```markdown
### Third-level heading

#### Fourth-level heading

##### Fifth level heading

###### Sixth-level heading
```

## <a name="text-styling"></a>文本样式

*斜体*  
用于用户生成的文件名、文件夹和路径（对于长项，单独一行显示）；新术语；参数名称；用户输入的值；以及 URL（除非呈现为链接，此为默认值）。

**加粗**  
用于 UI 元素和语言关键字。

## <a name="links"></a>链接

### <a name="internal-links"></a>内部链接

若要链接到同一 Markdown 文件中的标题（也称为定位链接），需要找出想要链接到的标题的 ID。 若要确认 ID，请查看呈现的文章的源，以查找 ID（例如， `id="blockquote"`），并使用 # + ID 进行链接（例如， `#blockquote`）。
ID 是基于标头文本自动生成的。 因此，例如，如果某个唯一部分名称为 `## Step 2`，则 ID 应类似于 `id="step-2"`。

- 示例：[第 1 章](#chapter-1)

若要链接到同一个存储库中的 Markdown 文件，请使用[相对链接](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)，文件名末尾包含“.md”。

- 示例：[自述文件](../readme.md)
- 示例：[欢迎使用 .NET](../docs/welcome.md)

若要链接到同一个存储库中的 Markdown 文件中的标头，请使用相对链接 + 哈希标记进行链接。

- 示例：[.NET 社区](../docs/welcome.md#community)

### <a name="docs-links"></a>Docs 链接

若要链接到其他 Docs 存储库中的文件，请使用 docs.microsoft.com 相对 URL 作为链接。 请勿添加 .md 后缀。

- 示例：[通用 Windows 平台文档](/windows/uwp)

### <a name="external-links"></a>外部链接

若要链接到外部文件，请使用完整的 URL 作为链接。 使用 HTTPS URL（若有）。

- 示例：[GitHub](https://www.github.com)

如果在 Markdown 文件中显示一个 URL，此 URL 将转换为可单击的链接。

- 示例： https://www.github.com

### <a name="links-to-apis"></a>链接到 API

生成系统具有一些扩展功能，使我们能够链接到 .NET 核心 API，而无需使用外部链接。  
链接到 API 时，可以使用从源代码自动生成的 API 的唯一标识符 (UID)。

可以使用以下任一种语法：

1. Markdown 链接：`[link_text](xref:UID)`
2. 自动链接：`<xref:UID>`
3. 简写形式： `@UID`

- 示例：`@System.String`
- 示例：`[String class](xref:System.String)`

有关使用这一表示法的详细信息，请参阅 [Using cross reference](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference)（使用交叉引用）。

> 目前，没有查找 UID 的便捷方法。 查找 API UID 的最佳方法是，在以下存储库中搜索它：[docascode/coreapi](https://github.com/docascode/coreapi)。 我们正努力实现将来拥有更好的系统。

当 UID 包含特殊字符 \` 或 \# 时，UID 值需要分别使用 HTML 编码为 60% 和 %23，如下面的示例所示：
- 示例：@System.Threading.Tasks.Task\`1 变为 `@System.Threading.Tasks.Task%601`
- 示例：@System.Exception \#ctor 变为 `@System.Exception.%23ctor`

## <a name="lists"></a>列表

列表的前后都应有空行。

### <a name="ordered-lists"></a>有序列表

1. 这
1. 是
1. 一个
1. Ordered
1. 列表

#### <a name="ordered-list-with-an-embedded-list"></a>包含嵌套列表的有序列表

1. Here
1. comes
1. 一个
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. list

### <a name="unordered-lists"></a>无序列表

- 这
- is
- a
- 无序
- list

#### <a name="unordered-list-with-an-embedded-list"></a>包含嵌套列表的无序列表

- 这
- 无序
- list
    - Mrs. Peacock
    - Mr. Green
- 包含  
- 其他
    1. Colonel Mustard
    1. Mrs. White
- 列表

## <a name="horizontal-rule"></a>水平标尺

___

## <a name="tables"></a>表

| 表        | 很           | 酷  |
| ------------- |:-------------:| -----:|
| 第 3 列是      | 右对齐 | $1600 |
| 第 2 列是      | 居中对齐      |   $12 |
| 第 1 列为默认对齐方式 | 左对齐     |    $1 |

可以使用 [Markdown 表生成器工具](https://www.tablesgenerator.com/markdown_tables)来更轻松地创建它们。 另请参阅 [Markdown 编辑工具](#markdown-editing-tools)。

## <a name="code"></a>代码

包含代码的最好方法是包含工作示例中的代码片段。 按照[参与指南](../CONTRIBUTING.md#contributing-to-samples)中的说明创建示例。

可以使用包括语法来包含代码：

```markdown
[!code-csharp[<title>](<pathToFile>#<RegionName)]
```

上面的示例显示的是 C# 语法，但也支持其他语言。
将 `code-fsharp` 用于 F# 示例；将 `code-vbnet` 用于 Visual Basic 示例。
支持的其他语言包括：

- C++：`code-cpp`
- HTML：`code-html`
- JavaScript：`code-javascript`
- PowerShell：`code-ps`
- SQL：`code-sql`
- XML：`code-xml`

针对 `<title>` 放置的文本显示为滚动的文本。 `<pathToFile>` 为源文件的路径。 `<RegionName>` 为源代码中应包括的区域。 使用 `#region` 和 `#endregion` 预处理器语法来指定要包括的代码区域。

对于区域不起作用的情况，可以使用 XML 元素名称以单行注释的形式指定代码片段的开始和结束。 例如，可以使用 C# 编写以下代码：

```csharp
// <CodeToInclude>
int j = 5;
int i ; 10;
int sum = i + j;
// </CodeToInclude>
```

在其他语言中，请使用该语言的注释语法。

最后，可以使用行号：`#L1-L10` 包含第 1 到 10 行。 我们不鼓励使用行号，因为它们容易出错。

包括完整程序中的代码片段可以确保在整个持续集成 (CI) 系统中运行所有代码。 但是，如果需要显示导致编译时或运行时错误的一些内容，则可以使用内联代码块。

### <a name="inline-code-blocks-with-language-identifier"></a>具有语言标识符的内联代码块

使用三个反撇号 (\`\`\`) + 语言 ID，将特定于语言的颜色编码应用到代码块。 此处是 [GFM 语言 ID](https://github.com/jmm/gfm-lang-ids/wiki/GitHub-Flavored-Markdown-(GFM)-language-IDs) 的完整列表。

#### <a name="c"></a>C\#

```csharp
using System;
namespace HelloWorld
{
    class Hello
    {
        static void Main() 
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>通用代码块

将三个反撇号 (&#96;&#96;&#96;) 用于通用代码块编码。

> 建议的方法是使用具有上一节中所述的语言标识符的代码块，以便确保在文档站点中突出显示正确的语法。 仅在需要时使用通用代码块。

```javascript
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

### <a name="inline-code"></a>内联代码

将反撇号 (&#96;) 用于 `inline code`。 将内联代码用于命令行命令、数据库表和列名称，以及语言表达式和函数名称。

## <a name="blockquotes"></a>块引用

> 干旱至今已持续了一千万年，可怕的蜥蜴的统治早已结束。 在位于赤道的这片陆地上（某天会把这里当成非洲），生存竞争已经达到新高潮，而胜利者尚未出现。 在这片贫瘠而干旱的土地上，只有那些渺小或者敏捷或者凶残的生物才能茁壮成长，亦或是有希望生存下去。

## <a name="images"></a>图像

### <a name="static-image-or-animated-gif"></a>静态图像或动态 gif

![这是替换文字](../images/Logo_DotNet.png)

### <a name="linked-image"></a>链接的图像

[![链接的图像的替换文字](../images/Logo_DotNet.png)](https://dot.net)

## <a name="videos"></a>视频

### <a name="channel-9"></a>第 9 频道

[![Larry Osterman - 他与 Bill Gates 的一次交互（通过 DOS 网络堆栈）](https://sec.ch9.ms/ch9/caf5/f8657a22-5b83-47a3-9748-4c1be9fecaf5/Larry-Osterman-His-one-interaction-with-Bill-Gate_960.jpg)
](https://channel9.msdn.com/Blogs/TheChannel9Team/Larry-Osterman-His-one-interaction-with-Bill-Gates-over-DOS-networking-stack)

### <a name="youtube"></a>YouTube

[![On .NET（2016 年 2 月 4 日）- Scott Hunter](https://img.youtube.com/vi/g2a4W6Q7aRw/0.jpg)
](https://www.youtube.com/watch?v=g2a4W6Q7aRw)

## <a name="docsmicrosoft-extensions"></a>docs.microsoft 扩展

docs.microsoft 为 GitHub Flavored Markdown 提供了其他一些扩展。 

### <a name="alerts"></a>警报

请务必使用以下警报格式，以便在文档站点中以正确格式呈现警报。 但是，GitHub 上的呈现引擎无法区分它们。

#### <a name="note"></a>说明

> [!NOTE]
> This is a NOTE

#### <a name="warning"></a>警告

> [!WARNING]
> This is a WARNING

#### <a name="tip"></a>提示

> [!TIP]
> This is a TIP

#### <a name="important"></a>重要事项

> [!IMPORTANT]
> This is IMPORTANT

这些警报呈现如下：![警报样式](../images/alerts.png)

### <a name="buttons"></a>按钮

> [!div class="button"]
[按钮链接](../docs/core/index.md)

可在 [Intune 文档](https://docs.microsoft.com/intune/get-started/choose-how-to-enroll-devices)中查看按钮操作示例。 

### <a name="selectors"></a>选择器

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Windows](../docs/core/tutorials/using-on-windows.md)

可在 [Intune 文档](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune#how-your-end-users-get-their-apps)中查看选择器操作示例。

### <a name="step-by-steps"></a>按步执行

>[!div class="step-by-step"]
[上一步](../docs/csharp/expression-trees-interpreting.md)
[下一步](../docs/csharp/expression-trees-translating.md)

可在[高级威胁分析文档](https://docs.microsoft.com/advanced-threat-analytics/deploy-use/install-ata-step2)中查看按步执行示例。
