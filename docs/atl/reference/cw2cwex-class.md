---
title: "CW2CWEX 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATL::CW2CWEX
- ATL.CW2CWEX
- ATL.CW2CWEX<t_nBufferLength>
- ATL::CW2CWEX<t_nBufferLength>
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: a85b67a58553dada36f4472ea0683e18bc775493
ms.lasthandoff: 02/24/2017

---
# <a name="cw2cwex-class"></a>CW2CWEX 类
此类由字符串转换宏`CW2CTEX`和`CT2CWEX`，和 typedef `CW2W`。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<int t_nBufferLength = 128>  
class CW2CWEX
```  
  
#### <a name="parameters"></a>参数  
 `t_nBufferLength`  
 在转换过程中所用的缓冲区的大小。 默认长度为 128 个字节。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CW2CWEX::CW2CWEX](#cw2cwex)|构造函数。|  
|[CW2CWEX:: ~ CW2CWEX](#dtor)|析构函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CW2CWEX::operator LPCWSTR](#operator_lpcwstr)|转换运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CW2CWEX::m_psz](#m_psz)|将源字符串存储的数据成员。|  
  
## <a name="remarks"></a>备注  
 除非需要额外功能，则使用`CW2CTEX`， `CT2CWEX`，或`CW2W`在代码中。  
  
 此类是在循环中安全使用，不会溢出堆栈。 默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。  
  
 下列宏基于此类︰  
  
- `CW2CTEX`  
  
- `CT2CWEX`  
  
 下面的 typedef 基于此类︰  
  
- `CW2W`  
  
 这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)。  
  
## <a name="example"></a>示例  
 请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)有关使用这些字符串转换宏的示例。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlconv.h  
  
##  <a name="a-namecw2cwexa--cw2cwexcw2cwex"></a><a name="cw2cwex"></a>CW2CWEX::CW2CWEX  
 构造函数。  
  
```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 要转换的文本字符串。  
  
 `nCodePage`  
 代码页中。 不使用此类中。  
  
### <a name="remarks"></a>备注  
 分配在转换过程中所用的缓冲区。  
  
##  <a name="a-namedtora--cw2cwexcw2cwex"></a><a name="dtor"></a>CW2CWEX:: ~ CW2CWEX  
 析构函数。  
  
```
~CW2CWEX() throw();
```  
  
### <a name="remarks"></a>备注  
 释放分配的缓冲区。  
  
##  <a name="a-namempsza--cw2cwexmpsz"></a><a name="m_psz"></a>CW2CWEX::m_psz  
 将源字符串存储的数据成员。  
  
```
LPCWSTR m_psz;
```  
  
##  <a name="a-nameoperatorlpcwstra--cw2cwexoperator-lpcwstr"></a><a name="operator_lpcwstr"></a>CW2CWEX::operator LPCWSTR  
 转换运算符。  
  
```  
operator LPCWSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回将文本字符串作为类型**LPCWSTR。**  
  
## <a name="see-also"></a>另请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [类概述](../../atl/atl-class-overview.md)

