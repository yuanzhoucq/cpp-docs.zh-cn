---
title: IRunnableObjectImpl 类
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: 6b1af7c21c6f5028ad6d3a228cb22650fa3cef42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495666"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 类

此类实现`IUnknown`并提供[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)接口的默认实现。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>参数

*T*<br/>
派生自`IRunnableObjectImpl`的类。

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|返回正在运行的控件的 CLSID。 ATL 实现将 CLSID 设置为 GUID_NULL 并返回 E_UNEXPECTED。|
|[IRunnableObjectImpl::IsRunning](#isrunning)|确定控件是否正在运行。 ATL 实现返回 TRUE。|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|将控件锁定为运行状态。 ATL 实现返回 S_OK。|
|[IRunnableObjectImpl::Run](#run)|强制运行控件。 ATL 实现返回 S_OK。|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|指示控件已嵌入。 ATL 实现返回 S_OK。|

## <a name="remarks"></a>备注

通过[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)接口, 容器可以确定控件是否正在运行、强制运行或将其锁定为运行状态。 类`IRunnableObjectImpl`提供此接口的默认实现, 并通过`IUnknown`在调试版本中将信息发送到转储设备来实现。

**相关文章**[Atl 教程](../../atl/active-template-library-atl-tutorial.md),[创建 atl 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>要求

**标头:** atlctl

##  <a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

返回正在运行的控件的 CLSID。

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>返回值

ATL 实现将\* *lpClsid*设置为 GUID_NULL, 并返回 E_UNEXPECTED。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IRunnableObject:: GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) 。

##  <a name="isrunning"></a>IRunnableObjectImpl:: IsRunning

确定控件是否正在运行。

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>返回值

ATL 实现返回 TRUE。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IRunnableObject:: IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) 。

##  <a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

将控件锁定为运行状态。

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>返回值

ATL 实现返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IRunnableObject:: LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) 。

##  <a name="run"></a>IRunnableObjectImpl:: Run

强制运行控件。

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>返回值

ATL 实现返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IRunnableObject:: Run](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) 。

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

指示控件已嵌入。

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>返回值

ATL 实现返回 S_OK。

### <a name="remarks"></a>备注

请参阅 Windows SDK 中的[IRunnableObject:: SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) 。

## <a name="see-also"></a>请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
