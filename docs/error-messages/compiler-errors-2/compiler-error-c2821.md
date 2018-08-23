---
title: 编译器错误 C2821 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2821
dev_langs:
- C++
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8c134d84ef27110cde83d54cbb8e46aa6a39efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236554"
---
# <a name="compiler-error-c2821"></a>编译器错误 C2821
operator new 的第一个正式参数必须是 unsigned 的 int  
  
第一个形参[运算符 new](../../standard-library/new-operators.md#op_new)必须是无符号`int`。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2821:  
  
```cpp  
// C2821.cpp  
// compile with: /c  
void * operator new( /* unsigned int,*/ void * );   // C2821  
void * operator new( unsigned int, void * );  
```