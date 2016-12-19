---
title: "链接器工具警告 LNK4104 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4104"
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具警告 LNK4104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符号“symbol”的导出应为 PRIVATE  
  
 `symbol` 可以为下列之一：  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllGetDocumentation`  
  
-   `DllInitialize`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllRegisterServerExW`  
  
-   `DllUnload`  
  
-   `DllUnregisterServer`  
  
-   `RasCustomDeleteEntryNotify`  
  
-   `RasCustomDial`  
  
-   `RasCustomDialDlg`  
  
-   `RasCustomEntryDlg`  
  
 当生成 DLL 的导入库并导出上述函数之一，但没有在模块定义文件中将该函数指定为 PRIVATE 时会发出此警告。  通常情况下，导出这些函数仅供 OLE 使用。  如果将它们放在导入库中，则当链接到此库的程序错误地调用它们时会导致异常行为。  有关 PRIVATE 关键字的更多信息，请参见 [EXPORTS](../../build/reference/exports.md)。