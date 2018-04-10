---
title: 注册表数据交换宏 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0bc12c48ef628a42c309c44ce0fc37abda9b6690
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="registry-data-exchange-macros"></a>注册表数据 Exchange 宏
这些宏执行注册表数据交换操作。  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|标记注册表数据交换映射的开始。|  
|[END_RDX_MAP](#end_rdx_map)|标记注册表数据交换映射的末尾。|  
|[RDX_BINARY](#rdx_binary)|将指定的注册表条目与类型为 BYTE 的指定的成员变量相关联。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表条目与指定的成员类型的变量的 CString 相关联。|  
|[RDX_DWORD](#rdx_dword)|将指定的注册表条目与类型为 DWORD 的指定的成员变量相关联。|  
|[RDX_TEXT](#rdx_text)|将指定的注册表条目与指定的成员类型的变量的 TCHAR 相关联。|  

## <a name="requirements"></a>惠?  
 **标头：** atlplus.h  
   
##  <a name="begin_rdx_map"></a>BEGIN_RDX_MAP  
 标记注册表数据交换映射的开始。  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>备注  
 在注册表数据交换映射内使用了以下宏来读取和写入系统注册表中的条目：  
  
|宏|描述|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|将指定的注册表条目与类型为 BYTE 的指定的成员变量相关联。|  
|[RDX_DWORD](#rdx_dword)|将指定的注册表条目与类型为 DWORD 的指定的成员变量相关联。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表条目与指定的成员类型的变量的 CString 相关联。|  
|[RDX_TEXT](#rdx_text)|将指定的注册表条目与指定的成员类型的变量的 TCHAR 相关联。|  
  
 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`你的代码需要在系统注册表之间交换数据时，应使用宏，与RDX 映射中指定的变量。  
  
##  <a name="end_rdx_map"></a>END_RDX_MAP  
 标记注册表数据交换映射的末尾。  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>RDX_BINARY  
 将指定的注册表条目与类型为 BYTE 的指定的成员变量相关联。  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>参数  
 `rootkey`  
 注册表项根。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 以字节为单位的成员变量的大小。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，以将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于执行的系统注册表和成员之间的数据交换RDX 映射中的变量。  
  
##  <a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT  
 将指定的注册表条目与指定的成员类型的变量的 CString 相关联。  
  
```
RDX_CSTRING_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>参数  
 `rootkey`  
 注册表项根。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 以字节为单位的成员变量的大小。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，以将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于执行的系统注册表和成员之间的数据交换RDX 映射中的变量。  
  
##  <a name="rdx_dword"></a>RDX_DWORD  
 将指定的注册表条目与类型为 DWORD 的指定的成员变量相关联。  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>参数  
 `rootkey`  
 注册表项根。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 以字节为单位的成员变量的大小。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，以将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于执行的系统注册表和成员之间的数据交换RDX 映射中的变量。  
  
##  <a name="rdx_text"></a>RDX_TEXT  
 将指定的注册表条目与指定的成员类型的变量的 TCHAR 相关联。  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>参数  
 `rootkey`  
 注册表项根。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 以字节为单位的成员变量的大小。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，以将成员变量与给定的注册表项相关联。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于执行的系统注册表和成员之间的数据交换RDX 映射中的变量。  
  
## <a name="see-also"></a>请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







