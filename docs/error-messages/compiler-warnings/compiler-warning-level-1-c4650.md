---
title: "编译器警告 （等级 1） C4650 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: af10d05562c0c60c6a010e105441533362d058df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4650"></a>编译器警告（等级 1）C4650
不在预编译标头; 调试信息将可仅全局符号从标头  
  
 预编译的头文件不是使用 Microsoft 符号化调试信息编译的。  
  
 当链接时，生成的可执行文件或动态链接库文件将不包括调试信息包含在预编译标头中的本地符号。  
  
 通过重新编译预编译标头文件，可以避免此警告[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)命令行选项。