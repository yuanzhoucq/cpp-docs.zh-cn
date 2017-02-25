---
title: "gslice_array 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::gslice_array"
  - "gslice_array"
  - "valarray/std::gslice_array"
  - "std.gslice_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "gslice_array 类"
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# gslice_array 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持泛切片的内部，辅助模板类通过提供了泛切片定义子集数组之间的操作 valarray 对象。  
  
## 语法  
  
```  
template<class Type>  
   class gslice_array : public gsplice {  
public:  
   typedef Type value_type;  
   void operator=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator=(  
      const Type& x  
   ) const;  
  
   void operator*=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator/=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator%=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator+=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator-=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator^=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator&=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator|=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator<<=(  
      const valarray<Type>& x  
   ) const;  
  
   void operator>>=(  
      const valarray<Type>& x  
   ) const;  
  
// The rest is private or implementation defined  
}  
```  
  
## 备注  
 类以及对象描述元素序列。**valarrayType\<\>** 对象中 [gslice](../standard-library/gslice-class.md) 类的 **gs**。描述存储为对象类 [valarray](../standard-library/valarray-class.md)**\<类型\>va** 的引用的对象。  
  
 通过窗体编写 [VA &#91;&#93; gs](../Topic/valarray::operator.md)的表达式只构造 **gslice\_array\<Type\>** 对象。  gslice\_array 类成员的行为像函数然后相应的函数签名定义为 **valarray\<Type\>**，但选择的元素序列仅受影响。  
  
 模板类的某些操作 valarray 直接在程序间接创建，不能用于。  切片写在下方的运算符使用内部辅助模板类：  
  
 `gslice_array`\<**类型**\>`valarray`\<**类型**\>`operator[]` \(**const** 或**gslice&**\)。  
  
 通过将窗体的 **va\[gsl\]**的表达式只构造 **gslice\_array\<Type\>** 对象 valarray 切片的 **va**，**gsl**。  gslice\_array 类成员的行为像函数然后相应的函数签名定义为 **valarray\<Type\>**，但选择的元素序列仅受影响。  顺序控制。gslice\_array 由切片构造函数、索引在第一切片的第一个元素，。的每个切片的元素和元素之间的距离的三参数定义。每个切片。  
  
 在下面的示例中：  
  
```  
const size_t lv[] = {2, 3};  
const size_t dv[] = {7, 2};  
const valarray<size_t> len(lv, 2), str(dv, 2);  
// va[gslice(3, len, str)] selects elements with  
//   indices 3, 5, 7, 10, 12, 14  
```  
  
 索引必须是有效的过程。可以有效。  
  
## 示例  
 有关示例的 [gslice::gslice](../Topic/gslice::gslice.md) 参见的示例演示如何声明和使用 slice\_array。  
  
## 要求  
 **Header:** \<valarray\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)