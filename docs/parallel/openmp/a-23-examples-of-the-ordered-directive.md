---
title: "A.23   Examples of the ordered Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.23   Examples of the ordered Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以使多个与 `for` 的有序部分指定与 `ordered` 子句。  ，因为 API 指定以下内容，第一个示例是不符合:  
  
 “的循环的迭代与 `for` 结构化不可多次执行相同 `ordered` 指令，因此，它无法执行多个 `ordered` 指令”。\(请参见在第 22 页\) 的 [第2.6.6部分](../../parallel/openmp/2-6-6-ordered-construct.md)  
  
 不在此示例中，所有迭代执行 2 个有序的部分:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
}  
```  
  
 下面的示例演示带有多个有序的 `for` :  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    if (i <= 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
    (i > 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
}  
```