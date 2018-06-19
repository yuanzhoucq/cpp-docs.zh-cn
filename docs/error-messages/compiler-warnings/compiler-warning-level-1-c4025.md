---
title: 编译器警告 （等级 1） C4025 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4025
dev_langs:
- C++
helpviewer_keywords:
- C4025
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e84ba11c7bed7420a9a1c699361612ef2002d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273944"
---
# <a name="compiler-warning-level-1-c4025"></a>编译器警告（等级 1）C4025
“编号”: 基指针传递给带变量参数的函数: 参数号  
  
 将基指针传递给使用变量参数的函数会导致指针被规范化，结果不可预知。 请勿将基指针传递给带变量参数的函数。