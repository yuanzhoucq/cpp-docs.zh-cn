---
title: "CW2CWEX 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a83f0fefed5e2393c303038346e3b84ec1a3d570
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cw2cwex-class"></a>CW2CWEX 类
此类由字符串转换宏`CW2CTEX`和`CT2CWEX`，和 typedef `CW2W`。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template<int t_nBufferLength = 128>  
class CW2CWEX
```  
  
#### <a name="parameters"></a>参数  
 `t_nBufferLength`  
 在转换过程中使用的缓冲区大小。 默认长度为 128 个字节。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
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
|[CW2CWEX::m_psz](#m_psz)|将源字符串存储数据成员。|  
  
## <a name="remarks"></a>备注  
 除非需要额外功能，则使用`CW2CTEX`， `CT2CWEX`，或`CW2W`在代码中。  
  
 此类可以安全地在循环中使用和不会溢出堆栈。 默认情况下，情况下，ATL 转换类和宏使用当前线程的 ANSI 代码页进行转换。  
  
 在此类基于以下宏：  
  
- `CW2CTEX`  
  
- `CT2CWEX`  
  
 以下 typedef 基于此类：  
  
- `CW2W`  
  
 这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)。  
  
## <a name="example"></a>示例  
 请参阅[ATL 和 MFC 字符串转换宏](string-conversion-macros.md)有关使用这些字符串转换宏的示例。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlconv.h  
  
##  <a name="cw2cwex"></a>CW2CWEX::CW2CWEX  
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
 分配在转换过程中使用的缓冲区。  
  
##  <a name="dtor"></a>CW2CWEX:: ~ CW2CWEX  
 析构函数。  
  
```
~CW2CWEX() throw();
```  
  
### <a name="remarks"></a>备注  
 释放已分配的缓冲区。  
  
##  <a name="m_psz"></a>CW2CWEX::m_psz  
 将源字符串存储数据成员。  
  
```
LPCWSTR m_psz;
```  
  
##  <a name="operator_lpcwstr"></a>CW2CWEX::operator LPCWSTR  
 转换运算符。  
  
```  
operator LPCWSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回文本字符串作为类型**LPCWSTR。**  
  
## <a name="see-also"></a>请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2AEX 类](../../atl/reference/cw2aex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [类概述](../../atl/atl-class-overview.md)
