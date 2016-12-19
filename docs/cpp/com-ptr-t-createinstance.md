---
title: "_com_ptr_t::CreateInstance | Microsoft Docs"
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
  - "_com_ptr_t::CreateInstance"
  - "_com_ptr_t.CreateInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInstance 方法"
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::CreateInstance
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 创建一个给定了 **CLSID** 或 **ProgID** 的对象的新实例。  
  
## 语法  
  
```  
  
      HRESULT CreateInstance(  
   const CLSID& rclsid,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCWSTR clsidString,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
HRESULT CreateInstance(  
   LPCSTR clsidStringA,  
   IUnknown* pOuter=NULL,  
   DWORD dwClsContext = CLSCTX_ALL   
) throw( );  
```  
  
#### 参数  
 `rclsid`  
 对象的 **CLSID**。  
  
 `clsidString`  
 包含 **CLSID**（以“**{**”开头）或 **ProgID** 的 Unicode 字符串。  
  
 `clsidStringA`  
 使用 ANSI 代码页并包括 **CLSID**（以“**{**”开头）或 **ProgID** 的多字节字符串。  
  
 `dwClsContext`  
 运行可执行代码的上下文。  
  
 `pOuter`  
 [聚合](../atl/aggregation.md)未知的外部对象。  
  
## 备注  
 这些成员函数调用 `CoCreateInstance` 来创建新的 COM 对象，然后查询此智能指针的接口类型。  生成的指针随后将封装在此 `_com_ptr_t` 对象内。  调用 **Release** 以减少前面封装的指针的引用计数。  此例程返回 `HRESULT` 以指示成功或失败。  
  
-   **CreateInstance\(**  `rclsid` **,**  `dwClsContext`  **\)** 创建一个给定了 **CLSID** 的对象的新运行实例。  
  
-   **CreateInstance\(**  `clsidString` **,**  `dwClsContext`  **\)** 创建给定了包含 **CLSID**（以“**{**”开头）或 **ProgID** 的 Unicode 字符串的对象的新运行实例。  
  
-   **CreateInstance\(**  `clsidStringA` **,**  `dwClsContext`  **\)** 创建给定了包含 **CLSID**（以“**{**”开头）或 **ProgID** 的多字节字符串的对象的新运行实例。  调用 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)，这假定字符串是在 ANSI 代码页中而不是 OEM 代码页中。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)