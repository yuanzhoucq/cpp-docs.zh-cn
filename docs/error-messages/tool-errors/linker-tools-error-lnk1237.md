---
title: "链接器工具错误 LNK1237 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee9ec0e197d51f76ff57ef06f5584c55df0a4746
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1237"></a>链接器工具错误 LNK1237
在代码生成期间编译器引入到符号 symbol 模块 module 使用 /GL 进行编译中定义的引用  
  
 在代码生成期间编译器应不引入稍后会将其解析为定义编译的符号**/GL**。 `symbol`是一个符号，已引入和更高版本被解析为与编译定义**/GL**。  
  
 有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。  
  
 若要解决 LNK1237，不编译具有符号**/GL**或使用[/INCLUDE （强制符号引用）](../../build/reference/include-force-symbol-references.md)以强制对符号的引用。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK1237。 若要解决此错误，请不要未初始化的数组中 LNK1237_a.cpp 并添加**/ 包括： __chkstk**到链接命令。  
  
```  
// LNK1237_a.cpp  
int main() {  
   char c[5000] = {0};  
}  
```  
  
```  
// LNK1237_b.cpp  
// compile with: /GS- /GL /c LNK1237_a.cpp  
// processor: x86  
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)  
extern "C" void _chkstk(size_t s) {}  
```