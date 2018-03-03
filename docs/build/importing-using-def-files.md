---
title: "使用 DEF 文件导入 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee213f1aa381415444288dbab4473cae6f5fc7b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="importing-using-def-files"></a>使用 DEF 文件导入
如果你选择使用**__declspec （dllimport)**和.def 文件，应更改.def 文件以使用代替常量的数据来减少不正确编码会引起问题的可能性：  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 下表说明了为什么。  
  
|关键字|发出中的导入库|导出|  
|-------------|---------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 使用**__declspec （dllimport)**和同时列出了常量`imp`版本和.lib DLL 中的未修饰的名称导入创建以允许显式链接的库。 使用**__declspec （dllimport)**和数据列表仅`imp`名称的版本。  
  
 如果使用常量时，可以使用以下代码构造任一访问`ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 或  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 但是，如果.def 文件中使用数据，仅使用以下定义编译的代码可以访问变量`ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 使用常量的风险更大，因为如果你忘记了使用额外级别的间接寻址，你可能无法访问的导入地址表指向的变量-变量本身。 由于导入地址表当前由只读通过编译器和链接器，此类型的问题可以经常表现为访问冲突。  
  
 如果它发现.def 文件中的常量来应对这种情况下，当前的 Visual c + + 链接器将发出警告。 使用常量的唯一的真正原因是如果你不能重新编译的头文件中未列出某些对象文件**__declspec （dllimport)**原型上。  
  
## <a name="see-also"></a>请参阅  
 [导入到应用程序中](../build/importing-into-an-application.md)
