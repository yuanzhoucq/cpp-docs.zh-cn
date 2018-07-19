---
title: 资源编译器错误 RW1025 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba216e63cb0cae92b4541800493a2fb6195553a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320009"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>资源编译器错误 RW1025
远堆内存不足  
  
 检查可能占用过多的空间驻留在内存中的软件。 CHKDSK 程序用于找出你具有的内存量。  
  
 如果要创建较大的资源文件，请将资源脚本拆分为两个文件。 在创建后两个.res 文件，使用 MS-DOS 命令行以将其联接起来：  
  
```  
copy first.res /b + second.res /b full.res  
```