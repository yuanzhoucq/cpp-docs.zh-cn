---
title: CPaintDC 类
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: 55342b03454a6dba07bc10ea5f0464c34e0e8db3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374778"
---
# <a name="cpaintdc-class"></a>CPaintDC 类

派生自[CDC](../../mfc/reference/cdc-class.md)的设备上下文类 。

## <a name="syntax"></a>语法

```
class CPaintDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPaintDC：CPaintDC](#cpaintdc)|构造连接到`CPaintDC`指定的[CWnd](../../mfc/reference/cwnd-class.md)的 。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CPaintDC：m_ps](#m_ps)|包含用于绘制工作区的[PAINTSTRUCT。](/windows/win32/api/winuser/ns-winuser-paintstruct)|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CPaintDC：m_hWnd](#m_hwnd)|此`CPaintDC`对象附加到的 HWND。|

## <a name="remarks"></a>备注

它执行[CWnd：：在施工时开始绘制，](../../mfc/reference/cwnd-class.md#beginpaint)在销毁时[执行 CWnd：endPaint。](../../mfc/reference/cwnd-class.md#endpaint)

对象`CPaintDC`只能在响应[WM_PAINT](/windows/win32/gdi/wm-paint)消息时使用，通常在`OnPaint`消息处理程序成员函数中。

有关 使用`CPaintDC`的详细信息，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a>CPaintDC：CPaintDC

构造`CPaintDC`对象，准备用于绘制的应用程序窗口，并将[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)结构存储在[m_ps](#m_ps)成员变量中。

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向`CPaintDC`对象所属`CWnd`的对象。

### <a name="remarks"></a>备注

如果 Windows `CResourceException` [GetDC](/windows/win32/api/winuser/nf-winuser-getdc)调用失败，将引发异常（类型类型）。 如果 Windows 已分配其所有可用设备上下文，则设备上下文可能不可用。 您的应用程序竞争 Windows 下任何给定时间可用的五个常见显示上下文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a>CPaintDC：m_hWnd

`HWND`附加到此`CPaintDC`对象。

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

*m_hWnd*是 HWND 类型的受保护变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a>CPaintDC：m_ps

`m_ps`是[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)类型的公共成员变量。

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>备注

它是`PAINTSTRUCT`传递给并填写的[CWnd：：BeginPaint。](../../mfc/reference/cwnd-class.md#beginpaint)

包含`PAINTSTRUCT`应用程序用于绘制与`CPaintDC`对象关联的窗口的工作区的信息。

请注意，您可以通过 访问设备上下文句柄`PAINTSTRUCT`。 但是，您可以通过从 CDC`m_hDC``CPaintDC`继承的成员变量更直接地访问句柄。

### <a name="example"></a>示例

  请参阅[CPaintDC：：m_hWnd](#m_hwnd)的示例。

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
