---
title: "编译器警告（等级 1）C4346 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4346"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4346"
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4346
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”: 依赖名称不是类型  
  
 如果依赖名称将被视为一个类型，则 [typename](../../cpp/typename.md) 关键字是必需的。  这是在 Visual C\+\+ .NET 2003 编译器中进行的重大更改，以便符合 ISO C\+\+ 标准。  
  
 为使代码在 Visual C\+\+ 的所有版本中以同样方式工作，请将 `typename` 添加到声明中。  
  
 下面的示例生成 C4346：  
  
```  
// C4346.cpp  
// compile with: /WX /LD  
template<class T>  
struct C {  
   T::X* x;   // C4346  
   // try the following line instead  
   // typename T::X* x;  
};  
```  
  
 下面的示例显示 **typename** 关键字是必需的其他示例：  
  
```  
// C4346b.cpp  
// compile with: /LD /W1  
template<class T>  
const typename T::X& f(typename T::Z* p);   // Required in both places  
  
template<class T, int N>  
struct L{};  
  
template<class T>  
struct M : public L<typename T::Type, T::Value>   
{   // required on type argument, not on non-type argument  
   typedef typename T::X   Type;  
   Type f();   // OK: "Type" is a type-specifer  
   typename T::X g();   // typename required  
   operator typename T::Z();   // typename required      
};  
```  
  
 并且，  
  
```  
// C4346c.cpp  
// compile with: /LD /WX  
struct Y {  
   typedef int Y_t;  
};  
  
template<class T>  
struct A {  
   typedef Y A_t;  
};  
  
template<class T>  
struct B {  
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here  
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here  
};  
```