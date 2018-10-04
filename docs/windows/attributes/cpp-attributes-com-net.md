---
title: 对于 COM 和.NET 的 c + + 特性 |Microsoft Docs
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fe6941e8809c0d735013b56d340f27302890b149
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790360"
---
# <a name="c-attributes-for-com-and-net"></a>对于 COM 和.NET 的 c + + 特性

Microsoft 定义一的组简化 COM 编程和.NET Framework 公共语言运行时开发的 c + + 属性。 当在源文件中包含的属性时，编译器可使用提供程序 Dll 可以插入代码或修改生成的对象文件中的代码。 这些属性可帮助创建.idl 文件、 接口、 类型库和其他 COM 元素。 在集成的开发环境 (IDE) 中，通过这些向导和属性窗口支持属性。

虽然属性消除一些详细编写 COM 对象所需的编码，您需要在后台[COM 基础知识](/windows/desktop/com/the-component-object-model)以最佳方式使用它们。

> [!NOTE]
> 如果您要查找 c + + 标准属性，请参阅[属性](../../cpp/attributes.md)。

## <a name="purpose-of-attributes"></a>特性用途

属性扩展的 c + + 中当前不可能的方向而不会破坏经典的语言结构。 属性允许提供程序 (单独的 Dll) 来动态扩展语言功能。 属性的主要目标是简化 COM 组件以及增加组件开发人员的工作效率级别的创作。 属性可应用于几乎任何 c + + 构造，如类、 数据成员或成员函数。 下面是提供这项新技术的优势的突出显示：

- 公开熟悉且简单的调用约定。

- 使用插入的代码，这不同于宏，调试器所识别。

- 允许简单而无需繁重的实现详细信息的基类派生。

- 取代了大量的 IDL 代码所需的少量简洁属性具有的 COM 组件。

例如，若要实现泛型 ATL 类的简单事件接收器，可以应用[event_receiver](event-receiver.md)特性为特定的类如`CMyReceiver`。 `event_receiver`属性然后编译的 Visual c + + 编译器，它将正确的代码插入到对象文件。

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

有三种方法将属性插入你的项目。 首先，您可以将它们手动插入您的源代码。 第二，您可以将它们插入在项目中使用对象的属性网格。 最后，您可以插入它们使用不同的向导。 有关使用的详细信息**属性**窗口和各种向导，请参阅[创建和管理 Visual c + + 项目](../../ide/creating-and-managing-visual-cpp-projects.md)。

作为之前，当生成项目时，编译器将分析每个 c + + 源代码文件，生成的对象文件。 但是，当编译器遇到属性，它分析并语法验证。 然后编译器将动态调用要插入代码或在编译时进行其他修改的属性提供程序。 具体取决于属性的类型不同的提供程序实现。 例如，由 Atlprov.dll 实现与 ATL 相关的属性。

下图演示了编译器和特性提供程序之间的关系。

![组件特性通信](../media/vccompattrcomm.gif "vcCompAttrComm")

> [!NOTE]
> 特性用法不会更改源文件的内容。 在调试会话过程中是唯一一次生成的属性代码均可见。 此外，对于每个源项目文件中，可以生成显示属性替换结果的文本文件。 此过程的详细信息，请参阅[/Fx （合并插入的代码）](../../build/reference/fx-merge-injected-code.md)并[调试插入代码](/visualstudio/debugger/how-to-debug-injected-code)。

大多数 c + + 构造，如属性具有一组特征定义其适当的使用情况。 这被称为属性的上下文并在每个属性参考主题的属性上下文表中解决。 例如，[组件类](coclass.md)属性仅对现有的类或结构，而不是应用[cpp_quote](cpp-quote.md)属性，可以插入 c + + 源代码文件中的任意位置。

## <a name="building-an-attributed-program"></a>生成特性化程序

Visual c + + 特性置于源代码后，你可能想 Visual c + + 编译器为您生成类型库和.idl 文件。 以下链接器选项可帮助您生成.tlb 和.idl 文件：

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

某些项目包含多个独立的.idl 文件。 这些用于生成两个或多个.tlb 文件并根据需要将其绑定到的资源块。 在 Visual c + + 中，当前不支持此方案。

此外，Visual c + + 链接器将输出到单个 MIDL 文件的所有与 IDL 相关的属性信息。 将没有办法从单个项目生成两个类型库。

## <a name="contexts"></a> 特性上下文

可以使用四个基本字段描述 c + + 特性： 它们可以应用到的目标 (**适用于**)，如果它们是可重复的还是不 (**Repeatable**)，则所需的其他属性 (存在**所需属性**)，并与其他属性的不兼容性 (**无效属性**)。 在每个属性的参考主题中的相关表中列出这些字段。 下面描述了每个字段。
  
### <a name="applies-to"></a>适用于

此字段描述了不同的 c + + 语言元素的指定属性的合法目标。 例如，如果属性中指定"的类"**适用于**字段中，这表示该属性可以仅应用于合法的 c + + 类。 如果该特性应用于类的成员函数，会产生语法错误。
  
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