---
title: "marshal_context::marshal_context | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::interop::marshal_context::marshal_context"
  - "marshal_context::marshal_context"
  - "msclr.interop.marshal_context.marshal_context"
  - "marshal_context.marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context 类 [C++], 操作"
ms.assetid: 5f08c895-60b0-4f72-97ff-7ae37c68e853
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# marshal_context::marshal_context
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

构造 `marshal_context` 对象为在托管和本机数据类型之间进行数据转换使用。  
  
## 语法  
  
```  
marshal_context();  
```  
  
## 备注  
 这些数据转换需要上下文。  参见转换需要上下文，并且的更多信息封送处理文件在应用程序必须包含的有关 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
## 示例  
 请参见 [marshal\_context::marshal\_as](../dotnet/marshal-context-marshal-as.md)中的示例。  
  
## 要求  
 **Header file:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, 或 \<msclr\\marshal\_atl.h\>  
  
 **Namespace:** msclr::interop  
  
## 请参阅  
 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context 类](../dotnet/marshal-context-class.md)