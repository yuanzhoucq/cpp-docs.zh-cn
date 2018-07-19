---
title: 编译器错误 C2129 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2129
dev_langs:
- C++
helpviewer_keywords:
- C2129
ms.assetid: 21a8223e-1d22-4baa-9ca1-922b7f751dd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d151c774672b1788ca893a9812deb3e41100dc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171713"
---
# <a name="compiler-error-c2129"></a>编译器错误 C2129
静态函数 function 声明但未定义  
  
 对进行的前向引用`static`永远不会定义的函数。  
  
 A`static`必须在文件范围内定义函数。 如果函数在另一个文件中定义的必须将它声明`extern`。