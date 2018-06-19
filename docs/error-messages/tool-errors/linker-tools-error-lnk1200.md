---
title: 链接器工具错误 LNK1200 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1200
dev_langs:
- C++
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab32939c55dce5e27f907f3d23e639b24741cdc3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298819"
---
# <a name="linker-tools-error-lnk1200"></a>链接器工具错误 LNK1200
读取程序数据库 filename 时出错  
  
 无法读取程序数据库 (PDB)。  
  
 可以通过文件损坏导致此错误。  
  
 如果`filename`是 PDB 对象文件，重新编译对象文件使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)。  
  
 如果`filename`是主输出文件中的 PDB，并且此错误出现在增量链接期间，删除 PDB 和重新链接。