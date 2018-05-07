---
title: 链接器工具警告 LNK4254 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4254
dev_langs:
- C++
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb57882ab4269c06a53ed73fed2a9d6caf2f2c85
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4254"></a>链接器工具警告 LNK4254
部分"资料节 1"（偏移量） 合并到 section2 （偏移量） 具有不同的属性  
  
 一个节的内容合并到另一个字符串，但特性的两个部分都相同。 你的程序可能产生意外的结果。 例如，你想要读取的数据仅可能现在处于可写部分。  
  
 若要解决 LNK4254，修改或删除合并请求。  
  
 在面向 x86 时机和 Visual c + +，Windows CE 目标 （ARM、 MIPS、 SH4，和 Thumb）。CRT 部分是只读的。 如果你的代码依赖于以前的行为 (。CRT 部分是读/写），你可能会看到意外的行为。  
  
 有关详细信息，请参阅  
  
-   [/MERGE（合并节）](../../build/reference/merge-combine-sections.md)  
  
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