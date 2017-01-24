---
title: "_com_ptr_t::GetActiveObject | Microsoft Docs"
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
  - "_com_ptr_t.GetActiveObject"
  - "_com_ptr_t::GetActiveObject"
  - "GetActiveObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetActiveObject 方法"
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::GetActiveObject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 根据 **CLSID** 或 **ProgID** 附加到一个对象的现有实例。  
  
## 语法  
  
```  
  
      HRESULT GetActiveObject(  
   const CLSID& rclsid   
) throw( );  
HRESULT GetActiveObject(  
   LPCWSTR clsidString   
) throw( );  
HRESULT GetActiveObject(  
   LPCSTR clsidStringA   
) throw( );  
```  
  
#### 参数  
 `rclsid`  
 对象的 **CLSID**。  
  
 `clsidString`  
 包含 **CLSID**（以“**{**”开头）或 **ProgID** 的 Unicode 字符串。  
  
 `clsidStringA`  
 使用 ANSI 代码页并包括 **CLSID**（以“**{**”开头）或 **ProgID** 的多字节字符串。  
  
## 备注  
 这些成员函数调用 `GetActiveObject` 来检索指向已向 OLE 注册的正在运行对象的指针，然后查询此智能指针的接口类型。  生成的指针随后将封装在此 `_com_ptr_t` 对象内。  调用 **Release** 以减少前面封装的指针的引用计数。  此例程返回 `HRESULT` 以指示成功或失败。  
  
-   **GetActiveObject\(**  `rclsid`  **\)** 根据 **CLSID** 附加到一个对象的现有实例。  
  
-   **GetActiveObject\(**  `clsidString`  **\)** 根据包含 **CLSID**（以“**{**”开头）或 **ProgID** 的 Unicode 字符串附加到一个对象的现有实例。  
  
-   **GetActiveObject\(**  `clsidStringA`  **\)** 根据包含 **CLSID**（以“**{**”开头）或 **ProgID** 的多字节字符串附加到一个对象的现有实例。  调用 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，这假定字符串是在 ANSI 代码页中而不是 OEM 代码页中。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)