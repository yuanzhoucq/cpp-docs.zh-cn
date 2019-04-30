---
title: CMFCAcceleratorKey 类
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: 6a99ad00a43ac7912320ee469d542b6bf9cca3de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403953"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey 类

实现虚拟键映射和格式设置的帮助器类。

## <a name="syntax"></a>语法

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|构造 `CMFCAcceleratorKey` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|将转换为其可视表示形式的加速结构。|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|设置的快捷键`CMFCAcceleratorKey`对象。|

## <a name="remarks"></a>备注

快捷键也被称为键盘快捷方式。 如果你想要显示用户输入的键盘快捷方式[CMFCAcceleratorKeyAssignCtrl 类](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)映射的键盘快捷方式，如 Alt + Shift + S，为自定义文本的格式，如"Alt + Shift + S"。 每个`CMFCAcceleratorKey`对象将一个快捷方式键映射到文本格式。

有关如何使用键盘快捷方式和快捷键对应表的详细信息，请参阅[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCAcceleratorKey`对象以及如何使用其`Format`方法。

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>要求

**标头：** afxacceleratorkey.h

##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey

构造[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)对象。

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>参数

*lpAccel*<br/>
[in]快捷方式键指向的指针。

### <a name="remarks"></a>备注

如果在创建时，没有提供的快捷键`CMFCAccleratorKey`，使用[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)方法将与快捷键关联起来你`CMFCAcceleratorKey`对象。

##  <a name="format"></a>  CMFCAcceleratorKey::Format

将转换为其关联的字符串值的加速结构。

```
void Format(CString& str) const;
```

### <a name="parameters"></a>参数

*str*<br/>
[out]对引用`CString`对象，则该方法将已翻译的快捷键。

### <a name="remarks"></a>备注

此方法检索关联的快捷键的字符串格式。 可以设置的字符串格式[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)对象使用构造函数或方法[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)。

##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator

设置的快捷键[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)对象。

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>参数

*lpAccel*<br/>
[in]快捷方式键指向的指针。

### <a name="remarks"></a>备注

使用此方法设置的快捷键`CMFCAcceleratorKey`如果你在创建时，未提供的快捷键`CMFCAcceleratorKey`。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)
