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
ms.openlocfilehash: 97f16fa00b2e90fd9c43bf9b6792b4eafe7d7b88
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780440"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog 类

`CMFCImageEditorDialog`类支持图像编辑器对话框。

## <a name="syntax"></a>语法

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|构造 `CMFCImageEditorDialog` 对象。|

## <a name="remarks"></a>备注

`CMFCImageEditorDialog`类提供了一个对话框，其中包括：

- 用于修改图像中的单个像素图片区域。

- 绘图工具来修改图片区域中的像素。

- 若要指定绘图工具使用的颜色调色板。

- 显示您的编辑的效果预览区域。

下图显示的图像编辑器对话框。

![CMFCImageEditorDialog 对话框](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog 对话框")

使用一种方式`CMFCImageEditorDialog`对象是将其传递`CBitmap`映像以进行编辑。 不要创建一个大图像，因为图像编辑区域存在大小限制和逻辑像素大小调整以适合区域。 调用`DoModal`方法以启动模式对话框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>要求

**标头：** afximageeditordialog.h

##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog

构造 `CMFCImageEditorDialog` 对象。

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>参数

*pBitmap*<br/>
指针的图像。

*pParent*<br/>
指向当前图像编辑器对话框的父窗口的指针。

*nBitsPixel*<br/>
用于表示也称为色彩深度单个像素的颜色的比特数。  如果*nBitsPixel*参数的值为-1，颜色深度派生自指定的图像*pBitmap*参数。 默认值为 -1。

### <a name="return-value"></a>返回值

若要修改映像，请将传递到 image 指针`CMFCImageEditorDialog`构造函数。 然后，调用`DoModal`方法打开模式对话框。 当`DoModal`方法返回时，位图包含新映像。

### <a name="remarks"></a>备注

### <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCImageEditorDialog`类。 此示例摘自[新的控件示例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
