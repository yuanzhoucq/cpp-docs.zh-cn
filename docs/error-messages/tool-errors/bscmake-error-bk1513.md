---
title: "BSCMAKE 错误 BK1513 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec1e317dcd686a76efba8b8ea8e4782246a3a87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1513"></a>BSCMAKE 错误 BK1513
非增量更新要求所有的 .SBR 文件  
  
 BSCMAKE 无法生成新的浏览信息 (.bsc) 文件，因为一个或多个 .sbr 文件被截断。 若要查找的截断的.sbr 文件的名称，请阅读[BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)伴随此错误的警告。  
  
 BSCMAKE 可使用截断的 .sbr 文件更新 .bsc 文件，但不能生成新文件。 BSCMAKE 可能生成新的 .bsc 文件，原因如下：  
  
-   缺少 .bsc 文件。  
  
-   为 .bsc 文件指定的文件名出错。  
  
-   .bsc 文件损坏。  
  
 若要解决此问题，请删除截断的 .sbr 文件并重新生成，或者清除解决方案并重新生成。 (在 IDE 中，选择**生成**，**清理解决方案**，然后选择**生成**，**重新生成解决方案**。)