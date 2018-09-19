---
title: IRunnableObjectImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
dev_langs:
- C++
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ad1efa3badf310a78b69d3abba5b9874e01daf7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020961"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 类

此类实现`IUnknown`，并提供的默认实现[IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject)接口。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
您的类，派生自`IRunnableObjectImpl`。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|返回正在运行的控件的 CLSID。 ATL 实现设置为 GUID_NULL 的 CLSID，并返回 E_UNEXPECTED。|
|[IRunnableObjectImpl::IsRunning](#isrunning)|确定控件是否正在运行。 ATL 实现，则返回 TRUE。|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|锁定到正在运行状态的控件。 ATL 实现返回 S_OK。|
|[IRunnableObjectImpl::Run](#run)|强制控件运行。 ATL 实现返回 S_OK。|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|该值指示控件嵌入。 ATL 实现返回 S_OK。|

## <a name="remarks"></a>备注

[IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject)接口，若要确定控件是否正在运行，强制其运行，或将其锁定到正在运行状态的容器。 类`IRunnableObjectImpl`提供默认实现此接口并实现`IUnknown`信息发送给转储调试中的设备生成。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)，[创建 ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>要求

**标头：** atlctl.h

##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass

返回正在运行的控件的 CLSID。

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>返回值

ATL 实现集\* *lpClsid* GUID_NULL 和返回 E_UNEXPECTED。

### <a name="remarks"></a>备注

请参阅[IRunnableObject::GetRunningClass](/windows/desktop/api/objidl/nf-objidl-irunnableobject-getrunningclass) Windows SDK 中。

##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning

确定控件是否正在运行。

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>返回值

ATL 实现，则返回 TRUE。

### <a name="remarks"></a>备注

请参阅[IRunnableObject::IsRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-isrunning) Windows SDK 中。

##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning

锁定到正在运行状态的控件。

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>返回值

ATL 实现返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IRunnableObject::LockRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-lockrunning) Windows SDK 中。

##  <a name="run"></a>  IRunnableObjectImpl::Run

强制控件运行。

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>返回值

ATL 实现返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IRunnableObject::Run](/windows/desktop/api/objidl/nf-objidl-irunnableobject-run) Windows SDK 中。

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

该值指示控件嵌入。

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>返回值

ATL 实现返回 S_OK。

### <a name="remarks"></a>备注

请参阅[IRunnableObject::SetContainedObject](/windows/desktop/api/objidl/nf-objidl-irunnableobject-setcontainedobject) Windows SDK 中。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
