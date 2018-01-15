---
title: "CW2AEX 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs: C++
helpviewer_keywords: CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d135797ff6902a9a63e89a692a25919b08b47f6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cw2aex-class"></a>CW2AEX 类
此类由字符串转换宏`CT2AEX`， `CW2TEX`， `CW2CTEX`，和`CT2CAEX`，和 typedef **CW2A**。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<int t_nBufferLength = 128>  
class CW2AEX
```  
  
#### <a name="parameters"></a>参数  
 `t_nBufferLength`  
 在转换过程中使用的缓冲区大小。 默认长度为 128 个字节。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CW2AEX::CW2AEX](#cw2aex)|构造函数。|  
|[CW2AEX:: ~ CW2AEX](#dtor)|析构函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CW2AEX::operator LPSTR](#operator_lpstr)|转换运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CW2AEX::m_psz](#m_psz)|将源字符串存储数据成员。|  
|[CW2AEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用于存储已转换的字符串。|  
  
## <a name="remarks"></a>备注  
 除非需要额外功能，则使用`CT2AEX`， `CW2TEX`， `CW2CTEX`， `CT2CAEX`，或**CW2A**在代码中。  
  
 此类包含固定大小静态缓冲区，用于存储转换的结果。 如果结果过大，无法放入静态缓冲区，则该类将使用 `malloc` 分配内存，并在对象超出范围时释放内存。 这样可确保，像文本转换宏可用在以前版本的 ATL，此类可以安全地在循环中使用和它不会溢出堆栈。  
  
 如果类尝试分配内存堆和失败，它将调用`AtlThrow`用参数**E_OUTOFMEMORY**。  
  
 默认情况下，情况下，ATL 转换类和宏使用当前线程的 ANSI 代码页进行转换。 如果你想要重写特定转换的该行为，请将代码页指定为类的构造函数的第二个参数。  
  
 在此类基于以下宏：  
  
- `CT2AEX`  
  
- `CW2TEX`  
  
- `CW2CTEX`  
  
- `CT2CAEX`  
  
 以下 typedef 基于此类：  
  
- **CW2A**  
  
 这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。  
  
## <a name="example"></a>示例  
 请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)有关使用这些字符串转换宏的示例。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlconv.h  
  
##  <a name="cw2aex"></a>CW2AEX::CW2AEX  
 构造函数。  
  
```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2AEX(LPCWSTR psz) throw(...);
```  
  
### <a name="parameters"></a>参数  
 `psz`  
 要转换的文本字符串。  
  
 `nCodePage`  
 用来执行转换的代码页。 请参阅 Windows SDK 函数的代码页参数讨论[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)有关详细信息。  
  
### <a name="remarks"></a>备注  
 分配在转换过程中使用的缓冲区。  
  
##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX  
 析构函数。  
  
```
~CW2AEX() throw();
```  
  
### <a name="remarks"></a>备注  
 释放已分配的缓冲区。  
  
##  <a name="m_psz"></a>CW2AEX::m_psz  
 将源字符串存储数据成员。  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CW2AEX::m_szBuffer  
 静态缓冲区，用于存储已转换的字符串。  
  
```
char m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>CW2AEX::operator LPSTR  
 转换运算符。  
  
```  
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回文本字符串作为类型**LPSTR。**  
  
## <a name="see-also"></a>请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [类概述](../../atl/atl-class-overview.md)
