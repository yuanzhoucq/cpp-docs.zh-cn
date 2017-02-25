---
title: "_variant_t 提取器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_variant_t.operatordouble"
  - "operatorlong"
  - "_variant_t::operator_bstr_t"
  - "operatordouble"
  - "_variant_t.operatorCY"
  - "operatorCY"
  - "_variant_t::operatorCY"
  - "_variant_t::operatordouble"
  - "operatorfloat"
  - "operatorBYTE"
  - "_variant_t.operatorDECIMAL"
  - "_variant_t::operatorlong"
  - "operatorIDispatch"
  - "_variant_t.operatorBYTE"
  - "operatorDECIMAL"
  - "_variant_t.operator_bstr_t"
  - "_variant_t::operatorDECIMAL"
  - "_variant_t.operatorIUnknown"
  - "_variant_t.operatorlong"
  - "_variant_t::operatorIDispatch"
  - "_variant_t::operatorIUnknown"
  - "operatorIUnknown"
  - "_variant_t.operatorbool"
  - "_variant_t::operatorBYTE"
  - "_variant_t.operatorfloat"
  - "operator_bstr_t"
  - "_variant_t::operatorbool"
  - "operatorshort"
  - "_variant_t::operatorshort"
  - "_variant_t::operatorfloat"
  - "_variant_t.operatorIDispatch"
  - "_variant_t.operatorshort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "提取器, _variant_t 类"
  - "运算符 _bstr_t"
  - "运算符 bool"
  - "运算符 BYTE"
  - "运算符 CY"
  - "运算符 DECIMAL"
  - "运算符 double"
  - "运算符 float"
  - "运算符 IDispatch"
  - "运算符 IUnknown"
  - "运算符 long"
  - "运算符 SHORT"
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _variant_t 提取器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 从封装的 **VARIANT** 对象中提取数据。  
  
## 语法  
  
```  
  
      operator short( ) const;   
operator long( ) const;   
operator float( ) const;   
operator double( ) const;   
operator CY( ) const;   
operator _bstr_t( ) const;   
operator IDispatch*( ) const;   
operator bool( ) const;   
operator IUnknown*( ) const;   
operator DECIMAL( ) const;   
operator BYTE( ) const;  
operator VARIANT() const throw();  
operator char() const;  
operator unsigned short() const;  
operator unsigned long() const;  
operator int() const;  
operator unsigned int() const;  
operator __int64() const;  
operator unsigned __int64() const;  
```  
  
## 备注  
 从封装的 **VARIANT** 中提取原始数据。  如果 **VARIANT** 还不是正确的类型，则使用 **VariantChangeType** 尝试转换，并在失败时生成错误：  
  
-   **operator short\( \)** 提取 **short** 整数值。  
  
-   **operator long\( \)** 提取 **long** 整数值。  
  
-   **operator float\( \)** 提取 **float** 数字值。  
  
-   **operator double\( \)** 提取 **double** 整数值。  
  
-   **operator CY\( \)** 提取 **CY** 对象。  
  
-   **operator bool\( \)** 提取 `bool` 值。  
  
-   **operator DECIMAL\( \)** 提取 **DECIMAL** 值。  
  
-   **operator BYTE\( \)** 提取 **BYTE** 值。  
  
-   **operator \_bstr\_t\( \)** 提取封装在 `_bstr_t` 对象中的字符串。  
  
-   **operator IDispatch\*\( \)** 从封装的 **VARIANT** 提取调度接口指针。  将对生成的指针调用 `AddRef`，因此由您决定是否调用 **Release** 来释放它。  
  
-   **operator IUnknown\*\( \)** 从封装的 **VARIANT** 提取 COM 接口指针。  将对生成的指针调用 `AddRef`，因此由您决定是否调用 **Release** 来释放它。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_variant\_t 类](../cpp/variant-t-class.md)