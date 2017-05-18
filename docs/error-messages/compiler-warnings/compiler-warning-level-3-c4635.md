---
title: "编译器警告 （等级 3） C4635 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4635
dev_langs:
- C++
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: d4c85ca32903e20ea18a731872c25ee999b67f89
ms.contentlocale: zh-cn
ms.lasthandoff: 04/12/2017

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
  
 此示例的问题是结束标记\<摘要 1> 格式不正确，并且编译器不识别其作为\<摘要 1> 结束标记。  \<成员 1> 标记每个 /doc 编译中的编译器嵌入到.xdc 文件中。  因此，此处问题是结束标记\</member 1>，不匹配编译器处理的前一个开始标记 (\<摘要 1>。
