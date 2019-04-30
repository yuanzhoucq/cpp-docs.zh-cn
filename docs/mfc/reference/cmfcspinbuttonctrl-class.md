---
title: CMFCSpinButtonCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 60808359c11604368493031e1b6f4573b3b2026f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410088"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl 类

`CMFCSpinButtonCtrl`类支持绘制数值调节钮按钮控件的可视管理器。

## <a name="syntax"></a>语法

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|默认构造函数。|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|重新绘制当前数值调节按钮控件。|

## <a name="remarks"></a>备注

若要使用视觉管理器在你的应用程序中绘制数值调节按钮控件，所有的实例替换为`CSpinButtonCtrl`类的`CMFCSpinButtonCtrl`类。

## <a name="example"></a>示例

下面的示例演示如何创建的对象`CMFCSpinButtonCtrl`类并使用其`Create`方法。

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxspinbuttonctrl.h

##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw

重新绘制当前数值调节按钮控件。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

### <a name="remarks"></a>备注

框架将调用`CMFCSpinButtonCtrl::OnPaint`方法以处理[CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint)消息，并且方法又调用这`CMFCSpinButtonCtrl::OnDraw`方法。 重写此方法以自定义框架绘制数值调节钮按钮控件的方式。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)
