---
title: '&lt;seealso > (C++文档注释)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: ea399e98723a265ef3c17f2282b7c81299b4abc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318831"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

使用 \<seealso> 标记，可以指定想要在“另请参阅”部分中显示的文本。 使用 [\<see>](see-visual-cpp.md) 从文本内指定链接。

## <a name="syntax"></a>语法

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>参数

*member*<br/>
对可从当前编译环境调用的成员或字段的引用。  将名称括在单引号或双引号中。

编译器检查是否存在给定的码位元素，并将 `member` 解析为输出 XML 中的元素名称。  如果编译器没有找到 `member`，它会发出警告。

有关如何创建对泛型类型的 cref 引用的信息，请参阅 [\<see>](see-visual-cpp.md)。

## <a name="remarks"></a>备注

使用 [/doc](doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

有关使用 \<seealso> 的示例，请参阅 [\<summary>](summary-visual-cpp.md)。

MSVC 编译器将尝试解析在一次传递通过文档注释的 cref 引用。  因此，如果使用 C++ 查找规则，编译器找不到符号，引用将被标记为未解析。

## <a name="example"></a>示例

在以下示例中，cref 中引用了未解析的符号。 针对 B::Test 的 cref 的 XML 注释将为 `<seealso cref="!:B::Test" />`，而对 A::Test 的引用则为格式标准的 `<seealso cref="M:A.Test" />`。

```
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>请参阅

[XML 文档](xml-documentation-visual-cpp.md)
