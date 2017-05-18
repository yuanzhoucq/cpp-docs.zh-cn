---
title: "IAxWinAmbientDispatchEx 界面 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinAmbientDispatchEx
- No header/ATL::IAxWinAmbientDispatchEx
- No header/ATL::SetAmbientDispatch
dev_langs:
- C++
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
caps.latest.revision: 25
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 915514a021aa89b751a49a34cb53b693b9fd0c45
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx 接口
此接口实现托管控件的补充环境的属性。  
  
> [!IMPORTANT]
>  该类及其成员无法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中执行的应用程序中使用。  
  
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
 在静态链接到 ATL 和主机的 ActiveX 控件，尤其是环境属性的 ActiveX 控件的 ATL 应用程序中包括此接口。 不包括此接口将生成此断言:"您是否忘记了要传递给 CComModule::Init 的 LIBID"  
  
 此接口由 ATL 的 ActiveX 控件承载对象公开。 派生自[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)，`IAxWinAmbientDispatchEx`都会添加一个允许您补充由 ATL 提供与自己的环境属性接口的方法。  
  
 [AXHost](https://msdn.microsoft.com/library/system.windows.forms.axhost.aspx)将尝试加载的类型信息有关`IAxWinAmbientDispatch`和`IAxWinAmbientDispatchEx`从类型库包含的代码。  
  
 如果要链接到 ATL90.dll， **AXHost**将从该 DLL 中的类型库加载的类型信息。  
  
 请参阅[承载 ActiveX 控件使用 ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md)的更多详细信息。  
  
## <a name="requirements"></a>要求  
 此接口的定义为提供多种形式下, 表中所示。  
  
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
 当`SetAmbientDispatch`调用与对新接口指针，这种新接口将用于调用任何属性或方法请求的托管控件，如果这些属性不会由已提供[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)。  
  
## <a name="see-also"></a>另请参阅  
 [IAxWinAmbientDispatch 接口](../../atl/reference/iaxwinambientdispatch-interface.md)

