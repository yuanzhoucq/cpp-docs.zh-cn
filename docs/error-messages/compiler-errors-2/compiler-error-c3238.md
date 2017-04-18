---
title: "编译器错误 C3238 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3238
dev_langs:
- C++
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 7f9ddf5c7772bfed7c1789e9927cbe46bd1f712c
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3238"></a>编译器错误 C3238
“type”：已将某个同名类型转发到程序集“assembly”  
  
 通过在引用的程序集中类型转发语法，已在客户端应用程序中定义的类型也被定义了。 两种类型均不能在应用程序的范围内定义。  
  
 请参阅[类型转发 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例创建了一个包含从另一个程序集已转发的类型的程序集。  
  
```  
// C3238.cpp  
// compile with: /clr /LD  
public ref class R {};  
```  
  
## <a name="example"></a>示例  
 下面的示例创建用来包含该类型定义的程序集，但不仅仅包含类型转发语法。  
  
```  
// C3238_b.cpp  
// compile with: /clr /LD  
#using "C3238.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>示例  
 以下示例生成 C3238。  
  
```  
// C3238_c.cpp  
// compile with: /clr /c  
// C3238 expected  
// Delete the following line to resolve.  
#using "C3238_b.dll"  
public ref class R {};  
```
