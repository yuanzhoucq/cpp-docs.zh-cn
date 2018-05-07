---
title: 编译器错误 C2441 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6557e913f2bd34fda9d435d44020697a925af4e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2441"></a>编译器错误 C2441
variable: __declspec 使用声明的符号必须是常量在 /clr: pure 模式  
  
 **/clr:pure** 和 **/clr:safe** 编译器选项在 Visual Studio 2015 中已弃用。  
  
 默认情况下，变量是每个应用程序域下 **/clr: pure**。 变量标记`__declspec(process)`下 **/clr: pure**很容易导致错误，如果在一个应用程序域中修改并在另一个中读取。  
  
 因此，编译器会强制执行每个进程变量为`const`下 **/clr： 纯**，仅在所有应用程序域中的进行读取它们。  
  
 有关详细信息，请参阅[过程](../../cpp/process.md)和[/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2441。  
  
```  
// C2441.cpp  
// compile with: /clr:pure /c  
__declspec(process) int i;   // C2441  
__declspec(process) const int j = 0;   // OK  
```