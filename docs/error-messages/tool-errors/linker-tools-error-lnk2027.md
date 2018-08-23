---
title: 链接器工具错误 LNK2027 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2027
dev_langs:
- C++
helpviewer_keywords:
- LNK2027
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156310a0d21651b9fd2ee6002ace419db4996681
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301367"
---
# <a name="linker-tools-error-lnk2027"></a>链接器工具错误 LNK2027
无法解析的模块引用 module  
  
 传递到链接器的文件都不使用指定的模块上具有依赖关系**进行**也直接传递到链接器。  
  
 若要解决 LNK2027，请执行以下操作：  
  
-   不要传递到链接器具有模块依赖项的文件。  
  
-   指定的模块**进行**。  
  
-   如果该模块是安全的 .netmodule，则将它直接传递给链接器。  
  
 有关详细信息，请参阅[进行 （添加 MSIL 模块的程序集）](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)和[用作链接器输入的.netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。