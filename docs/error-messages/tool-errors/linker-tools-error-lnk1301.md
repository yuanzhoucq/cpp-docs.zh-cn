---
title: "链接器工具错误 LNK1301 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1301
dev_langs:
- C++
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfcdb90b967ce5f0e9eda8dded9b93db5bdcc268
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1301"></a>链接器工具错误 LNK1301
找到，与 /LTCG:parameter 不兼容的 LTCG clr 模块  
  
 /GL 与 /clr 编译的模块传递到链接器一起按配置优化 (PGO) 参数的 /LTCG。  
  
 /Clr 模块不支持按配置优化。  
  
 有关详细信息，请参见:  
  
-   [/GL （全程序优化）](../../build/reference/gl-whole-program-optimization.md)  
  
-   [/LTCG （链接时间代码生成）](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [/clr （公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
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