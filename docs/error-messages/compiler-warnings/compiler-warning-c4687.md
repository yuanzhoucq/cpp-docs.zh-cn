---
title: "编译器警告 C4687 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4687
dev_langs:
- C++
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 266213deba94bdc925747d57dee184aca5f5f605
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4687"></a>编译器警告 C4687
class： 密封的抽象类不能实现接口 interface  
  
 密封的抽象类型是通常仅用于容纳静态成员函数。  
  
 有关详细信息，请参阅[抽象](../../windows/abstract-cpp-component-extensions.md)和[密封](../../windows/sealed-cpp-component-extensions.md)。  
  
 默认情况下，作为错误发出 C4687。 你可以取消与 C4687[警告](../../preprocessor/warning.md)杂注。 如果不能确定你想要在密封的抽象类型中实现接口，可以取消 C4687。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4687。  
  
```  
// C4687.cpp  
// compile with: /clr /c  
interface class A {};  
  
ref struct B sealed abstract : A {};   // C4687  
ref struct C sealed : A {};   // OK  
ref struct D abstract : A {};   // OK  
```
