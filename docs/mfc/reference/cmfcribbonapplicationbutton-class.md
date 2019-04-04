---
title: CMFCRibbonApplicationButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
ms.openlocfilehash: 01b6937ee597766922597fda5664c78f75be6b67
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772158"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton 类

实现位于应用程序窗口左上角的特殊按钮。 单击此按钮将打开一个菜单，其中通常包含公共的 **“文件”** 命令，如 **“打开”**、 **“保存”** 和 **“退出”**。

## <a name="syntax"></a>语法

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|构造并初始化一个 `CMFCRibbonApplicationButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonApplicationButton::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCRibbonApplicationButton::SetImage](#setimage)|将图像分配给功能区应用程序按钮。|

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCRibbonApplicationButton` 类中的各种方法。 该示例演示如何将图像分配给应用程序按钮，以及如何设置其工具提示。 此代码片段属于 [Draw Client 示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)

## <a name="requirements"></a>要求

**标头：** afxRibbonBar.h

##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton

构造并初始化[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)对象。

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>参数

*uiBmpResID*<br/>
若要在应用程序按钮上显示的图像资源 ID。

*hBmp*<br/>
若要在应用程序按钮上显示的位图句柄。

### <a name="remarks"></a>备注

功能区应用程序按钮是位于应用程序窗口的左上角的特殊按钮。 当用户单击此按钮时，应用程序打开一个菜单，其中通常包含公共**文件**命令，如**打开**，**保存**，和**退出**.

##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage

将图像分配给应用程序按钮。

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>参数

*uiBmpResID*<br/>
[in]若要在应用程序按钮上显示的图像资源 ID。

*hBmp*<br/>
[in]若要在应用程序按钮上显示的位图句柄。

### <a name="remarks"></a>备注

使用此方法将新映像分配到功能区应用程序按钮后创建按钮。 在应用程序窗口的左上角位于应用程序按钮。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton 类](../../mfc/reference/cmfcribbonbutton-class.md)
