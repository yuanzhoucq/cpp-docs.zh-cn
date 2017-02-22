---
title: "链接器工具警告 LNK4222 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4222"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4222"
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具警告 LNK4222
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不应为导出符号“symbol”分配序号  
  
 下列符号不应按序号导出：  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 应总是通过使用 `GetProcAddress` 按名称定位这些函数。  链接器就此类导出发出警告是因为该导出可能导致较大的图像。  如果序号导出的范围大，而导出相对较少，则可能发生这种情况。  例如，  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 要求导出地址表中有 100 个槽，其中 98 个 \(2\-99\) 仅供补充。  而  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 需要两个槽。（注意还可以使用 [\/EXPORT](../../build/reference/export-exports-a-function.md) 链接器选项进行导出。）