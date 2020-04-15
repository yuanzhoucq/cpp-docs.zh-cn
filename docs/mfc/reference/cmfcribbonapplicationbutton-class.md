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
ms.openlocfilehash: 0debd40825990b647cd5b1df9a144e3abd450de3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361610"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton 类

实现位于应用程序窗口左上角的特殊按钮。 单击此按钮将打开一个菜单，其中通常包含公共的 **“文件”** 命令，如 **“打开”**、 **“保存”** 和 **“退出”**。

## <a name="syntax"></a>语法

```
class CMFCRibbonApplicationButton : public CMFCRibbonButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC功能化应用按钮：：CMFC功能化应用按钮](#cmfcribbonapplicationbutton)|构造并初始化一个 `CMFCRibbonApplicationButton` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|`CMFCRibbonApplicationButton::CreateObject`|由框架用于创建此类类型的动态实例。|
|`CMFCRibbonApplicationButton::GetThisClass`|框架用于获取指向与此类类型关联的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对象的指针。|
|[CMFC功能化应用按钮：：设置图像](#setimage)|将图像分配给功能区应用程序按钮。|

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

**标题：** afxRibbonBar.h

## <a name="cmfcribbonapplicationbuttoncmfcribbonapplicationbutton"></a><a name="cmfcribbonapplicationbutton"></a>CMFC功能化应用按钮：：CMFC功能化应用按钮

构造并初始化[CMFC 功能应用程序按钮](../../mfc/reference/cmfcribbonapplicationbutton-class.md)对象。

```
CMFCRibbonApplicationButton();
CMFCRibbonApplicationButton(UINT uiBmpResID);
CMFCRibbonApplicationButton(HBITMAP hBmp);
```

### <a name="parameters"></a>参数

*乌布布雷斯ID*<br/>
要在应用程序按钮上显示的图像的资源 ID。

*hBmp*<br/>
要显示在应用程序按钮上的位图的句柄。

### <a name="remarks"></a>备注

功能区应用程序按钮是位于应用程序窗口左上角的特殊按钮。 当用户单击此按钮时，应用程序将打开一个菜单，该菜单通常包含常见的**文件**命令，如**打开**、**保存**和**退出**。

## <a name="cmfcribbonapplicationbuttonsetimage"></a><a name="setimage"></a>CMFC功能化应用按钮：：设置图像

将图像分配给应用程序按钮。

```
void SetImage(UINT uiBmpResID);
void SetImage(HBITMAP hBmp);
```

### <a name="parameters"></a>参数

*乌布布雷斯ID*<br/>
[在]要在应用程序按钮上显示的图像的资源 ID。

*hBmp*<br/>
[在]要显示在应用程序按钮上的位图的句柄。

### <a name="remarks"></a>备注

使用此方法在创建按钮后将新映像分配给功能区应用程序按钮。 应用程序按钮位于应用程序窗口的左上角。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC 功能按钮类](../../mfc/reference/cmfcribbonbutton-class.md)
