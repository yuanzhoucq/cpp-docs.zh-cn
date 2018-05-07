---
title: 资源编译器错误 RC1022 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1022
dev_langs:
- C++
helpviewer_keywords:
- RC1022
ms.assetid: 30a0f3c7-08a8-4c40-b0de-46ee5feb789d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c81a6afc3316c163e9d1451af51f57f208b6a209
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1022"></a>资源编译器错误 RC1022
预期 #endif  
  
 `#if`， **#ifdef**，或 **#ifndef**指令未终止与`#endif`指令。  
  
 请确保有`#if`， **#ifdef**，或 **#ifndef**实际上此语句前的语句。