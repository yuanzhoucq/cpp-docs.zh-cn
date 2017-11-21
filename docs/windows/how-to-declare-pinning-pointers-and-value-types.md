---
title: "如何： 声明钉住指针和值类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04ee5a54ec797324aa0bad6e72f8cfc0861d2a38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>如何：声明钉住指针和值类型
值类型可以隐式装箱。 然后可以声明钉住指针指向值的类型对象本身并使用**pin_ptr**为装箱的值类型。  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
// pin_ptr_value.cpp  
// compile with: /clr  
value struct V {  
   int i;  
};  
  
int main() {  
   V ^ v = gcnew V;   // imnplicit boxing  
   v->i=8;  
   System::Console::WriteLine(v->i);  
   pin_ptr<V> mv = &*v;  
   mv->i = 7;  
   System::Console::WriteLine(v->i);  
   System::Console::WriteLine(mv->i);  
}  
```  
  
### <a name="output"></a>输出  
  
```  
8  
7  
7  
```  
  
## <a name="see-also"></a>另请参阅  
 [pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)