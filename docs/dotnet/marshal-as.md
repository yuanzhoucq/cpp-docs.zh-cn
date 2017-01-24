---
title: "marshal_as | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshal_as"
  - "msclr.interop.marshal_as"
  - "msclr::interop::marshal_as"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_as 模板 [C++]"
ms.assetid: 2ed717da-2b11-41e5-981d-47d251771989
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_as
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此方法将在本机和托管环境之间封送数据。  
  
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
 此方法是一个简化的方式将本机之间的数据和托管类型。  要确定哪些是支持的数据类型，请参见[C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。  这些数据转换需要上下文。  可以使用 [marshal\_context 类](../dotnet/marshal-context-class.md)传唤那些数据类型。  
  
 如果您尝试封送处理对数据类型是不支持的，在编译时会`marshal_as` 产生错误[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md) 。  读取消息提供了此错误有关更多信息。  产生错误`C4996`的可能不仅仅是弃用的函数。  此示例尝试封送的数据类型匹配不受支持。  
  
 封送处理库包括多个标头文件。  所有转换只需要一个文件，但是，如果您为其他转换需要可以包含其他文件。  要查看哪些转换与文件相关联，在该表中寻找`Marshaling Overview`。  无论你做什么，命名空间要求始终是有效的。  
  
## 示例  
 例子封送一个从`const char*` 到 `System::String`的变量类型。  
  
```  
// marshal_as_test.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   const char* message = "Test String to Marshal";  
   String^ result;  
   result = marshal_as<String^>( message );  
   return 0;  
}  
```  
  
## 要求  
 **Header file:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, 或 \<msclr\\marshal\_atl.h\>  
  
 **Namespace:** msclr::interop  
  
## 请参阅  
 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_context 类](../dotnet/marshal-context-class.md)