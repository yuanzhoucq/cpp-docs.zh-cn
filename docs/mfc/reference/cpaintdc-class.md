---
title: CPaintDC 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b34c7ee72c7a76d261a50ae227039647617d6fbd
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079020"
---
# <a name="cpaintdc-class"></a>CPaintDC 类

设备上下文类派生自[CDC](../../mfc/reference/cdc-class.md)。

## <a name="syntax"></a>语法

```
class CPaintDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|构造`CPaintDC`连接到指定[CWnd](../../mfc/reference/cwnd-class.md)。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|包含[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)用于绘制的工作区。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|此 HWND`CPaintDC`附加对象。|

## <a name="remarks"></a>备注

它将执行[cwnd:: Beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)在构造时并[CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint)在析构时。

一个`CPaintDC`响应时，仅可以使用对象[WM_PAINT](/windows/desktop/gdi/wm-paint)消息，通常在您`OnPaint`消息处理程序成员函数。

有关使用的详细信息`CPaintDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

构造`CPaintDC`对象，用于绘制，准备应用程序窗口，并将存储[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)结构[m_ps](#m_ps)成员变量。

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向`CWnd`到对象`CPaintDC`所属对象。

### <a name="remarks"></a>备注

异常 (类型的`CResourceException`) 如果则会引发 Windows [GetDC](/windows/desktop/api/winuser/nf-winuser-getdc)调用失败。 设备上下文可能不可用，如果 Windows 已分配所有可用的设备上下文。 你的应用程序争夺可在 Windows 下任何给定时间的五个常见显示上下文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

`HWND`此`CPaintDC`附加对象。

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

*m_hWnd*是受保护的类型的变量的 HWND。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps` 类型的公共成员变量[PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md)。

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>备注

它是`PAINTSTRUCT`传递给且通过填写[cwnd:: Beginpaint](../../mfc/reference/cwnd-class.md#beginpaint)。

`PAINTSTRUCT`包含应用程序用来绘制与关联的窗口的工作区信息`CPaintDC`对象。

请注意，您可以访问的设备上下文句柄通过`PAINTSTRUCT`。 但是，可以访问的句柄更直接地通过`m_hDC`成员变量的`CPaintDC`继承自 CDC。

### <a name="example"></a>示例

  有关示例，请参阅[CPaintDC::m_hWnd](#m_hwnd)。

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../visual-cpp-samples.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)

