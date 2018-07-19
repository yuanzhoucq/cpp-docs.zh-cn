---
title: 链接器工具警告 LNK4205 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4205
dev_langs:
- C++
helpviewer_keywords:
- LNK4205
ms.assetid: d63b9d18-ef3c-4081-9d8d-93077dad13c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1764f04f7733cfb6b9a9a033b8667e53fbbfcc8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300711"
---
# <a name="linker-tools-warning-lnk4205"></a>链接器工具警告 LNK4205
filename 缺少引用模块中; 当前调试信息正在链接对象，如同没有调试信息  
  
 .Pdb 文件包含过期信息。 链接器将继续链接对象但不调试信息。 你可能想要重新编译对象文件使用[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)选项。