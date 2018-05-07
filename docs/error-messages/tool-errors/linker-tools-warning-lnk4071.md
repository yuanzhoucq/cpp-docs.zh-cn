---
title: 链接器工具警告 LNK4071 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4071
dev_langs:
- C++
helpviewer_keywords:
- LNK4071
ms.assetid: 803f8c34-8219-4f55-a4ae-7133ceff2ba3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cb0d4b8d78eb8c7cf1812abb1a7981c605f2c4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4071"></a>链接器工具警告 LNK4071
无法在后续的链接上以增量方式链接  
  
 找到链接的多个定义，则为一个或多个符号，但[/强制](../../build/reference/force-force-file-output.md)或 **/FORCE:MULTIPLE**用于创建输出文件而不考虑错误。 链接删除增量状态 (.ilk) 文件。