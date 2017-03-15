---
title: "编译器 COM 支持类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_raise_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, COM 支持"
  - "COM, 编译器支持"
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器 COM 支持类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 标准类用于支持某些 COM 类型。  这些类是在从类型库生成的 comdef.h 文件和头文件中定义的。  
  
|类|用途|  
|-------|--------|  
|[\_bstr\_t](../cpp/bstr-t-class.md)|包装 `BSTR` 类型，以提供有用的运算符和方法。|  
|[\_com\_error](../cpp/com-error-class.md)|定义在大多数失败中 [\_com\_raise\_error](../cpp/com-raise-error.md) 引发的错误对象。|  
|[\_com\_ptr\_t](../cpp/com-ptr-t-class.md)|封装 COM 接口指针，并且自动执行对 `AddRef`、**Release** 和 `QueryInterface` 的必需调用。|  
|[\_variant\_t](../cpp/variant-t-class.md)|包装 **VARIANT** 类型，以提供有用的运算符和方法。|  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器 COM 支持](../cpp/compiler-com-support.md)   
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)