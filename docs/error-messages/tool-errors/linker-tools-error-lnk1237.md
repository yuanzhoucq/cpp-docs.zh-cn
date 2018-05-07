---
title: 链接器工具错误 LNK1237 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1237
dev_langs:
- C++
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ffc337d6b1548db4717dc4b87ff8aa25ef92e93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1237"></a>链接器工具错误 LNK1237
在代码生成期间编译器引入到符号 symbol 模块 module 使用 /GL 进行编译中定义的引用  
  
 在代码生成期间编译器应不引入稍后会将其解析为定义编译的符号 **/GL**。 `symbol` 是一个符号，已引入和更高版本被解析为与编译定义 **/GL**。  
  
 有关详细信息，请参阅 [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)。  
  
 若要解决 LNK1237，不编译具有符号 **/GL**或使用[/INCLUDE （强制符号引用）](../../build/reference/include-force-symbol-references.md)以强制对符号的引用。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK1237。 若要解决此错误，请不要未初始化的数组中 LNK1237_a.cpp 并添加 **/ 包括： __chkstk**到链接命令。  
  
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