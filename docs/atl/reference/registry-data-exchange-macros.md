---
title: "注册表数据交换宏 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
caps.latest.revision: 16
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
ms.openlocfilehash: ee3c1d639ee4a6c6bd6cf26a8c59bb1a37a4fa02
ms.lasthandoff: 02/24/2017

---
# <a name="registry-data-exchange-macros"></a>注册表数据 Exchange 宏
这些宏执行注册表数据交换操作。  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|标记的注册表数据交换映射的开头。|  
|[END_RDX_MAP](#end_rdx_map)|将标记注册表数据交换映射的结尾。|  
|[RDX_BINARY](#rdx_binary)|将指定的注册表项与类型为 BYTE 的指定的成员变量相关联。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表项与指定的成员类型的变量的 CString 相关联。|  
|[RDX_DWORD](#rdx_dword)|将指定的注册表项 DWORD 类型的指定的成员变量相关联。|  
|[RDX_TEXT](#rdx_text)|将指定的注册表项与指定的成员类型的变量的 TCHAR 相关联。|  

## <a name="requirements"></a>要求  
 **标头︰** atlplus.h  
   
##  <a name="a-namebeginrdxmapa--beginrdxmap"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP  
 标记的注册表数据交换映射的开头。  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>备注  
 在注册表数据交换映射内使用了以下宏来读取和写入系统注册表中的条目︰  
  
|宏|说明|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|将指定的注册表项与类型为 BYTE 的指定的成员变量相关联。|  
|[RDX_DWORD](#rdx_dword)|将指定的注册表项 DWORD 类型的指定的成员变量相关联。|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|将指定的注册表项与指定的成员类型的变量的 CString 相关联。|  
|[RDX_TEXT](#rdx_text)|将指定的注册表项与指定的成员类型的变量的 TCHAR 相关联。|  
  
 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`代码需要在系统注册表和 RDX 映射中指定的变量之间交换数据时，应使用宏。  
  
##  <a name="a-nameendrdxmapa--endrdxmap"></a><a name="end_rdx_map"></a>END_RDX_MAP  
 将标记注册表数据交换映射的结尾。  
  
```
END_RDX_MAP
```  
  
##  <a name="a-namerdxbinarya--rdxbinary"></a><a name="rdx_binary"></a>RDX_BINARY  
 将指定的注册表项与类型为 BYTE 的指定的成员变量相关联。  
  
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
 注册表键根目录。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 大小 （以字节为单位的成员变量）。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏与给定的注册表项相关联的成员变量。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于 RDX 映射中执行系统注册表和成员变量之间交换数据。  
  
##  <a name="a-namerdxcstringtexta--rdxcstringtext"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT  
 将指定的注册表项与指定的成员类型的变量的 CString 相关联。  
  
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
 注册表键根目录。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 大小 （以字节为单位的成员变量）。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏与给定的注册表项相关联的成员变量。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于 RDX 映射中执行系统注册表和成员变量之间交换数据。  
  
##  <a name="a-namerdxdworda--rdxdword"></a><a name="rdx_dword"></a>RDX_DWORD  
 将指定的注册表项 DWORD 类型的指定的成员变量相关联。  
  
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
 注册表键根目录。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 大小 （以字节为单位的成员变量）。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏与给定的注册表项相关联的成员变量。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于 RDX 映射中执行系统注册表和成员变量之间交换数据。  
  
##  <a name="a-namerdxtexta--rdxtext"></a><a name="rdx_text"></a>RDX_TEXT  
 将指定的注册表项与指定的成员类型的变量的 TCHAR 相关联。  
  
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
 注册表键根目录。  
  
 `subkey`  
 注册表子项中。  
  
 `valuename`  
 注册表项中。  
  
 `member`  
 要与指定的注册表项相关联的成员变量。  
  
 `member_size`  
 大小 （以字节为单位的成员变量）。  
  
### <a name="remarks"></a>备注  
 结合使用此宏`BEGIN_RDX_MAP`和`END_RDX_MAP`宏与给定的注册表项相关联的成员变量。 全局函数[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)，或通过创建具有相同名称的成员函数`BEGIN_RDX_MAP`和`END_RDX_MAP`宏，应该用于 RDX 映射中执行系统注册表和成员变量之间交换数据。  
  
## <a name="see-also"></a>另请参阅  
 [宏](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)








