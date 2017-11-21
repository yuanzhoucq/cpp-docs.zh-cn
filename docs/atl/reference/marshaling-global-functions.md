---
title: "封送处理全局函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
dev_langs: C++
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9692e326dc8256c29373b72181517925d729da87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="marshaling-global-functions"></a>封送处理的全局函数
这些函数提供有关封送处理和封送数据转换为接口指针的支持。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序。  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|释放封送数据和`IStream`指针。|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|创建新的流对象，并将封送指定的接口指针。|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|将流的封送数据转换为的接口指针。|  

## <a name="requirements"></a>要求：
**标头：** atlbase.h
  
##  <a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 释放流中的封送数据，然后释放流指针。  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 [in]指向的指针`IStream`流用于封送的接口。  
  
### <a name="example"></a>示例  
  请参阅示例[AtlMarshalPtrInProc](#atlmarshalptrinproc)。  
  
##  <a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
 创建新的流对象，将代理的 CLSID 写入流，并通过将初始化代理所需的数据写入流来封送指定接口指针。  
  
```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```  
  
### <a name="parameters"></a>参数  
 *pUnk*  
 [in]指向要封送处理的接口的指针。  
  
 `iid`  
 [in]正封送的接口的 GUID。  
  
 `ppStream`  
 [out]指向的指针`IStream`上新的流对象用于封送的接口。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 **MSHLFLAGS_TABLESTRONG**以便可以将指针封送到多个流设置标志。 指针也可以取消封送多次。  
  
 如果封送处理失败，则释放流指针。  
  
 `AtlMarshalPtrInProc`仅可指向进程内对象的指针上使用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
 将流的封送数据转换为可由客户端使用的接口指针。  
   
```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 [in]指向正在取消封送的流的指针。  
  
 `iid`  
 [in]正在取消封送的接口的 GUID。  
  
 `ppUnk`  
 [out]指向取消封送的接口的指针。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="example"></a>示例  
  请参阅示例[AtlMarshalPtrInProc](#atlmarshalptrinproc)。  
  
## <a name="see-also"></a>另请参阅  
 [函数](../../atl/reference/atl-functions.md)
