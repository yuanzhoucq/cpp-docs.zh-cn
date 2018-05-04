---
title: 导入数据使用 __declspec （dllimport） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9877c5a229c3cabcb7703dd2617d1d57e3512f0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="importing-data-using-declspecdllimport"></a>使用 __declspec(dllimport) 导入数据
在使用的数据的情况下 **__declspec （dllimport)** 是中移除的间接层的方便项。 当你从 DLL 导入数据时，你仍必须经历的导入地址表。 之前 **__declspec （dllimport)**，这意味着你必须记住从 DLL 导出的访问数据时如何额外级别的间接寻址：  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 然后会将导出中的数据你。DEF 文件：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 并且在 DLL 外访问它：  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 当你将数据作为 **__declspec （dllimport)**，编译器自动为你生成的间接寻址代码。 不再需要担心上述步骤。 如前面所述，不要使用 **__declspec （dllimport)** 生成 DLL 时对数据的声明。 在该 DLL 中的函数不使用导入地址表要访问数据的对象;因此，你将没有额外级别的间接寻址存在。  
  
 若要从 DLL 自动导出数据，请使用此声明：  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## <a name="see-also"></a>请参阅  
 [导入到应用程序中](../build/importing-into-an-application.md)