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
ms.openlocfilehash: 5304fa322c62f67ed075be7912697f8c87b27392
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643828"
---
# <a name="cclientdc-class"></a>CClientDC 类

负责调用 Windows 函数[GetDC](/windows/desktop/api/winuser/nf-winuser-getdc)在构造时并[ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc)在析构时。

## <a name="syntax"></a>语法

```
class CClientDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|构造`CClientDC`连接到对象`CWnd`。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|此窗口的 HWND`CClientDC`有效。|

## <a name="remarks"></a>备注

这意味着，与关联的设备上下文`CClientDC`对象是一个窗口的工作区。

有关详细信息`CClientDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cclientdc"></a>  CClientDC::CClientDC

构造`CClientDC`对象的访问的工作区[CWnd](../../mfc/reference/cwnd-class.md)指向*pWnd*。

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
窗口设备上下文对象将访问其工作区中。

### <a name="remarks"></a>备注

构造函数将调用 Windows 函数[GetDC](/windows/desktop/api/winuser/nf-winuser-getdc)。

异常 (类型的`CResourceException`) 如果则会引发 Windows`GetDC`调用失败。 设备上下文可能不可用，如果 Windows 已分配所有可用的设备上下文。 你的应用程序争夺可在 Windows 下任何给定时间的五个常见显示上下文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CClientDC::m_hWnd

`HWND`的`CWnd`指针，用于构造`CClientDC`对象。

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

*m_hWnd*是受保护的变量。

### <a name="example"></a>示例

  有关示例，请参阅[CClientDC::CClientDC](#cclientdc)。

## <a name="see-also"></a>请参阅

[MFC 示例 MDI](../../visual-cpp-samples.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
