---
title: CWindowDC 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa21de880dbb2b15498fb1bbcc6e9dc35350b0b3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417563"
---
# <a name="cwindowdc-class"></a>CWindowDC 类

从 `CDC`派生。

## <a name="syntax"></a>语法

```
class CWindowDC : public CDC
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|构造 `CWindowDC` 对象。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|此 HWND`CWindowDC`附加。|

## <a name="remarks"></a>备注

调用 Windows 函数[GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)在构造时并[ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc)在析构时。 这意味着`CWindowDC`对象访问的整个屏幕区域[CWnd](../../mfc/reference/cwnd-class.md) （客户端和非工作区）。

有关使用的详细信息`CWindowDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>要求

标头： afxwin.h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

构造`CWindowDC`访问的整个屏幕区域 （客户端和非工作区） 的对象`CWnd`指向对象*pWnd*。

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
窗口设备上下文对象将访问其工作区中。

### <a name="remarks"></a>备注

构造函数将调用 Windows 函数[GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)。

异常 (类型的`CResourceException`) 如果则会引发 Windows`GetWindowDC`调用失败。 设备上下文可能不可用，如果 Windows 已分配所有可用的设备上下文。 你的应用程序争夺可在 Windows 下任何给定时间的五个常见显示上下文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

HWND`CWnd`指针用于构造`CWindowDC`对象。

```
HWND m_hWnd;
```

### <a name="remarks"></a>备注

`m_hWnd` 是受保护的类型的变量的 HWND。

### <a name="example"></a>示例

  有关示例，请参阅[CWindowDC::CWindowDC](#cwindowdc)。

## <a name="see-also"></a>请参阅

[CDC 类](../../mfc/reference/cdc-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CDC 类](../../mfc/reference/cdc-class.md)
