---
title: CWindowDC 类
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 89a822280ddebca942016f9a3a334a7128d8456a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371983"
---
# <a name="cwindowdc-class"></a>CWindowDC 类

从 `CDC`派生。

## <a name="syntax"></a>语法

```
class CWindowDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWindowDC：CWindowDC](#cwindowdc)|构造 `CWindowDC` 对象。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CWindowDC：m_hWnd](#m_hwnd)|附加到的`CWindowDC`HWND。|

## <a name="remarks"></a>备注

在构造时调用 Windows 函数[GetWindowDC，](/windows/win32/api/winuser/nf-winuser-getwindowdc)在销毁时[调用释放 DC。](/windows/win32/api/winuser/nf-winuser-releasedc) 这意味着对象`CWindowDC`访问[CWnd](../../mfc/reference/cwnd-class.md)的整个屏幕区域（客户端和非客户端区域）。

有关 使用`CWindowDC`的详细信息，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>要求

标头: afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a>CWindowDC：CWindowDC

构造一个`CWindowDC`对象，该对象访问`CWnd`*pWnd*指向的对象的整个屏幕区域（客户端和非客户端）。

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
设备上下文对象将访问其工作区的窗口。

### <a name="remarks"></a>备注

构造函数调用 Windows 函数[GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)。

如果 Windows`GetWindowDC`调用`CResourceException`失败，将引发异常（类型 类型）。 如果 Windows 已分配其所有可用设备上下文，则设备上下文可能不可用。 您的应用程序竞争 Windows 下任何给定时间可用的五个常见显示上下文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a>CWindowDC：m_hWnd

指针的`CWnd`HWND 用于构造`CWindowDC`对象。

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

`m_hWnd`是 HWND 类型的受保护变量。

### <a name="example"></a>示例

  请参阅[CWindowDC 的示例：cWindowDC](#cwindowdc)。

## <a name="see-also"></a>另请参阅

[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
