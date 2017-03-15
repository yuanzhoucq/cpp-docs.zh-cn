---
title: "卸载延迟加载的 DLL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__FUnloadDelayLoadedDLL2"
  - "DLL 的延迟加载, 卸载"
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 卸载延迟加载的 DLL
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认提供的延迟加载 Helper 检查延迟加载描述符，确定是否具有 pUnloadIAT 字段中的原始导入地址表 \(IAT\) 的指针和副本。  如果有，它将列表中的指针保存到导入延迟描述符。  这使得 Helper 函数能够按名称查找 DLL 以支持显式卸载找到的 DLL。  
  
 下面是与显式卸载延迟加载的 DLL 关联的结构和函数：  
  
```  
//  
// Unload support from delayimp.h  
//  
  
// routine definition; takes a pointer to a name to unload  
  
ExternC  
BOOL WINAPI  
__FUnloadDelayLoadedDLL2(LPCSTR szDll);  
  
// structure definitions for the list of unload records  
typedef struct UnloadInfo * PUnloadInfo;  
typedef struct UnloadInfo {  
    PUnloadInfo     puiNext;  
    PCImgDelayDescr pidd;  
    } UnloadInfo;  
  
// from delayhlp.cpp  
// the default delay load helper places the unloadinfo records in the   
// list headed by the following pointer.  
ExternC  
PUnloadInfo __puiHead;  
```  
  
 UnloadInfo 结构用一个 C\+\+ 类实现，该类将 **LocalAlloc** 和 **LocalFree** 实现分别用作其 **new** 运算符和 **delete** 运算符。  这些选项保留在列表头为 \_\_puiHead 的标准链接表中。  
  
 调用 \_\_FUnloadDelayLoadedDLL 将尝试查找在加载的 DLL 列表中提供的名称（要求完全匹配）。  如果找到了，pUnloadIAT 中的 IAT 副本被复制到正在运行的 IAT 的顶端以还原 thunk 指针，并用 **FreeLibrary** 释放库，断开匹配的 **UnloadInfo** 记录与列表的链接并删除该记录，并返回 TRUE。  
  
 函数 \_\_FUnloadDelayLoadedDLL2 的参数区分大小写。  例如，应该指定：  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 而不是：  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## 请参阅  
 [Understanding the Helper Function](http://msdn.microsoft.com/zh-cn/6279c12c-d908-4967-b0b3-cabfc3e91d3d)