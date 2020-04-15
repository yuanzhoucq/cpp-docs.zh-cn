---
title: CMFCAcceleratorKeyAssignCtrl 类
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: c7b60d9e695351e0c1d97b6629ff19664fcd6d05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369936"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 类

该`CMFCAcceleratorKeyAssignCtrl`类扩展[了 CEdit 类](../../mfc/reference/cedit-class.md)，以支持额外的系统按钮，如 ALT、CONTROL 和 SHIFT。

## <a name="syntax"></a>语法

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|构造 `CMFCAcceleratorKeyAssignCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC加速器键分配Ctrl：：GetAccel](#getaccel)|检索 `CMFCAcceleratorKeyAssignCtrl` 对象中按下的快捷键的 `ACCEL` 结构。|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|确定是否已定义快捷键。|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|类[CWinApp](../../mfc/reference/cwinapp-class.md)在窗口消息发送到[翻译消息](/windows/win32/api/winuser/nf-winuser-translatemessage)和[调度消息](/windows/win32/api/winuser/nf-winuser-dispatchmessage)窗口功能之前，用于转换窗口消息。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|重置快捷键。|

## <a name="remarks"></a>备注

此类通过支持快捷键（也称为加速键）来扩展 `CEdit` 类的功能。 该`CMFCAcceleratorKeyAssignCtrl`类作为[CEdit 类](../../mfc/reference/cedit-class.md)运行，还可以识别系统按钮。

此类会将物理快捷键组合映射到字符串值。 例如，假定键组合 ALT + B 映射到字符串“Alt + B”。 当用户按下 `CMFCAcceleratorKeyAssignCtrl` 对象中的此键组合时，会向用户显示“Alt + B”。 有关快捷键和字符串格式之间的映射的详细信息，请参阅[CMFC加速器密钥类](../../mfc/reference/cmfcacceleratorkey-class.md)。

## <a name="example"></a>示例

下列示例演示如何构造 `CMFCAcceleratorKeyAssignCtrl` 对象并使用其 `ResetKey` 方法来重置快捷键。

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>要求

**标题：** afx加速器键分配.h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFC加速器密钥分配Ctrl：：CMFC加速器键分配Ctrl

构造[CMFC 加速器KeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)对象。

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFC加速器键分配Ctrl：：GetAccel

检索在`ACCEL`[CMFC 加速器KeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)对象中按下的快捷键的结构。

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>返回值

描述`ACCEL`快捷键的结构。

### <a name="remarks"></a>备注

使用此函数可以检索用户输入`ACCEL`到`CMFCAcceleratorKeyAssignCtrl`对象的快捷键的结构。

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFC加速器密钥分配Ctrl：：聚焦

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFC加速器密钥分配Ctrl：：IsKey定义

确定是否已在[CMFC 加速器KeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)对象中定义快捷键。

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>返回值

如果用户已按下定义快捷键的有效键组合，则非零;否则 0。

### <a name="remarks"></a>备注

使用此函数可确定用户是否在对象`CMFCAcceleratorKeyAssignCtrl`中输入了有效的快捷键。 如果存在快捷键，则可以使用[CMFCFc 加速器KeyAssignCtrl：getAccel](#getaccel)方法获取与此快捷键`ACCEL`关联的结构。

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFC加速器键分配Ctrl：:P重新翻译消息

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>参数

[在]*pMsg*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFC加速器密钥分配Ctrl：：重置键

重置快捷键。

```
void ResetKey();
```

### <a name="remarks"></a>备注

该函数清除编辑控制文本。 这包括用户按下的任何快捷键。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC加速器密钥类](../../mfc/reference/cmfcacceleratorkey-class.md)
