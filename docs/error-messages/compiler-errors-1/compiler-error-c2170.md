---
title: 编译器错误 C2170 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2170
dev_langs:
- C++
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad0d19dff10d04d155d8071ffb349664f6b3104e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171085"
---
# <a name="compiler-error-c2170"></a>编译器错误 C2170
identifier： 未声明为函数，不能为内部函数  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  杂注`intrinsic`用于与函数之外的项。  
  
2.  杂注`intrinsic`用于没有内部形式的函数。