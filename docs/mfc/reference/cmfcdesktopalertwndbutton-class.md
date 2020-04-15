---
title: CMFC 桌面警报 WndButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 5b18a15f8bfd98396acae0558d121b32bc4127c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367628"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFC 桌面警报 WndButton 类

允许将按钮添加到桌面警报对话框中。

## <a name="syntax"></a>语法

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|默认构造函数。|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFC 桌面警报按钮：：是标题按钮](#iscaptionbutton)|确定该按钮是否显示在警报对话框的标题区域中。|
|[CMFC 桌面警报按钮：：正在关闭按钮](#isclosebutton)|确定按钮是否关闭警报对话框。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|名称|说明|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|指定按钮是否显示在警报对话框的标题区域中的布尔值。|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|指定按钮是否关闭警报对话框的布尔值。|

### <a name="remarks"></a>备注

默认情况下，构造函数将`m_bIsCaptionButton`和`m_bIsCloseButton`数据成员设置为 FALSE。 如果按钮`CMFCDesktopAlertDialog`位于警报`m_bIsCaptionButton`对话框的标题区域中，则父对象将设置为 TRUE。 类`CMFCDesktopAlertDialog`创建一个`CMFCDesktopAlertWndButton`对象，该对象用作关闭警报对话框并设置`m_bIsCloseButton`为 TRUE 的按钮。

将`CMFCDesktopAlertWndButton`对象添加到对象`CMFCDesktopAlertDialog`，就像添加任何按钮一样。 有关 的详细信息`CMFCDesktopAlertDialog`，请参阅[CMFC 桌面警报对话类](../../mfc/reference/cmfcdesktopalertdialog-class.md)。

## <a name="example"></a>示例

下面的示例演示如何在`SetImage``CMFCDesktopAlertWndButton`类中使用 方法。 此代码段是[桌面警报演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFC桌面警报按钮](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>要求

**标题：** afxdesktopalertwnd.h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a>CMFC 桌面警报按钮：：是标题按钮

确定该按钮是否显示在警报对话框的标题区域中。

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>返回值

如果按钮显示在警报对话框的标题区域中，则非零;否则，0。

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a>CMFC 桌面警报按钮：：正在关闭按钮

确定按钮是否关闭警报对话框。

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>返回值

如果按钮关闭警报对话框，则非零;否则，0。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 桌面警报对话类](../../mfc/reference/cmfcdesktopalertdialog-class.md)
