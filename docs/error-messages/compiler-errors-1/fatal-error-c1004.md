---
title: "错误 C1004 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1004
dev_langs:
- C++
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 528147eceadd35cc0d9fe656bdc7ce7965339a0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1004"></a>错误 C1004
中的意外的结束的文件  
  
 编译器未解析构造达到源文件的末尾。 该代码可能缺少以下元素之一：  
  
-   右大括号  
  
-   右括号  
  
-   结束注释标记 (* /)  
  
-   分号  
  
 若要解决此错误，请查看以下信息：  
  
-   默认磁盘驱动器没有足够的空间用于临时文件，需要大约两倍于源文件所在的空间。  
  
-   `#if`指令计算结果为 false 缺少右`#endif`指令。  
  
-   源文件不以回车符和换行符结尾。  
  
 下面的示例生成 C1004:  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 可能的解决方法：  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```