---
title: "safebuffers |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- safebuffers_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword (C++), safebuffers
- safebuffers __declspec keyword
ms.assetid: 0b0dce14-4523-44d2-8070-5dd0fdabc618
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eb9541bfc4a94253ac26e118e22c3abb2663a893
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="safebuffers"></a>safebuffers
**Microsoft 专用**  
  
 告知编译器不要插入针对函数的缓冲区溢出安全检查。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec( safebuffers )  
```  
  
## <a name="remarks"></a>备注  
 **/GS**编译器选项使编译器通过插入对堆栈中的安全检查来测试缓冲区溢出。 中介绍了符合安全检查的条件的数据结构的类型[/GS （缓冲区安全检查）](../build/reference/gs-buffer-security-check.md)。 缓冲区溢出检测的详细信息，请参阅[编译器安全检查在深度](http://go.microsoft.com/fwlink/p/?linkid=7260)MSDN 网站上。  
  
 专家手动代码评审或外部分析可能确定函数不会出现缓冲区溢出。 在这种情况下，你可以取消安全检查的函数显示通过应用`__declspec(safebuffers)`函数声明的关键字。  
  
> [!CAUTION]
>  缓冲区安全检查提供了重要的安全保护，并且对性能的影响微不足道。 因此，我们建议您不要取消它们，但在以下罕见的情况下除外：函数的性能至关重要，并且已经知道函数是安全的。  
  
## <a name="inline-functions"></a>内联函数  
 A*主函数*可以使用[内联](inline-functions-cpp.md)关键字插入一份*辅助函数*。 如果`__declspec(safebuffers)`关键字应用于函数，缓冲区溢出检测取消对该函数。 但是，内联，影响`__declspec(safebuffers)`通过以下方式的关键字。  
  
 假设**/GS**编译器选项指定为这两个函数，但主函数指定`__declspec(safebuffers)`关键字。 辅助函数中的数据结构将使它符合安全检查的条件，因此该函数不会取消这些检查。 这种情况下：  
  
-   指定[__forceinline](inline-functions-cpp.md)关键字以强制编译器内联到该函数无论编译器优化的辅助函数上。  
  
-   由于辅助函数符合安全检查的条件，安全检查也适用于的主要功能即使它指定`__declspec(safebuffers)`关键字。  
  
## <a name="example"></a>示例  
 下面的代码演示如何使用`__declspec(safebuffers)`关键字。  
  
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
  
## <a name="see-also"></a>请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [inline、 __inline、 \__forceinline](inline-functions-cpp.md)   
 [strict_gs_check](../preprocessor/strict-gs-check.md)