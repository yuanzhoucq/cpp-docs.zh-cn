---
title: 链接器工具错误 LNK1301 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b4e298ad3815c741ff6c901ac39bf7838ed135d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1301"></a>链接器工具错误 LNK1301
找到，与 /LTCG:parameter 不兼容的 LTCG clr 模块  
  
 /GL 与 /clr 编译的模块传递到链接器一起按配置优化 (PGO) 参数的 /LTCG。  
  
 /Clr 模块不支持按配置优化。  
  
 有关详细信息，请参见:  
  
-   [/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/LTCG（链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [按配置文件优化](../../build/reference/profile-guided-optimizations.md)  
  
### <a name="to-correct-this-error"></a>更正此错误  
  
1.  不使用 /clr 进行编译，或使用 /LTCG 的 PGO 参数之一不链接。  
  
## <a name="example"></a>示例  
 下面的示例生成 LNK1301:  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```