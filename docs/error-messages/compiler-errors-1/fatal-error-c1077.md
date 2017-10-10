---
title: "错误 C1077 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1077
dev_langs:
- C++
helpviewer_keywords:
- C1077
ms.assetid: 514d66f4-b512-479a-b793-ebf45c91e15b
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: a08d0592bb50edf57124a034d2397e10262009b4
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="fatal-error-c1077"></a>错误 C1077
编译器限制：命令行选项数不得超过其限定值  
  
 命令行选项数超过了内部限制。  
  
 可能多用 [/D](../../build/reference/d-preprocessor-definitions.md)定义的符号太多。 （改为将定义放置在头文件中。）
