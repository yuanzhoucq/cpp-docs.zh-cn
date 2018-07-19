---
title: 编译器警告 （等级 3） C4635 |Microsoft 文档
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
ms.openlocfilehash: 2dcc4b7466ed53a187b7f34ec45084a94adb59b4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291767"
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
  
 此示例的问题是结束标记\<摘要 > 格式不正确，并且编译器不识别其作为\<摘要 > 结束标记。  \<成员 > 标记嵌入到.xdc 文件中每个 /doc 编译中的编译器。  因此，此处问题是结束标记\</member >，不匹配编译器处理的前一个开始标记 (\<摘要 >。