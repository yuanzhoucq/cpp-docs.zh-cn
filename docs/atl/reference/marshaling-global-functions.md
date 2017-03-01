---
title: "封送处理全局函数 |Microsoft 文档"
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
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
caps.latest.revision: 19
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
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: dd4b8d50ec69974b7b2af29438b1657e1ce592b4
ms.lasthandoff: 02/24/2017

---
# <a name="marshaling-global-functions"></a>封送处理全局函数
这些函数提供支持封送处理和封送数据转换为接口指针。  
  
> [!IMPORTANT]
>  下表中列出的函数不能用于应用程序中执行[!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]。  
  
|||  
|-|-|  
|[AtlFreeMarshalStream](#atlfreemarshalstream)|释放封送数据和`IStream`指针。|  
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|创建新的流对象，并将封送指定的接口指针。|  
|[AtlUnmarshalPtr](#atlunmarshalptr)|将流的封送数据转换为一个接口指针。|  
  
##  <a name="a-nameatlfreemarshalstreama--atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream  
 释放流中的封送数据，然后释放流指针。  

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```  
  
### <a name="parameters"></a>参数  
 `pStream`  
 [in]一个指向`IStream`上用于封送处理的流接口。  
  
### <a name="example"></a>示例  
  请参阅示例[AtlMarshalPtrInProc](#atlmarshalptrinproc)。  
  
##  <a name="a-nameatlmarshalptrinproca--atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc  
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
 [out]一个指向`IStream`上新的流对象用于封送的接口。  
  
### <a name="return-value"></a>返回值  
 一个标准的 HRESULT 值。  
  
### <a name="remarks"></a>备注  
 **MSHLFLAGS_TABLESTRONG**以便可以将鼠标指针封送到多个流设置标志。 指针也可以取消封送多次。  
  
 如果封送处理将失败，则释放流指针。  
  
 `AtlMarshalPtrInProc`仅可在进程内对象的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_COM&#50;](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]  
  
##  <a name="a-nameatlunmarshalptra--atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr  
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

