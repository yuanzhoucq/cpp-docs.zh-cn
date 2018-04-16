---
title: "链接器工具警告 LNK4071 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4071
dev_langs:
- C++
helpviewer_keywords:
- LNK4071
ms.assetid: 803f8c34-8219-4f55-a4ae-7133ceff2ba3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d3be5732ea9fd05fd8bae61773431e7d092dd9c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4071"></a>链接器工具警告 LNK4071
无法在后续的链接上以增量方式链接  
  
 找到链接的多个定义，则为一个或多个符号，但[/强制](../../build/reference/force-force-file-output.md)或**/FORCE:MULTIPLE**用于创建输出文件而不考虑错误。 链接删除增量状态 (.ilk) 文件。