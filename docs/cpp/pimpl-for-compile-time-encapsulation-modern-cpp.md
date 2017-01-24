---
title: "用于编译时封装的 Pimpl（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用于编译时封装的 Pimpl（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*pimpl 惯例* 是隐藏实现的接口耦合，最小化和分隔一个现代的技术。  Pimpl 为“Fr 实现的指针是短”。您可能已经熟悉的概念，但由类似彻斯特猫或编译器防火墙固有的任何其他名称识别它。  
  
## 为何使用 pimpl?  
 这是 pimpl 思路可以如何提高软件开发生命期：  
  
-   编译依赖关系，低估的。  
  
-   接口与实现分离。  
  
-   可移植性。  
  
## Pimpl 标题  
  
```cpp  
  
// my_class.h  
class my_class {  
   //  ... all public and protected stuff goes here ...  
private:  
   class impl; unique_ptr<impl> pimpl; // opaque type here  
};  
  
```  
  
 pimpl 个 Rebuild 和级联避免生成脆弱的对象布局。  它 \(传递\) 的常见类型非常适合的。  
  
## Pimpl 实现  
 定义在 .cpp 文件中的 `impl` 类。  
  
```cpp  
  
// my_class.cpp  
class my_class::impl {  // defined privately here  
  // ... all private data and functions: all of these  
  //     can now change without recompiling callers ...  
};  
my_class::my_class(): pimpl( new impl )  
{  
  // ... set impl values ...   
}  
```  
  
## 最佳实践  
 是否考虑将引发非的交换专用化的支持。  
  
## 请参阅  
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)