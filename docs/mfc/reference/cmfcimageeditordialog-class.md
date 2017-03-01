---
title: "CMFCImageEditorDialog 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImageEditorDialog
dev_langs:
- C++
helpviewer_keywords:
- CMFCImageEditorDialog class
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1a629f9699aa2d6fb185737b51b36259ce574fe0
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog 类
`CMFCImageEditorDialog`类支持图像编辑器对话框。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCImageEditorDialog : public CDialogEx  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|构造 `CMFCImageEditorDialog` 对象。|  
  
## <a name="remarks"></a>备注  
 `CMFCImageEditorDialog`类提供了一个对话框，其中包括︰  
  
-   一个用于修改图像中的单个像素的图片区域。  
  
-   绘图工具来修改图片区域中的像素。  
  
-   若要指定绘图工具使用的颜色调色板。  
  
-   预览区域以显示您的编辑的效果。  
  
 下图显示的图像编辑器对话框。  
  
 ![CMFCImageEditorDialog 对话框](../../mfc/reference/media/imageedit.png "imageedit")  
  
 一种方式使用`CMFCImageEditorDialog`对象是将其传递`CBitmap`映像以进行编辑。 不要创建较大的图像，因为图像编辑区域有大小限制而逻辑像素大小调整以适合区域。 调用`DoModal`方法来启动一个模式对话框。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afximageeditordialog.h  
  
##  <a name="a-namecmfcimageeditordialoga--cmfcimageeditordialogcmfcimageeditordialog"></a><a name="cmfcimageeditordialog"></a>CMFCImageEditorDialog::CMFCImageEditorDialog  
 构造 `CMFCImageEditorDialog` 对象。  
  
```  
CMFCImageEditorDialog(
    CBitmap* pBitmap,  
    CWnd* pParent=NULL,  
    int nBitsPixel=-1);
```  
  
### <a name="parameters"></a>参数  
 `pBitmap`  
 指针的图像。  
  
 `pParent`  
 当前的图像编辑器对话框中的父窗口的指针。  
  
 `nBitsPixel`  
 用于表示也称为色彩深度的单一像素的颜色的比特数。  如果`nBitsPixel`参数为-1 时，颜色深度派生自指定的图像`pBitmap`参数。 默认值为 -1。  
  
### <a name="return-value"></a>返回值  
 若要修改图像，图像将指针传递至`CMFCImageEditorDialog`构造函数。 然后，调用`DoModal`方法打开一个模式对话框。 当`DoModal`方法返回时，该位图包含新映像。  
  
### <a name="remarks"></a>备注  
  
### <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCImageEditorDialog`类。 此示例摘自[新控件示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_NewControls #&8;](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]  
[!code-cpp[NVC_MFC_NewControls #&40;](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)

