---
title: "编译器 COM 支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe 编译器, COM 支持"
  - "COM, 编译器支持"
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器 COM 支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 Visual C\+\+ 编译器可以直接读取组件对象模型 \(COM\) 类型库并将内容转换为可包含在编译中的 C\+\+ 源代码。  提供了语言扩展来帮助在客户端上进行 COM 编程。  
  
 通过使用 [\#import 预处理器指令](../preprocessor/hash-import-directive-cpp.md)，编译器可以读取类型库并将其转换为将 COM 接口描述为类的 C\+\+ 头文件。  提供了一组 `#import` 特性来实现对生成的类型库头文件的内容的用户控制。  
  
 您可以使用 [\_\_declspec](../cpp/declspec.md) 扩展特性 [uuid](../cpp/uuid-cpp.md) 将全局唯一标识符 \(GUID\) 分配给 COM 对象。  关键字 [\_\_uuidof](../cpp/uuidof-operator.md) 可用于提取与 COM 对象关联的 GUID。  另一个 `__declspec` 特性（[属性](../cpp/property-cpp.md)）可用于为 COM 对象的数据成员指定 **get** 和 **set** 方法。  
  
 提供了一组 COM 支持全局函数和类来支持 **VARIANT** 和 `BSTR` 类型、实现智能指针以及封装 `_com_raise_error` 引发的错误对象：  
  
-   [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)  
  
-   [\_bstr\_t](../cpp/bstr-t-class.md)  
  
-   [\_com\_error](../cpp/com-error-class.md)  
  
-   [\_com\_ptr\_t](../cpp/com-ptr-t-class.md)  
  
-   [\_variant\_t](../cpp/variant-t-class.md)  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [编译器 COM 支持类](../cpp/compiler-com-support-classes.md)   
 [编译器 COM 全局函数](../cpp/compiler-com-global-functions.md)