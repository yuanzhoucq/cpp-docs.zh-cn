---
title: "_bstr_t::_bstr_t |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::_bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t method
- _bstr_t class
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
caps.latest.revision: 10
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
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: ccf087d3b48a00de00eab7016563f59d4ad2d974
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="bstrtbstrt"></a>_bstr_t::_bstr_t
**Microsoft 专用**  
  
 构造 `_bstr_t` 对象。  
  
## <a name="syntax"></a>语法  
  
```  
_bstr_t( ) throw( );   
_bstr_t(  
   const _bstr_t& s1   
) throw( );  
_bstr_t(  
   const char* s2   
);  
_bstr_t(  
   const wchar_t* s3   
);  
_bstr_t(  
   const _variant_t& var   
);  
_bstr_t(  
   BSTR bstr,  
   bool fCopy   
);  
```  
  
#### <a name="parameters"></a>参数  
 `s1`  
 要复制的 `_bstr_t` 对象。  
  
 `s2`  
 多字节字符串。  
  
 `s3`  
 Unicode 字符串  
  
 `var`  
 A [_variant_t](../cpp/variant-t-class.md)对象。  
  
 `bstr`  
 一个现有的 `BSTR` 对象。  
  
 `fCopy`  
 如果为 `false`，则通过调用 `bstr` 来将 `SysAllocString` 参数附加到新的对象，而不创建副本。  
  
## <a name="remarks"></a>备注  
 下表描述 `_bstr_t` 构造函数。  
  
|构造函数|描述|  
|-----------------|-----------------|  
|`_bstr_t( )`|构造默认`_bstr_t`对象，它封装 null`BSTR`对象。|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|构造一个 `_bstr_t` 对象作为另一个对象的副本。<br /><br /> 这是*浅表*副本，可增加封装的引用计数`BSTR`而不是创建一个新的对象。|  
|`_bstr_t( char*`  `s2`  `)`|通过调用 `_bstr_t` 来创建一个新的 `SysAllocString` 对象并封装该对象，从而构造一个 `BSTR` 对象。<br /><br /> 此构造函数首先执行多字节到 Unicode 的转换。|  
|`_bstr_t( wchar_t*`  `s3`  `)`|通过调用 `_bstr_t` 来创建一个新的 `SysAllocString` 对象并封装该对象，从而构造一个 `BSTR` 对象。|  
|`_bstr_t( _variant_t&`  `var`  `)`|通过先从封装的 VARIANT 对象检查 `_bstr_t` 对象来从 `_variant_t` 对象构造一个 `BSTR` 对象。|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|从现有 `_bstr_t` 构造一个 `BSTR` 对象（与 `wchar_t*` 字符串相对）。 如果 `fCopy` 为 false，则将提供的 `BSTR` 附加到新对象，而不使用 `SysAllocString` 创建新的副本。<br /><br /> 此构造函数由类型库标头中的包装器函数用于封装接口方法所返回的 `BSTR` 并获取其所有权。|  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [_bstr_t 类](../cpp/bstr-t-class.md)   
 [_variant_t 类](../cpp/variant-t-class.md)
