---
title: '&lt;example&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C++ XML tag
- example C++ XML tag
ms.assetid: c821aaa7-7ea7-4bee-9922-6705ad57f877
ms.openlocfilehash: 6fb6a83a170cfcf3e394ac8b0b15af869d6e59fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641631"
---
# <a name="ltexamplegt-visual-c"></a>&lt;example&gt; (Visual C++)

借助 \<example> 标记，可以指定如何使用方法或其他库成员的示例。 通常情况下，这将涉及使用 [\<code>](../ide/code-visual-cpp.md)标记。

## <a name="syntax"></a>语法

```
<example>description</example>
```

#### <a name="parameters"></a>参数

description<br/>
代码示例的说明。

## <a name="remarks"></a>备注

使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

## <a name="example"></a>示例

```
// xml_example_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_example_tag.dll

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary>
   /// GetZero method
   /// </summary>
   /// <example> This sample shows how to call the GetZero method.
   /// <code>
   /// int main()
   /// {
   ///    return GetZero();
   /// }
   /// </code>
   /// </example>
   static int GetZero() {
      return 0;
   }
};
```

## <a name="see-also"></a>请参阅

[XML 文档](../ide/xml-documentation-visual-cpp.md)