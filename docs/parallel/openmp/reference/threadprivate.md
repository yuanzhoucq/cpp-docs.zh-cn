---
title: "threadprivate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "threadprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "threadprivate OpenMP directive"
ms.assetid: 3515aaed-6f9d-4d59-85eb-342378bea2d3
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# threadprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

指定变量是私有的。线程。  
  
## 语法  
  
```  
#pragma omp threadprivate(var)  
```  
  
## 备注  
 其中，  
  
 `var`  
 逗号分隔的列表变量要使私有到线程的数据。  `var` 必须是全局变量或的 namespacescoped 或本地静态变量。  
  
## 备注  
 `threadprivate` 指令不支持 OpenMP 子句。  
  
 有关更多信息，请参见 [2.7.1 threadprivate 指令](../../../parallel/openmp/2-7-1-threadprivate-directive.md)。  
  
 `threadprivate` 指令根据 [线程](../../../cpp/thread.md)`__declspec` 属性;在 **\_\_declspec \(线程\)** 的限制适用于 `threadprivate`。  
  
 在通过 [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175)要加载的任何 DLL 无法使用 `threadprivate` 。  这包括用 [\/DELAYLOAD（延迟加载导入）](../../../build/reference/delayload-delay-load-import.md)加载，还使用 **LoadLibrary**的 DLL。  
  
 在静态加载进程启动的 DLL 可以使用 `threadprivate` 。  
  
 由于 `threadprivate` 基于 **\_\_declspec \(线程\)**， `threadprivate` 变量将存在于进程启动的所有线程，是并行区域给定的线程团队的一部分不的那些线程。  这是您可能希望了解的实现详细信息，，因为您可能注意，例如，调用通常然后预期的 `threadprivate` 用户定义的类型的构造函数。  
  
 一个 destructable 类型的 `threadprivate` 变量不能保证其调用析构函数。  例如：  
  
```  
struct MyType   
{  
    ~MyType();  
};  
  
MyType threaded_var;  
#pragma omp threadprivate(threaded_var)  
int main()   
{  
    #pragma omp parallel  
    {}  
}  
```  
  
 ，当组合并行区域的线程将停止，用户没有关于控件。  如果这些线程存在，在进程退出，线程不会通知进程退出，并且，析构函数不用于在任何线程的 `threaded_var` 调用除退出的一个 \(这里，主线程\)。  以使代码在 `threadprivate` 变量的相应损坏不应计数。  
  
## 示例  
 有关使用 `threadprivate`示例，请参见 [专用](../../../parallel/openmp/reference/private-openmp.md)。  
  
## 请参阅  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)