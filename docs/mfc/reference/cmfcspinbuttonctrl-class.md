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
ms.openlocfilehash: 445b857400d8c82109ca7220b84bac692a2abf89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376175"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl 类

类`CMFCSpinButtonCtrl`支持绘制旋转按钮控件的可视化管理器。

## <a name="syntax"></a>语法

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|默认构造函数。|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCSpinButtonCtrl：：在画上](#ondraw)|重新绘制当前旋转按钮控件。|

## <a name="remarks"></a>备注

要使用可视化管理器在应用程序中绘制旋转按钮控件，请将`CSpinButtonCtrl`类的所有实例替换为`CMFCSpinButtonCtrl`类。

## <a name="example"></a>示例

下面的示例演示如何创建`CMFCSpinButtonCtrl`类的对象并使用其`Create`方法。

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>要求

**标题：** afxspinbuttonctrl.h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl：：在画上

重新绘制当前旋转按钮控件。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向设备上下文的指针。

### <a name="remarks"></a>备注

框架调用`CMFCSpinButtonCtrl::OnPaint`方法来处理[CWnd：：OnPaint](../../mfc/reference/cwnd-class.md#onpaint)消息，该方法反过来调用此方法`CMFCSpinButtonCtrl::OnDraw`。 重写此方法以自定义框架绘制旋转按钮控件的方式。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)
