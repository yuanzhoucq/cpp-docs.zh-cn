---
title: "可变数据成员 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "mutable_cpp"
  - "mutable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mutable 关键字 [C++]"
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 可变数据成员 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此关键字只能应用于类的非静态和非常量数据成员。  如果某个数据成员被声明为 `mutable`，则从 **const** 成员函数为此数据成员赋值是合法的。  
  
## 语法  
  
```  
  
mutable member-variable-declaration;  
```  
  
## 备注  
 例如，以下代码在编译时不会出错，因为 `m_accessCount` 已声明为 `mutable`，因此可以由 `GetFlag` 修改，即使 `GetFlag` 是常量成员函数。  
  
```  
// mutable.cpp  
class X  
{  
public:  
   bool GetFlag() const  
   {  
      m_accessCount++;  
      return m_flag;  
   }  
private:  
   bool m_flag;  
   mutable int m_accessCount;  
};  
  
int main()  
{  
}  
```  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)