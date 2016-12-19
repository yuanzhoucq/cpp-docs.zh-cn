---
title: "_bstr_t::_bstr_t | Microsoft Docs"
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
  - "_bstr_t::_bstr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_bstr_t 类"
  - "_bstr_t 方法"
  - "BSTR 对象"
ms.assetid: 116d994e-5a72-4351-afbe-866c80b4c165
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::_bstr_t
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 构造 `_bstr_t` 对象。  
  
## 语法  
  
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
  
#### 参数  
 `s1`  
 要复制的 `_bstr_t` 对象。  
  
 `s2`  
 多字节字符串。  
  
 `s3`  
 Unicode 字符串  
  
 `var`  
 [\_variant\_t](../cpp/variant-t-class.md) 对象。  
  
 `bstr`  
 一个现有的 `BSTR` 对象。  
  
 `fCopy`  
 如果为 `false`，则通过调用 `SysAllocString` 来将 `bstr` 参数附加到新的对象，而不创建副本。  
  
## 备注  
 下表描述 `_bstr_t` 构造函数。  
  
|构造函数|说明|  
|----------|--------|  
|`_bstr_t( )`|构造一个封装空 `BSTR` 对象的默认 `_bstr_t` 对象。|  
|`_bstr_t( _bstr_t&`  `s1`  `)`|构造一个 `_bstr_t` 对象作为另一个对象的副本。<br /><br /> 这是一个卷影副本，可增加封装的 `BSTR` 对象的引用计数而不是创建新的计数。|  
|`_bstr_t( char*`  `s2`  `)`|通过调用 `SysAllocString` 来创建一个新的 `BSTR` 对象并封装该对象，从而构造一个 `_bstr_t` 对象。<br /><br /> 此构造函数首先执行多字节到 Unicode 的转换。|  
|`_bstr_t( wchar_t*`  `s3`  `)`|通过调用 `SysAllocString` 来创建一个新的 `BSTR` 对象并封装该对象，从而构造一个 `_bstr_t` 对象。|  
|`_bstr_t( _variant_t&`  `var`  `)`|通过先从封装的 VARIANT 对象检查 `BSTR` 对象来从 `_variant_t` 对象构造一个 `_bstr_t` 对象。|  
|`_bstr_t( BSTR`  `bstr` `, bool`  `fCopy`  `)`|从现有 `BSTR` 构造一个 `_bstr_t` 对象（与 `wchar_t*` 字符串相对）。  如果 `fCopy` 为 false，则将提供的 `BSTR` 附加到新对象，而不使用 `SysAllocString` 创建新的副本。<br /><br /> 此构造函数由类型库标头中的包装器函数用于封装接口方法所返回的 `BSTR` 并获取其所有权。|  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [\_bstr\_t 类](../cpp/bstr-t-class.md)   
 [\_variant\_t 类](../cpp/variant-t-class.md)