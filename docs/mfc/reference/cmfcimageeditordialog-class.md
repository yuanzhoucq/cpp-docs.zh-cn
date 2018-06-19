---
title: CMFCImageEditorDialog 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 795e5548e93323af389c3faeaefa7dda0bf7d80c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376244"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog 类
`CMFCImageEditorDialog`类支持的图像编辑器对话框。  
  
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
 `CMFCImageEditorDialog`类提供一个对话框，其中包括：  
  
-   用于修改在映像中的单个像素图片区域。  
  
-   绘图工具修改图片区域中的像素。  
  
-   若要指定的绘图工具使用颜色调色板。  
  
-   显示你的编辑的效果预览区域。  
  
 下图显示的图像编辑器对话框。  
  
 ![CMFCImageEditorDialog 对话框](../../mfc/reference/media/imageedit.png "imageedit")  
  
 一种方式使用`CMFCImageEditorDialog`对象是将其传递`CBitmap`映像以进行编辑。 不要创建较大的图像，因为编辑区域的映像具有有限的大小和逻辑像素大小调整以适合区域。 调用`DoModal`方法以启动模式对话框。  
  
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
 `pBitmap`  
 指向图像的指针。  
  
 `pParent`  
 指向当前的图像编辑器对话框的父窗口的指针。  
  
 `nBitsPixel`  
 用于表示对一个像素，也称为颜色深度的颜色的比特数。  如果`nBitsPixel`参数的值为-1，从指定的映像派生的颜色深度`pBitmap`参数。 默认值为 -1。  
  
### <a name="return-value"></a>返回值  
 若要修改映像时，将传递到的映像指针`CMFCImageEditorDialog`构造函数。 然后调用`DoModal`方法打开模式对话框。 当`DoModal`方法返回时，该位图包含新映像。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCImageEditorDialog`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]  
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
