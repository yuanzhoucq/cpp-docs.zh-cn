---
title: 编译器警告 （等级 1） C4650 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cb1c9979141e7958b6c2802aaf321efe41e9570
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4650"></a>编译器警告（等级 1）C4650
不在预编译标头; 调试信息将可仅全局符号从标头  
  
 预编译的头文件不是使用 Microsoft 符号化调试信息编译的。  
  
 当链接时，生成的可执行文件或动态链接库文件将不包括调试信息包含在预编译标头中的本地符号。  
  
 通过重新编译预编译标头文件，可以避免此警告[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令行选项。