---
title: "链接器工具警告 LNK4104 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4104
dev_langs: C++
helpviewer_keywords: LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d049ef8663798236250977e90d12c2971dec443
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4104"></a>链接器工具警告 LNK4104
导出符号 symbol 应为私有  
  
 `symbol`可以是以下之一：  
  
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
  
 此警告时生成 DLL 导入库发出，且导出上述函数之一，而无需在模块定义文件中指定它为私有。 一般情况下，这些函数仅由 OLE 用于导出。 将它们放置在导入库可能会导致异常行为时程序链接到库不正确地调用它们。 PRIVATE 关键字的详细信息，请参阅[导出](../../build/reference/exports.md)。