---
title: C++COM 和.NET 的属性
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: f9d339860e9d2bdb8d66f6b7f8f49d3993b2d5cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148314"
---
# <a name="c-attributes-for-com-and-net"></a>C++COM 和.NET 的属性

Microsoft 定义了一组C++属性，用于简化 COM 编程和.NET Framework 公共语言运行时开发。 当在源文件中包含的属性时，编译器可使用提供程序 Dll 可以插入代码或修改生成的对象文件中的代码。 这些属性可帮助创建.idl 文件、 接口、 类型库和其他 COM 元素。 在集成的开发环境 (IDE) 中，通过这些向导和属性窗口支持属性。

虽然属性消除一些详细编写 COM 对象所需的编码，您需要在后台[COM 基础知识](/windows/desktop/com/the-component-object-model)以最佳方式使用它们。

> [!NOTE]
> 如果您正在寻找C++标准属性，请参阅[特性](../../cpp/attributes.md)。

## <a name="purpose-of-attributes"></a>特性用途

属性扩展C++中而不会中断语言的经典结构目前不可能的方向。 属性允许提供程序 (单独的 Dll) 来动态扩展语言功能。 属性的主要目标是简化 COM 组件以及增加组件开发人员的工作效率级别的创作。 特性可以应用到几乎任意C++构造，如类、 数据成员或成员函数。 下面是提供这项新技术的优势的突出显示：

- 公开熟悉且简单的调用约定。

- 使用插入的代码，这不同于宏，调试器所识别。

- 允许简单而无需繁重的实现详细信息的基类派生。

- 取代了大量的 IDL 代码所需的少量简洁属性具有的 COM 组件。

例如，若要实现泛型 ATL 类的简单事件接收器，可以应用[event_receiver](event-receiver.md)特性为特定的类如`CMyReceiver`。 `event_receiver`属性然后编译该视觉对象的C++编译器，将适当的代码插入到对象文件。

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

然后可以设置`CMyReceiver`方法`handler1`并`handler2`来处理事件 (使用内部函数[__hook](../../cpp/hook.md)) 的事件源，可以创建使用[event_source](event-source.md).

## <a name="basic-mechanics-of-attributes"></a>特性的基本机制

有三种方法将属性插入你的项目。 首先，您可以将它们手动插入您的源代码。 第二，您可以将它们插入在项目中使用对象的属性网格。 最后，您可以插入它们使用不同的向导。 有关使用的详细信息**属性**窗口和各种向导，请参阅[创建和管理 VisualC++项目](../../build/creating-and-managing-visual-cpp-projects.md)。

如前面一样，生成项目时，编译器会分析每个C++源文件，生成的对象文件。 但是，当编译器遇到属性，它分析并语法验证。 然后编译器将动态调用要插入代码或在编译时进行其他修改的属性提供程序。 具体取决于属性的类型不同的提供程序实现。 例如，由 Atlprov.dll 实现与 ATL 相关的属性。

下图演示了编译器和特性提供程序之间的关系。

![组件特性通信](../media/vccompattrcomm.gif "组件特性通信")

> [!NOTE]
> 特性用法不会更改源文件的内容。 在调试会话过程中是唯一一次生成的属性代码均可见。 此外，对于每个源项目文件中，可以生成显示属性替换结果的文本文件。 此过程的详细信息，请参阅[/Fx （合并插入的代码）](../../build/reference/fx-merge-injected-code.md)并[调试插入代码](/visualstudio/debugger/how-to-debug-injected-code)。

如同大多C++构造，属性具有一组特征定义其适当的使用情况。 这被称为属性的上下文并在每个属性参考主题的属性上下文表中解决。 例如，[组件类](coclass.md)属性仅对现有的类或结构，而不是应用[cpp_quote](cpp-quote.md)属性，可以在任意位置插入C++源文件。

## <a name="building-an-attributed-program"></a>生成特性化程序

使视觉对象后C++属性插入源代码中，你可能想视觉对象C++编译器可为你生成类型库和.idl 文件。 以下链接器选项可帮助您生成.tlb 和.idl 文件：

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

某些项目包含多个独立的.idl 文件。 这些用于生成两个或多个.tlb 文件并根据需要将其绑定到的资源块。 在 Visual 中当前不支持这种情况下C++。

此外，视觉对象C++链接器将输出到单个 MIDL 文件的所有与 IDL 相关的属性信息。 将没有办法从单个项目生成两个类型库。

## <a name="contexts"></a> 特性上下文

C++可以使用四个基本字段描述属性： 它们可以应用到的目标 (**适用于**)，如果它们是可重复的还是不 (**Repeatable**)，则所需的其他属性存在 (**所需属性**)，并与其他属性的不兼容性 (**无效属性**)。 在每个属性的参考主题中的相关表中列出这些字段。 下面描述了每个字段。

### <a name="applies-to"></a>适用于

此字段描述了不同C++是指定的属性的合法目标的语言元素。 例如，如果属性中指定"的类"**适用于**字段中，这表示该属性只能为合法应用C++类。 如果该特性应用于类的成员函数，会产生语法错误。

有关详细信息，请参阅[按使用情况的特性](attributes-by-usage.md)。

### <a name="repeatable"></a>可重复

此字段规定是否该属性可以重复应用于同一个目标。 属性的大多数都不是可重复。

### <a name="required-attributes"></a>必需的特性

此字段中列出了需要其他属性指定的属性才能正常运行 （即，应用到同一目标） 存在。 它是常见的一个属性以包含此字段的任何条目。

### <a name="invalid-attributes"></a>无效的属性

此字段中列出了与指定的特性不兼容的其他属性。 它是常见的一个属性以包含此字段的任何条目。

## <a name="in-this-section"></a>本节内容

[特性编程常见问题解答](attribute-programming-faq.md)<br/>
[按组分的特性](attributes-by-group.md)<br/>
[按用法分的特性](attributes-by-usage.md)<br/>
[按字母顺序的特性参考](attributes-alphabetical-reference.md)