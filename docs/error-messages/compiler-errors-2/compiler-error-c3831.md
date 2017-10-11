---
title: "编译器错误 C3831 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3831
dev_langs:
- C++
helpviewer_keywords:
- C3831
ms.assetid: a125d8dc-b75a-4ea0-b6c7-fe7b119dba25
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 27b330e82c952bd02de7499e8dffe548acfe819c
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3831"></a>编译器错误 C3831
member: class 不能具有固定的数据成员或成员函数返回钉住指针  
  
 [pin_ptr (C + + /cli CLI)](../../windows/pin-ptr-cpp-cli.md)未正确使用。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3831:  
  
```  
// C3831a.cpp  
// compile with: /clr  
ref class Y  
{  
public:  
   int i;  
};  
  
ref class X  
{  
   pin_ptr<int> mbr_Y;   // C3831  
   int^ mbr_Y2;   // OK  
};  
  
int main() {  
   Y y;  
   pin_ptr<int> p = &y.i;  
}  
```  

