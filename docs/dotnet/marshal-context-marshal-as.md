---
title: "marshal_context::marshal_as | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshal_context::marshal_as"
  - "marshal_context.marshal_as"
  - "msclr.interop.marshal_context.marshal_as"
  - "msclr::interop::marshal_context::marshal_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context 类 [C++], 操作"
ms.assetid: 24a1afee-51c0-497c-948c-f77fe43635c8
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# marshal_context::marshal_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对特定数据对象执行封送，将其在托管和本机数据类型之间转换。  
  
## 语法  
  
```  
To_Type marshal_as<To_Type>(  
   From_Type input   
);  
```  
  
#### 参数  
 \[in\] `input`  
 要编组到`To_Type`变量的值。  
  
## 返回值  
 类型`To_Type` 的一个变量，它是`input`的转换值。  
  
## 备注  
 此函数针对特定数据对象进行封送处理。  使用此函数仅有 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)表中指示的转换。  
  
 如果您尝试封送处理对数据类型是不支持的，在编译时会`marshal_as` 产生错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 。  读取消息提供了此错误有关更多信息。  产生错误`C4996`的可能不仅仅是弃用的函数。  会生成此错误的两种情况是不支持尝试封送对数据类型并对需要上下文的转换尝试使用 `marshal_as`。  
  
 封送处理库包括多个标头文件。  所有转换只需要一个文件，但是，如果您为其他转换需要可以包含其他文件。  `Marshaling Overview in C++` 中的表指示对于每次转换封送文件应该被包含。  
  
## 示例  
 此示例创建一封送的上下文从 `System::String` 到 `const char *` 变量的类型。  转换数据在删除上下文的行之后将是无效的。  
  
```  
// marshal_context_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   marshal_context^ context = gcnew marshal_context();  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = context->marshal_as<const char*>( message );  
   delete context;  
   return 0;  
}  
```  
  
## 要求  
 **Header file:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, 或 \<msclr\\marshal\_atl.h\>  
  
 **Namespace:** msclr::interop  
  
## 请参阅  
 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context 类](../dotnet/marshal-context-class.md)