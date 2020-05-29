---
title: CClientDC 类
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: abe8a3220fd37a0375fcf37504c715edf4c6962e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352295"
---
# <a name="cclientdc-class"></a>CClientDC 类

负责在施工时调用 Windows 函数[GetDC，](/windows/win32/api/winuser/nf-winuser-getdc)在销毁时[调用释放 DC。](/windows/win32/api/winuser/nf-winuser-releasedc)

## <a name="syntax"></a>语法

```
class CClientDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CClientDC：CClientDC](#cclientdc)|构造连接到`CClientDC`的对象`CWnd`。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[CClientDC：m_hWnd](#m_hwnd)|其`CClientDC`有效的窗口的 HWND。|

## <a name="remarks"></a>备注

这意味着与`CClientDC`对象关联的设备上下文是窗口的工作区。

有关 的详细信息`CClientDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC：CClientDC

构造一个`CClientDC`对象，该对象访问*pWnd*指向的[CWnd](../../mfc/reference/cwnd-class.md)的工作区。

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
设备上下文对象将访问其工作区的窗口。

### <a name="remarks"></a>备注

构造函数调用 Windows 函数[GetDC](/windows/win32/api/winuser/nf-winuser-getdc)。

如果 Windows`GetDC`调用`CResourceException`失败，将引发异常（类型 类型）。 如果 Windows 已分配其所有可用设备上下文，则设备上下文可能不可用。 您的应用程序竞争 Windows 下任何给定时间可用的五个常见显示上下文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a>CClientDC：m_hWnd

用于`HWND`构造对象的`CWnd`指针的`CClientDC`。

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

*m_hWnd*是受保护的变量。

### <a name="example"></a>示例

  请参阅[CClientDC 示例：cClientDC](#cclientdc)。

## <a name="see-also"></a>另请参阅

[MFC 样品 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
