---
title: 使用 MFC 源文件
ms.date: 08/19/2019
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
ms.openlocfilehash: ca5799da7a6ada42db20e3551b3fb7262e8990a0
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631668"
---
# <a name="using-the-mfc-source-files"></a>使用 MFC 源文件

Microsoft 基础类 (MFC) 库提供完整源代码。 头文件 (.h) 位于 *\atlmfc\include*目录中。 实现文件 (.cpp) 位于 *\atlmfc\src\mfc*目录中。

本文介绍 MFC 用于注释每个类的各个部分的约定、这些注释的含义, 以及在每个部分应该会发现的内容。 Visual Studio 向导对为您创建的类使用类似的约定, 您可能会发现这些约定对您自己的代码很有用。

你可能熟悉**公共**、**受保护**和**私有** C++关键字。 在 MFC 头文件中, 可以找到每个类, 每个类都有多个。 例如, 公共成员变量和函数可能位于多个**public**关键字下。 这是因为 MFC 根据成员变量和函数的使用来分隔它们, 而不是允许的访问类型。 MFC 使用的是**专用**的。 即使是视为实现的详细信息的项目经常**受到保护**, 而且很多时候都是**公开**的。 虽然不建议访问实现的详细信息，但 MFC 会将决定权留给您。

在 mfc 应用程序向导创建的 MFC 源文件和标头文件中, 您将在类声明 (通常按此顺序) 中找到类似于下面的注释:

`// Constructors`

`// Attributes`

`// Operations`

`// Overridables`

`// Implementation`

## <a name="an-example-of-the-comments"></a>注释示例

下面的类`CStdioFile`分部列表使用 MFC 在其类中使用的大多数标准注释, 以将类成员分为其使用方式:

```cpp
/*============================================================================*/
// STDIO file implementation

class CStdioFile : public CFile
{
    DECLARE_DYNAMIC(CStdioFile)

public:
// Constructors
    CStdioFile();

    // . . .

// Attributes
    FILE* m_pStream;    // stdio FILE
                        // m_hFile from base class is _fileno(m_pStream)

// Operations
    // reading and writing strings
    virtual void WriteString(LPCTSTR lpsz);
    virtual LPTSTR ReadString(_Out_writes_z_(nMax) LPTSTR lpsz, _In_ UINT nMax);
    virtual BOOL ReadString(CString& rString);

// Implementation
public:
    virtual ~CStdioFile();
#ifdef _DEBUG
    void Dump(CDumpContext& dc) const;
#endif
    virtual ULONGLONG GetPosition() const;
    virtual ULONGLONG GetLength() const;
    virtual BOOL Open(LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL);

    // . . .

protected:
    void CommonBaseInit(FILE* pOpenStream, CAtlTransactionManager* pTM);
    void CommonInit(LPCTSTR lpszFileName, UINT nOpenFlags, CAtlTransactionManager* pTM);
};
```

这些注释将一致地标记包含类似种类成员的类声明的各个部分。 请记住, 它们是 MFC 约定, 而不是设置规则。

## <a name="-constructors-comment"></a>构造函数注释

MFC `// Constructors`类声明的部分声明构造函数 (在C++意义上), 以及实际使用对象所需的任何初始化函数。 例如, `CWnd::Create`在构造函数部分, 因为在`CWnd`使用对象之前, 必须先调用C++构造函数, 然后调用`Create`函数, 才能 "完全构造"。 通常, 这些成员是公共的。

