---
title: "资源编译器错误 RW1025 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 487968f8a1242dd4c36e4bbd9b4ede08a5ab4d95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rw1025"></a>资源编译器错误 RW1025
远堆内存不足  
  
 检查可能占用过多的空间驻留在内存中的软件。 CHKDSK 程序用于找出你具有的内存量。  
  
 如果要创建较大的资源文件，请将资源脚本拆分为两个文件。 在创建后两个.res 文件，使用 MS-DOS 命令行以将其联接起来：  
  
```  
copy first.res /b + second.res /b full.res  
```