---
title: '&lt;param&gt; (Visual C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- param
- <param>
dev_langs:
- C++
helpviewer_keywords:
- param C++ XML tag
- <param> C++ XML tag
ms.assetid: 66c1a1c3-4f98-4bcf-8c7d-9a40308982fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 94382cb1f2bab59fae6c397f8ad6dadee221c96b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434838"
---
# <a name="ltparamgt-visual-c"></a>&lt;param&gt; (Visual C++)

在方法声明的注释中，应使用 \<param> 标记来描述方法参数之一。

## <a name="syntax"></a>语法

```
<param name='name'>description</param>
```

#### <a name="parameters"></a>参数

*name*<br/>
方法参数的名称。  将名称括在单引号或双引号中。  如果编译器没有找到 `name`，它会发出警告。

description<br/>
参数的说明。

## <a name="remarks"></a>备注

\<param> 标记的文本将显示在 IntelliSense、[对象浏览器](/visualstudio/ide/viewing-the-structure-of-code)和代码注释 Web 报表中。

使用 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 进行编译可以将文档注释处理到文件中。

## <a name="example"></a>示例

```cpp
// xml_param_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_param_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <param name="Int1">Used to indicate status.</param>
   void MyMethod(int Int1) {
   }
};
```

## <a name="see-also"></a>请参阅

[XML 文档](../ide/xml-documentation-visual-cpp.md)