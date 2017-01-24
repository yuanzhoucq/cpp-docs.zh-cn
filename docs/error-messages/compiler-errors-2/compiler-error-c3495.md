---
title: "编译器错误 C3495 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3495"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3495"
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3495
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：lambda 捕获必须有自动存储持续时间  
  
 不能捕获没有自动存储持续时间的变量，如标记为 `static` 或 `extern` 的变量。  
  
### 更正此错误  
  
-   不要将 `static` 或 `extern` 变量传递到 lambda 表达式的捕获列表。  
  
## 示例  
 下面的示例将生成 C3495，因为 lambda 表达式的捕获列表中出现了 `static` 变量 `n`：  
  
```  
// C3495.cpp int main() { static int n = 66; [&n]() { return n; }(); // C3495 }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)   
 [\(NOTINBUILD\) 存储类说明符](http://msdn.microsoft.com/zh-cn/10b3d22d-cb40-450b-994b-08cf9a211b6c)