例如, 类`CStdioFile`具有五个构造函数, 其中一个构造函数在[注释示例](#an-example-of-the-comments)中显示。

## <a name="-attributes-comment"></a>特性注释

MFC 类声明的 `// Attributes` 部分包含对象的公共特性（或属性）。 通常, 特性是成员变量或获取/设置函数。 “Get”和“Set”函数可能是或可能不是虚拟的。 "Get" 函数通常是**常量**, 因为在大多数情况下它们不会有副作用。 这些成员通常是公共的。 受保护的特性和私有特性通常在实现部分中找到。

在来自类`CStdioFile`的示例列表中, 在[注释的示例](#an-example-of-the-comments)下, 列表包含一个成员变量*m_pStream*。 类 `CDC` 在此注释下列出了近 20 个成员。

> [!NOTE]
> 大型类（如 `CDC` 和 `CWnd`）可能具有非常多的成员，因此只是在一个组中列出所有特性并不会大幅提高清晰性。 在这种情况下，类库使用其他注释作为标题来进一步描述这些成员。 例如，`CDC` 使用 `// Device-Context Functions`、`// Drawing Tool Functions`、`// Drawing Attribute Functions` 等。 表示特性的组将采用上述常用语法。 许多 OLE 类都具有一个称为 `// Interface Maps` 的实现部分。

## <a name="-operations-comment"></a>操作注释

MFC `// Operations`类声明的部分包含成员函数, 你可以在对象上调用这些成员函数来执行操作或采取操作 (执行操作)。 这些函数通常是非常**量**的, 因为它们通常有副作用。 它们可能是虚拟的, 也可能是非虚拟的, 具体取决于类的需求。 通常, 这些成员是公共的。

在类`CStdioFile`的示例列表中, 在[注释示例](#an-example-of-the-comments)中, 此列表包含以下注释中的三个成员函数: `WriteString`和的`ReadString`两个重载。

与属性一样, 可以进一步细分操作。

## <a name="-overridables-comment"></a>可重写注释

MFC 类声明的 `// Overridables` 部分包含您在需要修改基类行为时可在派生类中重写的虚拟函数。 它们的名称通常以 "On" 开头, 但并不是绝对必要的。 此处的函数设计为进行重写，并且一般实现或提供某种“回调”或“挂钩”。 通常，这些成员是受保护的。

在 MFC 本身中，纯虚拟函数始终放置在此节中。 中C++的纯虚函数采用以下格式:

`virtual void OnDraw( ) = 0;`

在类`CStdioFile`的示例列表中, 在[注释示例](#an-example-of-the-comments)中, 列表不包含可重写部分。 另一方面`CDocument`, 类会列出大约10个可重写的成员函数。

在部分类中，您还可以查看注释 `// Advanced Overridables`。 这些函数是只有高级程序员应尝试重写的函数。 您可能永远不需要重写它们。

> [!NOTE]
> 一般而言，本文中描述的约定也适用于自动化（之前称为“OLE 自动化”）方法和属性。 自动化方法类似于 MFC 操作。 自动化属性类似于 MFC 特性。 自动化事件（受 ActiveX 控件（之前称为“OLE 控件”）支持）类似于 MFC 可重写成员函数。

## <a name="-implementation-comment"></a>实现注释

`// Implementation` 节是任何 MFC 类声明的最重要的部分。

此节存储所有实现详细信息。 成员变量和成员函数都可在此节中出现。 此行下的所有内容在未来版本的 MFC 中都可能会更改。 除非您无法避免这种情况, 否则不应依赖于`// Implementation`行下面的详细信息。 此外, 虽然技术说明中讨论了某些实现, 但在实现行下面声明的成员并未记录。 基类中的虚函数的重写驻留在此节中, 无论在哪个节中定义了基类函数。 当函数重写基类实现时, 它被视为实现细节。 通常，这些成员是受保护的，但并不总是这样。

`// Implementation`[在注释示例](#an-example-of-the-comments)下的列表中, 注释下面声明的成员可以声明为公共、受保护或私有`CStdioFile` 。 请谨慎使用这些成员, 因为这些成员将来可能会更改。 若要使类库实现正常工作, 可能需要将一组成员声明为**公共**成员。 但是, 这并不意味着您可以安全地使用成员进行声明。

> [!NOTE]
> 您可以在 `// Implementation` 注释的上面或下面找到剩余类型的注释。 在任一情况下，这些注释都描述在其下面声明的类型的成员。 如果这些注释出现在 `// Implementation` 注释下面，则应假设成员在将来版本的 MFC 中可能会更改。

## <a name="see-also"></a>请参阅

[常规 MFC 主题](../mfc/general-mfc-topics.md)
