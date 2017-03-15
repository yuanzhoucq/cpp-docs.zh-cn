---
title: "链接器工具错误 LNK1301 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1301"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1301"
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 链接器工具错误 LNK1301
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找到 LTCG clr 模块，与 \/LTCG:parameter 不兼容  
  
 用 \/clr 和 \/GL 编译的模块传递给了链接器以及 \/LTCG 的按配置优化 \(PGO\) 参数之一。  
  
 \/clr 模块不支持按配置优化。  
  
 有关详细信息，请参阅：  
  
-   [\/GL（全程序优化）](../../build/reference/gl-whole-program-optimization.md)  
  
-   [\/LTCG（链接时代码生成）](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [按配置文件优化](../../build/reference/profile-guided-optimizations.md)  
  
### 更正此错误  
  
1.  请不要使用 \/clr 进行编译，也不要使用 PGO 参数之一链接到 \/LTCG。  
  
## 示例  
 下面的示例生成 LNK1301：  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```