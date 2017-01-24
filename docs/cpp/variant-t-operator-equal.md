---
title: "_variant_t::operator = | Microsoft Docs"
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
  - "_variant_t.operator="
  - "_variant_t::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= 运算符, 具有特定的 Visual C++ 对象"
  - "运算符 =, 变量"
  - "operator=, 变量"
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::operator =
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
## 语法  
  
```  
  
      _variant_t& operator=(  
   const VARIANT& varSrc   
);  
  
_variant_t& operator=(  
   const VARIANT* pVarSrc   
);  
  
_variant_t& operator=(  
   const _variant_t& var_t_Src   
);  
  
_variant_t& operator=(  
   short sSrc   
);  
  
_variant_t& operator=(  
   long lSrc   
);  
  
_variant_t& operator=(  
   float fltSrc   
);  
  
_variant_t& operator=(  
   double dblSrc   
);  
  
_variant_t& operator=(  
   const CY& cySrc   
);  
  
_variant_t& operator=(  
   const _bstr_t& bstrSrc   
);  
  
_variant_t& operator=(  
   const wchar_t* wstrSrc   
);  
  
_variant_t& operator=(  
   const char* strSrc   
);  
  
_variant_t& operator=(  
   IDispatch* pDispSrc   
);  
  
_variant_t& operator=(  
   bool bSrc   
);  
  
_variant_t& operator=(  
   IUnknown* pSrc   
);  
  
_variant_t& operator=(  
   const DECIMAL& decSrc   
);  
  
_variant_t& operator=(  
   BYTE bSrc   
);  
  
_variant_t& operator=(  
   char cSrc  
);  
  
_variant_t& operator=(  
   unsigned short usSrc  
);  
  
_variant_t& operator=(  
   unsigned long ulSrc  
);  
  
_variant_t& operator=(  
   int iSrc  
);  
  
_variant_t& operator=(  
   unsigned int uiSrc  
);  
  
_variant_t& operator=(  
   __int64 i8Src  
);  
  
_variant_t& operator=(  
   unsigned __int64 ui8Src  
);  
```  
  
## 备注  
 此运算符将向 `_variant_t` 对象赋予新值：  
  
-   **operator\=\(**  *varSrc*  **\)** 将现有 **VARIANT** 赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *pVarSrc*  **\)** 将现有 **VARIANT** 赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *var\_t\_Src*  **\)** 将现有 `_variant_t` 对象赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *sSrc*  **\)** 将 **short** 整数值赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  `lSrc`  **\)** 将 **long** 整数值赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *fltSrc*  **\)** 将 **float** 数字值赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *dblSrc*  **\)** 将 **double** 数字值赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *cySrc*  **\)** 将 **CY** 对象赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *bstrSrc*  **\)** 将 `BSTR` 对象赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *wstrSrc*  **\)** 将 Unicode 字符串赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  `strSrc`  **\)** 将多字节字符串赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  `bSrc` **\)** 将 `bool` 值赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *pDispSrc*  **\)** 将 **VT\_DISPATCH** 对象赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *pIUnknownSrc*  **\)** 将 **VT\_UNKNOWN** 对象赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  *decSrc*  **\)** 将 **DECIMAL** 值赋给 `_variant_t` 对象。  
  
-   **operator\=\(**  `bSrc` **\)** 将 **BYTE** 值赋给 `_variant_t` 对象。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)