---
title: "CW2AEX 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8bf433224396f54b81fb5310ec29dfed213c6855
ms.lasthandoff: 02/24/2017

---
# <a name="cw2aex-class"></a>CW2AEX 类
此类由字符串转换宏`CT2AEX`， `CW2TEX`， `CW2CTEX`，和`CT2CAEX`，和 typedef **CW2A**。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
template<int t_nBufferLength = 128>  
class CW2AEX
```  
  
#### <a name="parameters"></a>参数  
 `t_nBufferLength`  
 在转换过程中所用的缓冲区的大小。 默认长度为 128 个字节。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CW2AEX::CW2AEX](#cw2aex)|构造函数。|  
|[CW2AEX:: ~ CW2AEX](#dtor)|析构函数。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CW2AEX::operator LPSTR](#operator_lpstr)|转换运算符。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CW2AEX::m_psz](#m_psz)|将源字符串存储的数据成员。|  
|[CW2AEX::m_szBuffer](#m_szbuffer)|静态缓冲区，用来存储转换后的字符串。|  
  
## <a name="remarks"></a>备注  
 除非需要额外功能，则使用`CT2AEX`， `CW2TEX`， `CW2CTEX`， `CT2CAEX`，或**CW2A**在代码中。  
  
 此类包含固定大小的静态缓冲区用于存储转换的结果。 如果结果过大，无法放入静态缓冲区，则该类将使用 `malloc` 分配内存，并在对象超出范围时释放内存。 这样可确保，像文本转换宏可在以前版本的 ATL，它是此类是在循环中安全使用，并且它不会溢出堆栈。  
  
 如果该类尝试分配内存堆和无法正常工作，它将调用`AtlThrow`用参数**E_OUTOFMEMORY**。  
  
 默认情况下，ATL 转换类和宏用于当前线程的 ANSI 代码页转换。 如果您想要重写特定转换的该行为，作为类的构造函数的第二个参数指定的代码页。  
  
 下列宏基于此类︰  
  
- `CT2AEX`  
  
- `CW2TEX`  
  
- `CW2CTEX`  
  
- `CT2CAEX`  
  
 下面的 typedef 基于此类︰  
  
- **CW2A**  
  
 这些文本转换宏的讨论，请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)。  
  
## <a name="example"></a>示例  
 请参阅[ATL 和 MFC 字符串转换宏](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)有关使用这些字符串转换宏的示例。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlconv.h  
  
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
 用来执行转换的代码页。 请参阅对每个代码页参数讨论[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]函数[MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)的更多详细信息。  
  
### <a name="remarks"></a>备注  
 分配在转换过程中所用的缓冲区。  
  
##  <a name="dtor"></a>CW2AEX:: ~ CW2AEX  
 析构函数。  
  
```
~CW2AEX() throw();
```  
  
### <a name="remarks"></a>备注  
 释放分配的缓冲区。  
  
##  <a name="m_psz"></a>CW2AEX::m_psz  
 将源字符串存储的数据成员。  
  
```
LPSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CW2AEX::m_szBuffer  
 静态缓冲区，用来存储转换后的字符串。  
  
```
char m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpstr"></a>CW2AEX::operator LPSTR  
 转换运算符。  
  
```  
operator LPSTR() const throw();
```  
  
### <a name="return-value"></a>返回值  
 返回将文本字符串作为类型**LPSTR。**  
  
## <a name="see-also"></a>另请参阅  
 [CA2AEX 类](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 类](../../atl/reference/ca2caex-class.md)   
 [CA2WEX 类](../../atl/reference/ca2wex-class.md)   
 [CW2CWEX 类](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 类](../../atl/reference/cw2wex-class.md)   
 [类概述](../../atl/atl-class-overview.md)

