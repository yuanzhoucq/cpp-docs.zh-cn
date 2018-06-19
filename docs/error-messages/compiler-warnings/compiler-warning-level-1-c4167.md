---
title: 编译器警告 （等级 1） C4167 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4167
dev_langs:
- C++
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c72d6fd88b8c4797b2e352d6d30dbf797a23a00d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280327"
---
# <a name="compiler-warning-level-1-c4167"></a>编译器警告（等级 1）C4167
函数：仅可用作内部函数  
  
 **#pragma 函数** 尝试强制编译器对必须以内部形式使用的函数使用常规调用。 将忽略杂注。  
  
 若要避免此警告，请删除 **#pragma 函数**。  
  
## <a name="example"></a>示例  
  
```  
// C4167.cpp  
// compile with: /W1  
#include <malloc.h>  
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only  
int main(){}  
```