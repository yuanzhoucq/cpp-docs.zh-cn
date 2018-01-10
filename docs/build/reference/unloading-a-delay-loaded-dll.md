---
title: "卸载延迟加载的 DLL |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b47969da4c560f28c07ac09caef83873e362ddc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="unloading-a-delay-loaded-dll"></a>卸载延迟加载的 DLL
默认提供延迟加载 helper 检查以查看的延迟加载描述符 pUnloadIAT 字段中是否具有为指针，原始的导入地址表 (IAT) 的副本。 如果是这样，它会将指针保存到导入延迟描述符列表中。 这使要按名称以支持显式卸载该 DLL 中查找该 DLL 的帮助器函数。  
  
 以下是关联的结构和函数的显式卸载延迟加载的 DLL:  
  
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
  
 使用使用的 c + + 类实现 UnloadInfo 结构**LocalAlloc**和**LocalFree**作为其运算符的实现**新**和运算符**删除**分别。 这些选项将保留在作为列表的开头使用 __puiHead 的标准链接列表。  
  
 调用 __FUnloadDelayLoadedDLL 将尝试查找名称在加载 Dll （完全匹配，则需要） 的列表中提供。 如果找到，则复制中 pUnloadIAT IAT 的副本正在运行的 IAT 要还原的转换 （thunk） 指针的顶部，通过库用来释放**FreeLibrary**，匹配**UnloadInfo**记录为取消链接列表和删除，并返回 TRUE。  
  
 函数 __FUnloadDelayLoadedDLL2 的自变量是区分大小写。 例如，则会指定：  
  
```  
__FUnloadDelayLoadedDLL2("user32.DLL");  
```  
  
 而不是：  
  
```  
__FUnloadDelayLoadedDLL2("User32.DLL");.  
```  
  
## <a name="see-also"></a>请参阅  
 [了解 Helper 函数](understanding-the-helper-function.md)