---
title: "private (C++) | Microsoft Docs"
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
  - "private_cpp"
  - "private"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "private 关键字 [C++]"
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# private (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
private:  
   [member-list]  
private base-class  
```  
  
## 备注  
 当位于类成员列表之前时，`private` 关键字指定这些成员仅可从成员函数和该类的友元中进行访问。  这适用于声明到下一个访问指示符或类的末尾的所有成员。  
  
 当位于基类的名称之前时，`private` 关键字指定基类的公共成员和受保护成员为派生类的私有成员。  
  
 类中成员的默认访问是私有的。  结构或联合中成员的默认访问是公共的。  
  
 基类的默认访问对于类是私有的，而对于结构是公共的。   联合不能具有基类。  
  
 有关相关信息，请参阅[控制对类成员的访问](../cpp/friend-cpp.md)中的[友元](../cpp/public-cpp.md)、[公共](../cpp/protected-cpp.md)、[受保护的](../misc/controlling-access-to-class-members.md)和成员访问表。  
  
## \/clr 专用  
 在 CLR 类型中，C\+\+访问说明符关键字（**public**、`private` 和 `protected`）可能影响与程序集相关的类型和方法的可见性。  有关详细信息，请参阅[类型和成员可见性](../misc/type-and-member-visibility.md)。  
  
> [!NOTE]
>  使用 [\/LN](../build/reference/ln-create-msil-module.md) 编译的文件不受此行为的影响。  在这种情况下，所有托管类（公共或私有）都将可见。  
  
## END \/clr 专用  
  
## 示例  
  
```  
// keyword_private.cpp  
class BaseClass {  
public:  
   // privMem accessible from member function  
   int pubFunc() { return privMem; }  
private:  
   void privMem;  
};  
  
class DerivedClass : public BaseClass {  
public:  
   void usePrivate( int i )  
      { privMem = i; }   // C2248: privMem not accessible  
                         // from derived class  
};  
  
class DerivedClass2 : private BaseClass {  
public:  
   // pubFunc() accessible from derived class  
   int usePublic() { return pubFunc(); }  
};  
  
int main() {  
   BaseClass aBase;  
   DerivedClass aDerived;  
   DerivedClass2 aDerived2;  
   aBase.privMem = 1;     // C2248: privMem not accessible  
   aDerived.privMem = 1;  // C2248: privMem not accessible  
                          //    in derived class  
   aDerived2.pubFunc();   // C2247: pubFunc() is private in  
                          //    derived class  
}  
```  
  
## 请参阅  
 [控制对类成员的访问](../misc/controlling-access-to-class-members.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)