---
title: 编译器警告 （等级 4） C4057 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3217ccb0a96fbe02e152ff82dedeb7e8e54b89ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292274"
---
# <a name="compiler-warning-level-4-c4057"></a>编译器警告（等级 4）C4057
“operator”: “identifier1”与“identifier2”在稍微不同的基类型间接寻址上不同  
  
 两个指针表达式引用不同的基类型。 使用表达式时无需转换。  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>通过检查以下可能的原因进行修复  
  
1.  混合签名和未签名的类型。  
  
2.  混合 **short** 和 **long** 类型。