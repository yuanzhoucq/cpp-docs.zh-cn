---
title: 链接器工具警告 LNK4222 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359af4c4d3b1079b2d56f108bff0ee1488ea71f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302144"
---
# <a name="linker-tools-warning-lnk4222"></a>链接器工具警告 LNK4222
不应为导出的符号 symbol 分配是执行序号  
  
 不应该按序号导出以下符号：  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 这些函数始终位于的名称，使用`GetProcAddress`。 链接器警告有关这种导出是因为它可能会导致更大的映像。 这可能是如果序号导出的范围很大，包含相对较少的导出。 例如，应用于对象的  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 需要有 100 个槽中其中 98 个导出地址表 (2-99) 仅供补充。 另一方面  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 将需要两个槽。 (请注意，你还可以将导出与[/导出](../../build/reference/export-exports-a-function.md)链接器选项。)