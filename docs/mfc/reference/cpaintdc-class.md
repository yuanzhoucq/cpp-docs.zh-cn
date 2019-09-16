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
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503141"
---
# <a name="cpaintdc-class"></a>CPaintDC 类

从[CDC](../../mfc/reference/cdc-class.md)派生的设备上下文类。

## <a name="syntax"></a>语法

```
class CPaintDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|构造连接到指定 [CWnd](../../mfc/reference/cwnd-class.md) 的`CPaintDC`。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|包含用于绘制工作区的[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) 。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|此`CPaintDC`对象附加到的 HWND。|

## <a name="remarks"></a>备注

它在构造时执行[cwnd：： BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) ，在析构时执行[Cwnd：： EndPaint](../../mfc/reference/cwnd-class.md#endpaint) 。

仅当响应[WM_PAINT](/windows/win32/gdi/wm-paint)消息时`OnPaint` ，才可以使用对象，通常是在消息处理程序成员函数中。`CPaintDC`

有关使用`CPaintDC`的详细信息，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cpaintdc"></a>CPaintDC：： CPaintDC

构造一个`CPaintDC`对象，准备用于绘制的应用程序窗口，并将[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)结构存储在[m_ps](#m_ps)成员变量中。

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向`CPaintDC`对象所属`CWnd`的对象。

### <a name="remarks"></a>备注

如果 Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc)调用失败`CResourceException`，则会引发异常（类型为）。 如果 Windows 已分配了其所有可用设备上下文，则设备上下文可能不可用。 您的应用程序将在 Windows 下的任何给定时间为五个常见显示上下文进行竞争。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>CPaintDC：： m_hWnd

`HWND` 此`CPaintDC`对象附加到的。

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

*m_hWnd*是类型为 hWnd 的受保护变量。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps`是[PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct)类型的公共成员变量。

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>备注

它是`PAINTSTRUCT`传递到并由[CWnd：： BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint)填充的。

包含应用程序用来绘制`CPaintDC`与对象关联的窗口的工作区的信息。 `PAINTSTRUCT`

请注意，你可以通过`PAINTSTRUCT`访问设备上下文句柄。 但是，您可以通过`m_hDC`从 CDC `CPaintDC`继承的成员变量更直接地访问句柄。

### <a name="example"></a>示例

  请参阅[CPaintDC：： m_hWnd](#m_hwnd)的示例。

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
