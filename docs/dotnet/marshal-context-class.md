---
title: "marshal_context 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "marshal_context"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "marshal_context 类 [C++]"
ms.assetid: 241b0cf6-4ca4-4812-aaee-d671c11dc034
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# marshal_context 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类将在本机和托管环境之间封送数据。  
  
## 语法  
  
```  
class marshal_context  
```  
  
## 备注  
 对于需要上下文的转换数据，使用 `marshal_context` 类。  有关转换需要上下文并且必须包括封送处理文件的更多信息，请参阅 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md) 。  当使用一上下文时，封送处理的结果有效，直到销毁 `marshal_context` 对象。  若要保留结果，必须复制数据。  
  
 同一个 `marshal_context` 可以用于多个数据转换。  该行为重用上下文进行不影响从之前封装处理调用的结果。  
  
## 要求  
 **Header file:** \<msclr\\marshal.h\>, \<msclr\\marshal\_windows.h\>, \<msclr\\marshal\_cppstd.h\>, 或 \<msclr\\marshal\_atl.h\>  
  
 **Namespace:** msclr::interop  
  
## 请参阅  
 [C\+\+ 中的封送处理概述](../dotnet/overview-of-marshaling-in-cpp.md)   
 [marshal\_as](../dotnet/marshal-as.md)