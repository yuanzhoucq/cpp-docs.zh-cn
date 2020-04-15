---
title: CMFCImageEditorDialog 类
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 23c2a919428689fe107b82041bd87b758ede2bc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367469"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog 类

类`CMFCImageEditorDialog`支持图像编辑器对话框。

## <a name="syntax"></a>语法

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFC图像编辑器：CMFC图像编辑器对话](#cmfcimageeditordialog)|构造 `CMFCImageEditorDialog` 对象。|

## <a name="remarks"></a>备注

该`CMFCImageEditorDialog`类提供一个对话框，其中包括：

- 用于修改图像中单个像素的图片区域。

- 绘图工具以修改图片区域中的像素。

- 用于指定绘图工具使用的颜色的调色板。

- 显示编辑效果的预览区域。

下图显示了图像编辑器对话框。

![CMFCImageEditorDialog 对话框](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog 对话框")

使用对象的一种方法`CMFCImageEditorDialog`是传递要编辑`CBitmap`的图像。 不要创建大图像，因为图像编辑区域的大小有限，并且调整逻辑像素大小以适合该区域。 调用`DoModal`方法以启动模式对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>要求

**标题：** afx 图像编辑器.h

## <a name="cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFC图像编辑器：CMFC图像编辑器对话

构造 `CMFCImageEditorDialog` 对象。

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
指向图像的指针。

*p 父级*<br/>
指向当前图像编辑器对话框的父窗口。

*nBits像素*<br/>
用于表示单个像素颜色（也称为颜色深度）的位数。  如果*nBitsPixel*参数为 -1，则颜色深度将从*pBitmap*参数指定的图像派生。 默认值为 -1。

### <a name="return-value"></a>返回值

要修改图像，请将图像指针传递给`CMFCImageEditorDialog`构造函数。 然后调用`DoModal`方法以打开一个模态对话框。 当`DoModal`方法返回时，位图包含新图像。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何构造`CMFCImageEditorDialog`类的对象。 此示例是["新控件"示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
