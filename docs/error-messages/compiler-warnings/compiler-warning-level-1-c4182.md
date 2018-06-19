---
title: 编译器警告 （等级 1） C4182 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4182
dev_langs:
- C++
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79e86076a9d8218d08bd7437e2a06878b6ee91ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278176"
---
# <a name="compiler-warning-level-1-c4182"></a>编译器警告（等级 1）C4182
\#包括嵌套级别为 number 层;可能的无限递归  
  
 由于嵌套的包含文件数量过多，编译器用尽了堆上的空间。 当包含文件包含在另一个包含文件中时，它就是嵌套的。  
  
 此消息是信息性消息，出现在错误 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)之前。