---
title: "safebuffers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "safebuffers"
  - "safebuffers_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 (C++), safebuffers"
  - "safebuffers __declspec 关键字"
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# safebuffers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 告知编译器不要插入针对函数的缓冲区溢出安全检查。  
  
## 语法  
  
```  
__declspec( safebuffers )  
```  
  
## 备注  
 **\/GS** 编译器选项将使编译器通过插入对堆栈的安全检查来测试缓冲区溢出。  符合安全检查条件的数据结构的类型在 [\/GS（缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)中介绍。  有关缓冲区溢出检测的详细信息，请参阅 MSDN 网站上的[编译器深度安全检查](http://go.microsoft.com/fwlink/?linkid=7260)。  
  
 专家手动代码评审或外部分析可能确定函数不会出现缓冲区溢出。  在这种情况下，可以通过对声明函数应用 `declspec(safebuffers)` 关键字来取消对函数的安全检查。  
  
> [!CAUTION]
>  缓冲区安全检查提供了重要的安全保护，并且对性能的影响微不足道。  因此，我们建议您不要取消它们，但在以下罕见的情况下除外：函数的性能至关重要，并且已经知道函数是安全的。  
  
## 内联函数  
 主函数可以使用 [inlining](../misc/inline-inline-forceinline.md) 关键字插入辅助函数的副本。  如果将 \_\_`declspec(safebuffers)` 关键字应用于函数，则会取消对该函数的缓冲区溢出检测。  但是，内联将通过以下几种方式影响 \_\_`declspec(safebuffers)` 关键字。  
  
 假设为这两种函数都指定了 **\/GS** 编译器选项，但主函数指定了 \_\_`declspec(safebuffers)` 关键字。  辅助函数中的数据结构将使它符合安全检查的条件，因此该函数不会取消这些检查。  在这种情况下：  
  
-   在辅助函数上指定 [\_\_forceinline](../misc/inline-inline-forceinline.md) 关键字以强制编译器内联到该函数（无论编译器优化情况如何）。  
  
-   由于辅助函数符合安全检查的条件，因此即使主函数指定了 `declspec(safebuffers)` 关键字，也会对主函数应用安全检查。  
  
## 示例  
 以下代码演示如何使用 `declspec(safebuffers)` 关键字。  
  
```  
// compile with: /c /GS  
typedef struct {  
    int x[20];  
} BUFFER;  
static int checkBuffers() {  
    BUFFER cb;  
    // Use the buffer...  
    return 0;  
};  
static __declspec(safebuffers)   
    int noCheckBuffers() {  
    BUFFER ncb;  
    // Use the buffer...  
    return 0;  
}  
int wmain() {  
    checkBuffers();  
    noCheckBuffers();  
    return 0;  
}  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [inline、\_\_inline、\_\_forceinline](../misc/inline-inline-forceinline.md)   
 [strict\_gs\_check](../preprocessor/strict-gs-check.md)