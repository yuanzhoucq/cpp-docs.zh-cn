---
title: 编译器警告 （等级 3） C4635 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7651012d4c48d420734a9c6ec2ff051718f82007
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038108"
---
# <a name="compiler-warning-level-3-c4635"></a>编译器警告（等级 3）C4635

XML 文档注释目标: XML 格式不正确: 原因

编译器发现此 XML 标记存在一些问题。  解决该问题并重新编译

下面的示例生成 C4635：

```
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

请注意，此示例的输出显示： **结束标记“member”与开始标记“summary”不匹配。**

此示例的问题是的结束标记\<摘要 > 格式不正确，且编译器无法识别其作为\<摘要 > 结束标记。  \<成员 > 标记中每个 /doc 编译的编译器嵌入到.xdc 文件中。  因此，此处的问题是，结束标记\</member >，与编译器处理前一个开始标记不匹配 (\<摘要 >。