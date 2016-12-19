---
title: "enable_shared_from_this 类 | Microsoft Docs"
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
  - "tr1.enable_shared_from_this"
  - "enable_shared_from_this"
  - "std.tr1.enable_shared_from_this"
  - "memory/std::tr1::enable_shared_from_this"
  - "std::tr1::enable_shared_from_this"
  - "tr1::enable_shared_from_this"
  - "std.enable_shared_from_this"
  - "memory/std::enable_shared_from_this"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "enable_shared_from_this 类"
  - "enable_shared_from_this 类 [TR1]"
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
caps.latest.revision: 22
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# enable_shared_from_this 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

帮助生成一个 `shared_ptr`。  
  
## 语法  
  
```  
template<class Ty>  
    class enable_shared_from_this {  
public:  
    shared_ptr<Ty> shared_from_this();  
    shared_ptr<const Ty> shared_from_this() const;  
  
protected:  
    enable_shared_from_this();  
    enable_shared_from_this(const enable_shared_from_this&);  
    enable_shared_from_this& operator=(const enable_shared_from_this&);  
    ~enable_shared_from_this();  
    };  
```  
  
#### 参数  
 `Ty`  
 由共享指针控制的类型。  
  
## 备注  
 对象，派生自 `enable_shared_from_this` 可以使用 `shared_from_this` 中成员函数来创建的方法 [shared\_ptr](../standard-library/shared-ptr-class.md) 与现有共享所有权的实例的所有者 `shared_ptr` 所有者。 否则为如果您创建一个新 `shared_ptr` 使用 `this`, ，它是不同于现有 `shared_ptr` 可能会导致无效的引用，或者导致不止一次删除的对象的所有者。  
  
 构造函数、 析构函数和赋值运算符保护系统，以帮助防止意外误。 模板参数类型 `Ty` 必须是派生类的类型。  
  
 有关用法的示例，请参阅 [enable\_shared\_from\_this::shared\_from\_this](../Topic/enable_shared_from_this::shared_from_this.md)。  
  
## 要求  
 **标头：**\<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [enable\_shared\_from\_this::shared\_from\_this](../Topic/enable_shared_from_this::shared_from_this.md)   
 [shared\_ptr 类](../standard-library/shared-ptr-class.md)