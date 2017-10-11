---
title: "编译器错误 C3669 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3669
dev_langs:
- C++
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 56e725bd03ecd1ba4f8ab3d77eeab6633a9ef062
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3669"></a>编译器错误 C3669
member： 重写的说明符替代不允许在静态成员函数或构造函数  
  
 未正确指定替代。 有关详细信息，请参阅[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3669。  
  
```  
// C3669.cpp  
// compile with: /clr  
public ref struct R {  
   R() override {}   // C3669  
};  
```
