---
title: "uuid (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "uuid"
  - "uuid_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], uuid"
  - "uuid __declspec 关键字"
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uuid (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 编译器将 GUID 附加到使用 `uuid` 特性声明或定义的（仅完整的 COM 对象定义）类或结构中。  
  
## 语法  
  
```  
  
__declspec( uuid("  
ComObjectGUID  
") ) declarator  
```  
  
## 备注  
 `uuid` 特性采用字符串作为其参数。  此字符串采用带有或不带 **{ }** 分隔符的普通注册表格式命名 GUID。  例如：  
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 此特性可应用于重新声明。  这允许系统标头提供接口定义（如 **IUnknown**），并允许其他标头（如 COMDEF.H）中的重新声明提供 GUID。  
  
 可以应用关键字 [\_\_uuidof](../cpp/uuidof-operator.md) 来检索附加到用户定义的类型的常量 GUID。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)