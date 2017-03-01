---
title: "CW2WEX 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2WEX
- ATL.CW2WEX<t_nBufferLength>
- ATL::CW2WEX
- ATL.CW2WEX
- ATL::CW2WEX<t_nBufferLength>
dev_langs:
- C++
helpviewer_keywords:
- CW2WEX class
ms.assetid: 46262e56-e0d2-41fe-855b-0b67ecc8fcd7
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 9382f8404c1469b3f847500f35ab26499b6579bc
ms.lasthandoff: 02/24/2017

---
# <a name="cw2wex-class"></a>CW2WEX 类
此类由字符串转换宏`CW2TEX`和`CT2WEX`，和 typedef `CW2W`。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <int t_nBufferLength = 128>  
class CW2WEX
```  
  
#### <a name="parameters"></a>参数  
 `t_nBufferLength`  
 在转换过程中所用的缓冲区的大小。 默认长度为 128 个字节。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CW2WEX::CW2WEX](#cw2wex)|构造函数。|  
|[CW2WEX:: ~ CW2WEX](#dtor)|析构函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CW2WEX::operator LPWSTR](#operator_lpwstr)|转换运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CW2WEX::m_psz](#m_psz)|将源字符串存储的数据成员。|  
|[CW2WEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用来存储转换后的字符串。|  
  
## <a name="remarks"></a>备注  
 除非需要额外功能，则使用`CW2TEX`， `CT2WEX`，或`CW2W`在代码中。  
  
 此类包含固定大小的静态缓冲区用于存储转换的结果。 如果结果过大，无法放入静态缓冲区，则该类将使用 `malloc` 分配内存，并在对象超出范围时释放内存。 这样可确保，像文本转换宏可在以前版本的 ATL，它是此类是在循环中安全使用，并且它不会溢出堆栈。  
  
 如果该类尝试分配内存堆和无法正常工作，它将调用`AtlThrow`用参数**E_OUTOFMEMORY**。  
  
 默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。  
  
 下列宏基于此类︰  
  
- `CW2TEX`  
  
- `CT2WEX`  
  
 下面的 typedef 基于此类︰  
  
- `CW2W`  
  
 这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)。  
  
## <a name="example"></a>示例  
 请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)有关使用这些字符串转换宏的示例。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlconv.h  
  
##  <a name="a-namecw2wexa--cw2wexcw2wex"></a><a name="cw2wex"></a>CW2WEX::CW2WEX  
 构造函数。  
  
```
CW2WEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2WEX( LPCWSTR  psz) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 要转换的文本字符串。  
  
 `nCodePage`  
 代码页中。 不使用此类中。  
  
### <a name="remarks"></a>备注  
 创建转换所需的缓冲区。  
  
##  <a name="a-namedtora--cw2wexcw2wex"></a><a name="dtor"></a>CW2WEX:: ~ CW2WEX  
 析构函数...  
  
```
~CW2WEX() throw();
```  
  
### <a name="remarks"></a>备注  
 释放分配的缓冲区。  
  
##  <a name="a-namempsza--cw2wexmpsz"></a><a name="m_psz"></a>CW2WEX::m_psz  
 将源字符串存储的数据成员。  
  
```
LPWSTR m_psz;
```  
  
##  <a name="a-namemszbuffera--cw2wexmszbuffer"></a><a name="m_szbuffer"></a>CW2WEX::m_szBuffer  
 静态缓冲区，用来存储转换后的字符串。  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="a-nameoperatorlpwstra--cw2wexoperator-lpwstr"></a><a name="operator_lpwstr"></a>CW2WEX::operator LPWSTR  
 强制转换运算符。  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回将文本字符串作为类型`LPWSTR`。  
  
## <a name="see-also"></a>另请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [类概述](../../atl/atl-class-overview.md)

