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
ms.openlocfilehash: 46428740d052c70218d4443395777428cdf3c3b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507338"
---
# <a name="cclientdc-class"></a>CClientDC 类

负责在构造时调用 Windows 函数[GetDC](/windows/win32/api/winuser/nf-winuser-getdc) , 并在析构时调用[ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) 。

## <a name="syntax"></a>语法

```
class CClientDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|构造连接到的`CWnd`对象。`CClientDC`|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|此`CClientDC`对其有效的窗口的 HWND。|

## <a name="remarks"></a>备注

这意味着与`CClientDC`对象关联的设备上下文是窗口的工作区。

有关的详细信息`CClientDC`, 请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cclientdc"></a>CClientDC:: CClientDC

构造一个`CClientDC`对象, 该对象访问*pWnd*指向的[CWnd](../../mfc/reference/cwnd-class.md)的工作区。

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
设备上下文对象将访问的工作区所在的窗口。

### <a name="remarks"></a>备注

构造函数调用 Windows 函数[GetDC](/windows/win32/api/winuser/nf-winuser-getdc)。

如果 Windows `CResourceException` `GetDC`调用失败, 则会引发异常 (类型为)。 如果 Windows 已分配了其所有可用设备上下文, 则设备上下文可能不可用。 您的应用程序将在 Windows 下的任何给定时间为五个常见显示上下文进行竞争。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CClientDC::m_hWnd

用于构造对象`CClientDC`的指针的。 `CWnd` `HWND`

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

*m_hWnd*是受保护的变量。

### <a name="example"></a>示例

  请参阅[CClientDC:: CClientDC](#cclientdc)的示例。

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../overview/visual-cpp-samples.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
