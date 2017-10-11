---
title: "编译器错误 C3869 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3869
dev_langs:
- C++
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 902786dcce2a9bc8b959eb42b037c7476fad0738
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3869"></a>C3869
gcnew 约束缺少空的参数列表 '（）'  
  
 `gcnew`特殊约束指定不为空的参数列表。 请参阅[泛型类型参数的约束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3869。  
  
```  
// C3869.cpp  
// compile with: /c /clr  
using namespace System;  
generic <typename T>  
where T : gcnew   // C3869  
// try the following line instead  
// where T : gcnew()  
ref class List {};  
```
