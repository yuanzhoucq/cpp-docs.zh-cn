---
title: "CA2AEX 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 979e06cbb4386f61f6490342f16d48739be55e95
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="ca2aex-class"></a>CA2AEX 类
此类由字符串转换宏`CA2TEX`和`CT2AEX`，和 typedef **CA2A**。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <int t_nBufferLength = 128>
class CA2AEX
```  
  
#### <a name="parameters"></a>参数  
 `t_nBufferLength`  
 在转换过程中使用的缓冲区大小。 默认长度为 128 个字节。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CA2AEX::CA2AEX](#ca2aex)|构造函数。|  
|[CA2AEX:: ~ CA2AEX](#dtor)|析构函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CA2AEX::operator LPSTR](#operator_lpstr)|转换运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CA2AEX::m_psz](#m_psz)|将源字符串存储数据成员。|  
|[CA2AEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用于存储已转换的字符串。|  
  
## <a name="remarks"></a>备注  
 除非需要额外功能，则使用`CA2TEX`， `CT2AEX`，或**CA2A**你自己的代码中。  
  
 此类包含固定大小静态缓冲区，用于存储转换的结果。 如果结果过大，无法放入静态缓冲区，则该类将使用 `malloc` 分配内存，并在对象超出范围时释放内存。 这样可确保，像文本转换宏可用在以前版本的 ATL，此类可以安全地在循环中使用和它不会溢出堆栈。  
  
 如果类尝试分配内存堆和失败，它将调用`AtlThrow`用参数**E_OUTOFMEMORY**。  
  
 默认情况下，情况下，ATL 转换类和宏使用当前线程的 ANSI 代码页进行转换。  
  
 在此类基于以下宏︰  
  
- `CA2TEX`  
  
- `CT2AEX`  
  
 以下 typedef 取决于此类︰  
  
- **CA2A**  
  
 这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。  
  
## <a name="example"></a>示例  
 请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)有关使用这些字符串转换宏的示例。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlconv.h  
  
##  <a name="ca2aex"></a>CA2AEX::CA2AEX  
 构造函数。  
  
```
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 要转换的文本字符串。  
  
 `nCodePage`  
 在此类中未使用。  
  
### <a name="remarks"></a>备注  
 创建转换所需的缓冲区。  
  
##  <a name="dtor"></a>CA2AEX:: ~ CA2AEX  
 析构函数。  
  
```
~CA2AEX() throw();
```  
  
### <a name="remarks"></a>备注  
 释放已分配的缓冲区。  
  
##  <a name="m_psz"></a>CA2AEX::m_psz  
 将源字符串存储数据成员。  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CA2AEX::m_szBuffer  
 静态缓冲区，用于存储已转换的字符串。  
  
```
char m_szBuffer[ t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>CA2AEX::operator LPSTR  
 转换运算符。  
  
```
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回文本字符串作为类型**LPSTR**。  
  
## <a name="see-also"></a>另请参阅  
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [类概述](../../atl/atl-class-overview.md)
