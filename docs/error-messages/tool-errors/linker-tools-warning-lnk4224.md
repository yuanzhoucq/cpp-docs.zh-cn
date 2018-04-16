---
title: "链接器工具警告 LNK4224 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4224
dev_langs:
- C++
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96399e0c66eb3cb719073b2318513cd680723d97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4224"></a>链接器工具警告 LNK4224
不再支持选项;忽略  
  
 指定并忽略无效、 过时的链接器选项。  
  
 例如，如果 /comment 指令出现在出现 LNK4224 可以。 obj。/Comment 指令将通过添加[注释 （C/c + +）](../../preprocessor/comment-c-cpp.md)杂注时，使用不推荐使用的 exestr 选项。 使用 dumpbin [/所有](../../build/reference/all.md)若要查看的.obj 文件中的链接器指令。  
  
 如果可能，请修改.obj 的源和移除杂注。 如果不要忽略此警告，则可能使用编译.executable **/clr: pure**将未按预期运行。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK4224。  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```