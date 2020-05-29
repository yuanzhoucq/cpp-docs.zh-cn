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
ms.openlocfilehash: 2843c0c25a5c104ffbdff72255ac5d85cf53b1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329449"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl 类

此类实现`IUnknown`并提供[IRunnableObject 接口](/windows/win32/api/objidl/nn-objidl-irunnableobject)的默认实现。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

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

|名称|说明|
|----------|-----------------|
|[IRunn 可对象Impl：：获取运行类](#getrunningclass)|返回正在运行的控件的 CLSID。 ATL 实现将 CLSID 设置为GUID_NULL并返回E_UNEXPECTED。|
|[可运行对象impl：：正在运行](#isrunning)|确定控件是否正在运行。 ATL 实现返回 TRUE。|
|[可运行对象Impl：：锁定运行](#lockrunning)|将控件锁定到运行状态。 ATL 实现返回S_OK。|
|[IRunnable 对象Impl：：运行](#run)|强制控件运行。 ATL 实现返回S_OK。|
|[可运行对象 Impl：：设置包含对象](#setcontainedobject)|指示控件已嵌入。 ATL 实现返回S_OK。|

## <a name="remarks"></a>备注

[IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)接口使容器能够确定控件是否正在运行、强制它运行或将其锁定到运行状态。 类`IRunnableObjectImpl`通过在调试生成中向转储设备发送`IUnknown`信息来提供此接口的默认实现和实现。

**相关文章** [ATL 教程](../../atl/active-template-library-atl-tutorial.md)， 创建[ATL 项目](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>要求

**标题：** atlctl.h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunn 可对象Impl：：获取运行类

返回正在运行的控件的 CLSID。

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>返回值

ATL 实现将\* *lpClsid*集到GUID_NULL并返回E_UNEXPECTED。

### <a name="remarks"></a>备注

请参阅[IRunnableObject：获取](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass)Windows SDK 中的运行类。

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a>可运行对象impl：：正在运行

确定控件是否正在运行。

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>返回值

ATL 实现返回 TRUE。

### <a name="remarks"></a>备注

请参阅[IRunnableObject：正在](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning)Windows SDK 中运行。

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>可运行对象Impl：：锁定运行

将控件锁定到运行状态。

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>返回值

ATL 实现返回S_OK。

### <a name="remarks"></a>备注

请参阅[IRunnableObject：：在](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning)Windows SDK 中锁定运行。

## <a name="irunnableobjectimplrun"></a><a name="run"></a>IRunnable 对象Impl：：运行

强制控件运行。

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>返回值

ATL 实现返回S_OK。

### <a name="remarks"></a>备注

请参阅[IRunnableObject：：](/windows/win32/api/objidl/nf-objidl-irunnableobject-run)在 Windows SDK 中运行。

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>可运行对象 Impl：：设置包含对象

指示控件已嵌入。

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>返回值

ATL 实现返回S_OK。

### <a name="remarks"></a>备注

请参阅[IRunnableObject：：在](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject)Windows SDK 中设置包含对象。

## <a name="see-also"></a>另请参阅

[CComControl 类](../../atl/reference/ccomcontrol-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
