---
title: CMFC加速器密钥类
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
ms.openlocfilehash: 7d66e7043325bbbd324f3ac443368787a653ebe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369930"
---
# <a name="cmfcacceleratorkey-class"></a>CMFC加速器密钥类

实现虚拟密钥映射和格式化的帮助程序类。

## <a name="syntax"></a>语法

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC加速器键：CMFC加速器键](#cmfcacceleratorkey)|构造 `CMFCAcceleratorKey` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC加速器键：格式](#format)|将 ACCEL 结构转换为其可视表示形式。|
|[CMFC加速器键：：设置加速器](#setaccelerator)|设置`CMFCAcceleratorKey`对象的快捷键。|

## <a name="remarks"></a>备注

快捷键也称为快捷键。 如果要显示用户输入的键盘快捷键[，CMFC加速器KeyAssignCtrl 类](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)会将键盘快捷键（如 Alt_Shift_S）映射到自定义文本格式，如"Alt + Shift + S"。 每个`CMFCAcceleratorKey`对象将单个快捷键映射到文本格式。

有关如何使用快捷键和快捷键表的详细信息，请参阅[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCAcceleratorKey`对象以及如何使用其`Format`方法。

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>要求

**标题：** afx加速器键.h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFC加速器键：CMFC加速器键

构造[CMFC 加速器键](../../mfc/reference/cmfcacceleratorkey-class.md)对象。

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>参数

*lpAccel*<br/>
[在]指向快捷键的指针。

### <a name="remarks"></a>备注

如果在创建 时未提供快捷键`CMFCAccleratorKey`，请使用[CMFCAcceleratorKey：：setAccelerator](#setaccelerator)方法将快捷键与`CMFCAcceleratorKey`对象相关联。

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a>CMFC加速器键：格式

将 ACCEL 结构转换为其关联的字符串值。

```
void Format(CString& str) const;
```

### <a name="parameters"></a>参数

*Str*<br/>
[出]对对象引用`CString`，该方法在其中写入已翻译的快捷键。

### <a name="remarks"></a>备注

此方法检索关联的快捷键的字符串格式。 您可以使用构造函数或方法[CMFC 加速器键：：：setaccelerator](#setaccelerator)设置，设置[CMFC加速器Key](../../mfc/reference/cmfcacceleratorkey-class.md)对象的字符串格式。

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFC加速器键：：设置加速器

设置[CMFC 加速器键](../../mfc/reference/cmfcacceleratorkey-class.md)对象的快捷键。

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>参数

*lpAccel*<br/>
[在]指向快捷键的指针。

### <a name="remarks"></a>备注

`CMFCAcceleratorKey`如果在 创建 时未提供快捷键，请使用 此方法为 设置 的`CMFCAcceleratorKey`快捷键。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager 类](../../mfc/reference/ckeyboardmanager-class.md)
