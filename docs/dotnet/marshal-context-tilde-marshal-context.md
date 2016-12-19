---
title: "marshal_context::~marshal_context | Microsoft Docs"
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
  - "marshal_context::~marshal_context"
  - "msclr.interop.marshal_context.~marshal_context"
  - "marshal_context.~marshal_context"
  - "msclr::interop::marshal_context::~marshal_context"
  - "~marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context 类 [C++], 操作"
ms.assetid: 34c41b38-4c33-4f61-b74e-831ac46b4ab5
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# marshal_context::~marshal_context
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

销毁 `marshal_context` 对象。  
  
## 语法  
  
```  
~marshal_context();  
```  
  
## 备注  
 这些数据转换需要上下文。  参见转换需要上下文，并且的更多信息封送处理文件在应用程序必须包含的有关 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)。  
  
 删除 `marshal_context` 对象将导致该上下文转换的数据。  如果要保留数据，`marshal_context` 对象销毁后，则必须手动将数据复制到中依然存在的变量。  
  
## 要求  
 **Header file:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, 或 \<msclr\\marshal\_atl.h\>  
  
 **Namespace:** msclr::interop  
  
## 请参阅  
 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)   
 [marshal\_context 类](../dotnet/marshal-context-class.md)