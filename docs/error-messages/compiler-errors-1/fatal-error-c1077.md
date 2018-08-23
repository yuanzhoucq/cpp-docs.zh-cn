---
title: 错误 C1077 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1077
dev_langs:
- C++
helpviewer_keywords:
- C1077
ms.assetid: 514d66f4-b512-479a-b793-ebf45c91e15b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfc2881180fd2b3948c0e9ed7b3125dc03d0f093
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226358"
---
# <a name="fatal-error-c1077"></a>错误 C1077
编译器限制：命令行选项数不得超过其限定值  
  
 命令行选项数超过了内部限制。  
  
 可能多用 [/D](../../build/reference/d-preprocessor-definitions.md)定义的符号太多。 （改为将定义放置在头文件中。）