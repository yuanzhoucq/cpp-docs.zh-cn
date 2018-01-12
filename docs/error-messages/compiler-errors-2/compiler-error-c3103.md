---
title: "编译器错误 C3103 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3103
dev_langs: C++
helpviewer_keywords: C3103
ms.assetid: 7984bd3e-d51d-43e4-b6f4-08c1e9fb9704
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c640db4e67c2de728260ef4f4843c9bb6f73d08f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3103"></a>编译器错误 C3103
自变量： 重复的命名的参数  
  
 属性不能重复命名自变量。  
  
 有关详细信息，请参阅 [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3103。  
  
```  
// C3103.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref class Attr : public Attribute {  
public:  
   int m_t;  
};  
  
[Attr(m_t = 10, m_t = 1)]   // C3103  
// try the following line instead  
// [Attr(m_t = 10)]  
ref class A {};  
```