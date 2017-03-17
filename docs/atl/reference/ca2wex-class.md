---
title: "CA2WEX 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7c1029d0d9cb1abb1980f97c9541e2c1ce40b539
ms.lasthandoff: 02/24/2017

---
# <a name="ca2wex-class"></a>CA2WEX 类
此类由字符串转换宏`CA2TEX`， `CA2CTEX`， `CT2WEX`，和`CT2CWEX`，和 typedef **CA2W**。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>参数  
 `t_nBufferLength`  
 在转换过程中所用的缓冲区的大小。 默认长度为 128 个字节。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|构造函数。|  
|[CA2WEX:: ~ CA2WEX](#dtor)|析构函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|转换运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|将源字符串存储的数据成员。|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用来存储转换后的字符串。|  
  
## <a name="remarks"></a>备注  
 除非需要额外功能，则使用`CA2TEX`， `CA2CTEX`， `CT2WEX`， `CT2CWEX`，或**CA2W**在代码中。  
  
 此类包含固定大小的静态缓冲区用于存储转换的结果。 如果结果过大，无法放入静态缓冲区，则该类将使用 `malloc` 分配内存，并在对象超出范围时释放内存。 这样可确保，像文本转换宏可在以前版本的 ATL，它是此类是在循环中安全使用，并且它不会溢出堆栈。  
  
 如果该类尝试分配内存堆和无法正常工作，它将调用`AtlThrow`用参数**E_OUTOFMEMORY**。  
  
 默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。 如果您想要重写特定转换的该行为，作为类的构造函数的第二个参数指定的代码页。  
  
 下列宏基于此类︰  
  
- `CA2TEX`  
  
- `CA2CTEX`  
  
- `CT2WEX`  
  
- `CT2CWEX`  
  
 下面的 typedef 基于此类︰  
  
- **CA2W**  
  
 这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)。  
  
## <a name="example"></a>示例  
 请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)有关使用这些字符串转换宏的示例。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlconv.h  
  
##  <a name="ca2wex"></a>CA2WEX::CA2WEX  
 构造函数。  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 要转换的文本字符串。  
  
 `nCodePage`  
 用来执行转换的代码页。 请参阅对每个代码页参数讨论[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]函数[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)的更多详细信息。  
  
### <a name="remarks"></a>备注  
 分配在转换过程中所用的缓冲区。  
  
##  <a name="dtor"></a>CA2WEX:: ~ CA2WEX  
 析构函数。  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>备注  
 释放分配的缓冲区。  
  
##  <a name="m_psz"></a>CA2WEX::m_psz  
 将源字符串存储的数据成员。  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CA2WEX::m_szBuffer  
 静态缓冲区，用来存储转换后的字符串。  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>CA2WEX::operator LPWSTR  
 转换运算符。  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回将文本字符串作为类型**LPWSTR。**  
  
## <a name="see-also"></a>另请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [类概述](../../atl/atl-class-overview.md)

