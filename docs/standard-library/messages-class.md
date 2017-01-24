---
title: "messages 类 | Microsoft Docs"
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
  - "messages"
  - "xlocmes/std::messages"
  - "std.messages"
  - "std::messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "messages 类"
ms.assetid: c4c71f40-4f24-48ab-9f7c-daccd8d5bd83
caps.latest.revision: 18
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# messages 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述一个对象来充当区域设置 facet，以便从给定区域设置的国际化消息目录中检索本地化消息。  
  
 目前，虽然已实现消息类，但没有任何消息。  
  
## 语法  
  
```  
template <class CharType>  
   class messages : public messages_base;  
```  
  
#### 参数  
 `CharType`  
 在程序中用于对区域设置中的字符进行编码的类型。  
  
## 备注  
 对于任何区域设置 facet，静态对象 ID 的初始存储值为零。 第一次尝试访问其存储的值中存储唯一正值中的 **id。**  
  
 大致来说，此 facet 会打开基类 messages\_base 中定义的消息目录，检索所需要的信息，然后关闭目录。  
  
### 构造函数  
  
|||  
|-|-|  
|[消息](../Topic/messages::messages.md)|消息 facet 构造函数。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/messages::char_type.md)|一种用于显示消息的字符类型。|  
|[string\_type](../Topic/messages::string_type.md)|一种类型，此类型描述包含 `basic_string` 类型字符的 `CharType` 类型字符串。|  
  
### 成员函数  
  
|||  
|-|-|  
|[关闭](../Topic/messages::close.md)|关闭消息目录。|  
|[do\_close](../Topic/messages::do_close.md)|一种为失去消息目录而调用的虚拟函数。|  
|[do\_get](../Topic/messages::do_get.md)|一种为检索消息目录而调用的虚拟函数。|  
|[do\_open](../Topic/messages::do_open.md)|一种为打开消息目录而调用的虚拟函数。|  
|[get](../Topic/messages::get.md)|检索消息目录。|  
|[打开](../Topic/messages::open.md)|打开消息目录。|  
  
## 要求  
 **标头：**\<locale\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<locale\>](../standard-library/locale.md)   
 [messages\_base 类](../standard-library/messages-base-class.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)