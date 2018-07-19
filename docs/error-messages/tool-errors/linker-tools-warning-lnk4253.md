---
title: 链接器工具警告 LNK4253 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4253
dev_langs:
- C++
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bae4e88e1fe1434cd638d5c31cc8fd4d5c02c4de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301276"
---
# <a name="linker-tools-warning-lnk4253"></a>链接器工具警告 LNK4253
部分"资料节 1"不合并到 section2';已合并到 section3  
  
 链接器检测到多个冲突的合并请求。 链接器将忽略其中一个请求。  
  
 A **/合并**遇到选项或指令和`from`节已合并到由于先前的其他部分 **/合并**选项或指令 （或由于来自的隐式合并链接器）。  
  
 若要解决 LNK4253，删除其中一个的合并请求。  
  
 在面向 x86 时机和 Visual c + +，Windows CE 目标 （ARM、 MIPS、 SH4，和 Thumb）。CRT 部分现在为只读。 如果你的代码依赖于以前的行为 (。CRT 部分是读/写），你可能会看到意外的行为。  
  
 有关详细信息，请参阅  
  
-   [/MERGE（合并节）](../../build/reference/merge-combine-sections.md)  
  
-   [注释 (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>示例  
 在下面的示例中，链接器将指示合并`.rdata`部分两次，但到不同的节。 下面的示例生成 LNK4253。  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```