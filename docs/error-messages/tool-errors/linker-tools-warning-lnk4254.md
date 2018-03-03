---
title: "链接器工具警告 LNK4254 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e17bcd03f92114c1b7cd21e63220cf6372c17bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4254"></a>链接器工具警告 LNK4254
部分"资料节 1"（偏移量） 合并到 section2 （偏移量） 具有不同的属性  
  
 一个节的内容合并到另一个字符串，但特性的两个部分都相同。 你的程序可能产生意外的结果。 例如，你想要读取的数据仅可能现在处于可写部分。  
  
 若要解决 LNK4254，修改或删除合并请求。  
  
 在面向 x86 时机和 Visual c + +，Windows CE 目标 （ARM、 MIPS、 SH4，和 Thumb）。CRT 部分是只读的。 如果你的代码依赖于以前的行为 (。CRT 部分是读/写），你可能会看到意外的行为。  
  
 有关详细信息，请参阅  
  
-   [/MERGE （合并节）](../../build/reference/merge-combine-sections.md)  
  
-   [注释 (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK4254。  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```