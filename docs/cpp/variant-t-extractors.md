---
title: "_variant_t 提取器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t.operatordouble
- operatorlong
- _variant_t::operator_bstr_t
- operatordouble
- _variant_t.operatorCY
- operatorCY
- _variant_t::operatorCY
- _variant_t::operatordouble
- operatorfloat
- operatorBYTE
- _variant_t.operatorDECIMAL
- _variant_t::operatorlong
- operatorIDispatch
- _variant_t.operatorBYTE
- operatorDECIMAL
- _variant_t.operator_bstr_t
- _variant_t::operatorDECIMAL
- _variant_t.operatorIUnknown
- _variant_t.operatorlong
- _variant_t::operatorIDispatch
- _variant_t::operatorIUnknown
- operatorIUnknown
- _variant_t.operatorbool
- _variant_t::operatorBYTE
- _variant_t.operatorfloat
- operator_bstr_t
- _variant_t::operatorbool
- operatorshort
- _variant_t::operatorshort
- _variant_t::operatorfloat
- _variant_t.operatorIDispatch
- _variant_t.operatorshort
dev_langs:
- C++
helpviewer_keywords:
- extractors, _variant_t class
- operator CY
- operator IDispatch
- operator SHORT
- operator double
- operator long
- operator _bstr_t
- operator DECIMAL
- operator float
- operator bool
- operator BYTE
- operator IUnknown
ms.assetid: 33c1782f-045a-4673-9619-1d750efc83a9
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: f460497071445cff87308fa9bf6e0d43c6f13a3e
ms.openlocfilehash: 9ec02d82529a6772e079305c34c5f43ee163a2f7
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="variantt-extractors"></a>_variant_t 提取器
**Microsoft 专用**  
  
 从封装中提取数据**VARIANT**对象。  
  
## <a name="syntax"></a>语法  
  
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
  
## <a name="remarks"></a>备注  
 从封装中提取原始数据**VARIANT**。 如果**VARIANT**尚不正确的类型， **VariantChangeType**用于尝试进行转换，并在失败时生成错误：  
  
-   **operator short （)**提取**短**整数值。  
  
-   **operator long （)**提取**长**整数值。  
  
-   **operator float （)**提取**float**数字值。  
  
-   **operator double （)**提取**double**整数值。  
  
-   **operator CY （)**提取**CY**对象。  
  
-   **operator bool （)**提取`bool`值。  
  
-   **operator DECIMAL （)**提取**十进制**值。  
  
-   **operator BYTE （)**提取**字节**值。  
  
-   **operator _bstr_t （)**提取字符串，封装在`_bstr_t`对象。  
  
-   **运算符 IDispatch\*（)**从封装中提取调度接口指针**VARIANT**。 `AddRef`因此由您才能调用是否在生成的指针上调用**版本**来释放它。  
  
-   **运算符 IUnknown\*（)**提取从封装的 COM 接口指针**VARIANT**。 `AddRef`因此由您才能调用是否在生成的指针上调用**版本**来释放它。  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_variant_t 类](../cpp/variant-t-class.md)

