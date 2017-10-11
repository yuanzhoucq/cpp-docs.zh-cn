---
title: "限制 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 2d1cdbff84966e7926b30ef70c40581cc3801a93
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="restrict"></a>restrict
**Microsoft 专用**  
  
 应用于函数声明或定义，该声明或定义返回指针类型，并通知编译器该函数将返回不会将任何其他指针作为别名的对象。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec(restrict) return_type f();  
```  
  
## <a name="remarks"></a>备注  
 编译器将传播 `__declspec(restrict)`。 例如，CRT `malloc` 函数是使用 `__declspec(restrict)` 修饰的，因此，使用 `malloc` 初始化为内存位置的指针也暗示不使用别名。  
  
 编译器不检查指针到底有没有使用别名。 开发人员负责确保程序没有对使用 `restrict __declspec` 修饰符标记的指针使用别名。  
  
 在变量上相似的语义，请参阅[__restrict](../cpp/extension-restrict.md)。  
  
## <a name="example"></a>示例  
 请参阅[noalias](../cpp/noalias.md)的使用示例`restrict`。  
  
 有关限制关键字是 c + + AMP 的信息，请参阅[限制 (c + + AMP)](../cpp/restrict-cpp-amp.md)。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)
