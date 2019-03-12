---
title: '&lt;see&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <see>
- see
helpviewer_keywords:
- <see> C++ XML tag
- see C++ XML tag
ms.assetid: 20ef66f4-b278-45cf-8613-63919edf5720
ms.openlocfilehash: c8e797dff1495e9b4573ab4e0820d60b8027a293
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747587"
---
# <a name="ltseegt-visual-c"></a>&lt;see&gt; (Visual C++)

通过 \<see> 标记可以从文本内指定链接。 使用 [\<seealso>](../ide/seealso-visual-cpp.md) 指示想要在“另请参阅”部分中显示的文本。

## <a name="syntax"></a>语法

```
<see cref="member"/>
```

#### <a name="parameters"></a>参数

*member*<br/>
对可从当前编译环境调用的成员或字段的引用。  将名称括在单引号或双引号中。

编译器检查是否存在给定的码位元素，并将 `member` 解析为输出 XML 中的元素名称。  如果编译器没有找到 `member`，它会发出警告。

## <a name="remarks"></a>备注

使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

有关使用 \<see> 的示例，请参阅 [\<summary>](../ide/summary-visual-cpp.md)。

Visual C++ 编译器将尝试通过文档注释在一次处理中解决 cref 引用。  因此，如果使用 C++ 查找规则，编译器找不到符号，引用将被标记为未解析。 请参阅 [\<seealso>](../ide/seealso-visual-cpp.md)，获取详细信息。

## <a name="example"></a>示例

以下示例显示了如何对泛型类型进行 cref 引用，以便编译器解析该引用。

```
// xml_see_cref_example.cpp
// compile with: /LD /clr /doc
// the following cref shows how to specify the reference, such that,
// the compiler will resolve the reference
/// <see cref="C{T}">
/// </see>
ref class A {};

// the following cref shows another way to specify the reference,
// such that, the compiler will resolve the reference
/// <see cref="C < T >"/>

// the following cref shows how to hard-code the reference
/// <see cref="T:C`1">
/// </see>
ref class B {};

/// <see cref="A">
/// </see>
/// <typeparam name="T"></typeparam>
generic<class T>
ref class C {};
```

## <a name="see-also"></a>请参阅

[XML 文档](../ide/xml-documentation-visual-cpp.md)
