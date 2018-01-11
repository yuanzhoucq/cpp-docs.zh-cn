---
title: "编译器错误 C3465 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3465
dev_langs: C++
helpviewer_keywords: C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8b7706779684158da8b1bc7187621420e52a640a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3465"></a>编译器错误 C3465
若要使用类型“type”，必须引用程序集“assembly”  
  
 在重新编译客户端之前，类型转发都将适用于客户端应用程序。 重新编译时，包含客户端应用程序中所用类型定义的每个程序集都将需要一个引用。  
  
 有关详细信息，请参阅[类型转发 (C + + /cli CLI)](../../windows/type-forwarding-cpp-cli.md)。  
  
## <a name="example"></a>示例  
 以下示例生成包含类型新位置的程序集。  
  
```  
// C3465.cpp  
// compile with: /clr /LD  
public ref class R {  
public:  
   ref class N {};  
};  
```  
  
## <a name="example"></a>示例  
 以下示例生成用来包含类型定义的程序集，但现在却包含此类型的转发语法。  
  
```  
// C3465_b.cpp  
// compile with: /clr /LD  
#using "C3465.dll"  
[ assembly:TypeForwardedTo(R::typeid) ];  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C3465。  
  
```  
// C3465_c.cpp  
// compile with: /clr  
// C3465 expected  
#using "C3465_b.dll"  
// Uncomment the following line to resolve.  
// #using "C3465.dll"  
  
int main() {  
   R^ r = gcnew R();  
}  
```