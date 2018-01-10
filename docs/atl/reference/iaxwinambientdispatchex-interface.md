---
title: "IAxWinAmbientDispatchEx 接口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
dev_langs: C++
helpviewer_keywords: IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fd212417a00335bfc02699cf5e38eeacc6451ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 接口
此接口实现的托管控件的补充环境属性。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```  
  
## <a name="members"></a>成员  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[SetAmbientDispatch](#setambientdispatch)|调用此方法来补充具有用户定义的接口的默认环境属性接口。|  
  
## <a name="remarks"></a>备注  
 在静态链接到 ATL 和主机 ActiveX 控件，尤其是具有环境属性的 ActiveX 控件的 ATL 应用程序中包括此接口。 不包括此接口将生成此断言:"是否忘记了要传递给 CComModule::Init 的 LIBID"  
  
 此接口公开的 ATL 的 ActiveX 控件承载对象。 派生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)，`IAxWinAmbientDispatchEx`将添加一个方法，以便你补充 ATL 提供与一个你自己的环境属性界面。  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)将尝试加载类型信息有关`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`从类型库包含的代码。  
  
 如果要链接到 ATL90.dll， **AXHost**将从类型库 DLL 中加载的类型信息。  
  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)有关详细信息。  
  
## <a name="requirements"></a>惠?  
 此接口的定义可用于多种形式下, 表中所示。  
  
|定义类型|文件|  
|---------------------|----------|  
|IDL|atliface.idl|  
|类型库|ATL.dll|  
|C++|atliface.h （也包括在 ATLBase.h）|  
  
##  <a name="setambientdispatch"></a>IAxWinAmbientDispatchEx::SetAmbientDispatch  
 调用此方法来补充具有用户定义的接口的默认环境属性接口。  
  
```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```  
  
### <a name="parameters"></a>参数  
 *pDispatch*  
 指向新的接口指针。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 当`SetAmbientDispatch`调用与对新接口指针，此新界面将用于调用任何属性或方法请求的托管的控件中，如果这些属性没有已提供的[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).  
  
## <a name="see-also"></a>请参阅  
 [IAxWinAmbientDispatch 接口](../../atl/reference/iaxwinambientdispatch-interface.md)
