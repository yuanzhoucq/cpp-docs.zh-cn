---
title: "slice_array 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "slice_array"
  - "valarray/std::slice_array"
  - "std.slice_array"
  - "std::slice_array"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "slice_array 类"
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# slice_array 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过提供了子集数组之间的切片操作支持对象的内部，辅助模板类。valarray 切片定义。  
  
## 语法  
  
```  
template<class Type>  
   class slice_array : public slice {  
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
 类描述与类一起存储到 [valarray](../standard-library/valarray-class.md)类**\<类型\>**对象的引用，[切片](../standard-library/slice-class.md)对象，描述元素序列 **valarray\<Type\>** 对象中的对象。  
  
 模板类的某些操作 valarray 直接在程序间接创建，不能用于。  切片写在下方的运算符使用的内部，辅助模板类：  
  
 `slice_array`\<**类型**\>`valarray`\<**类型**\) 或`operator[]` \(`slice`\)。  
  
 通过窗体编写 **slice\_array\<Type\>** 的表达式只构造 [va&#91;sl&#93;](../Topic/valarray::operator.md) 对象切片的 **sl** of valarray **va**。  slice\_array 类成员的行为像函数然后相应的函数签名定义为 **valarray\<Type\>**，但选择的元素序列仅受影响。  顺序控制。slice\_array 由切片构造函数、索引。切片的第一个元素，。的元素和元素之间的距离的三参数定义。  从 **va**valarray 声明的 **va** 的 slice\_array 剪切 \[`slice`\(2，5，3\]\) 选择使用索引 2，5，8，11 和 14 个元素。**va**。  索引必须是有效的过程。可以有效。  
  
## 示例  
 有关示例的 [slice::slice](../Topic/slice::slice.md) 参见的示例演示如何声明和使用 slice\_array。  
  
## 要求  
 **Header:** \<valarray\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)