---
title: "CMFCImagePaintArea 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
dev_langs:
- C++
helpviewer_keywords:
- CMFCImagePaintArea class
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c16fd9605474e57f167646ddc9bc91d235d1cba5
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea 类
提供用于修改图像编辑器对话框中的图像的图片区域。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|构造 `CMFCImagePaintArea` 对象。|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCImagePaintArea::GetMode](#getmode)|检索当前绘图模式。|  
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|设置图片区域的位图图像。|  
|[CMFCImagePaintArea::SetColor](#setcolor)|设置当前绘图的颜色。|  
|[CMFCImagePaintArea::SetMode](#setmode)|设置当前绘图模式。|  
  
### <a name="remarks"></a>备注  
 此类不应在代码中直接使用。  
  
 框架使用此类以在图像编辑器对话框中显示图片区域。 图像编辑器对话框中的详细信息，请参阅[CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCImagePaintArea`类中，设置当前绘图时的颜色，设置当前绘图模式中，并设置图片区域的位图图像。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&37;](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afximagepaintarea.h  
  
##  <a name="cmfcimagepaintarea"></a>CMFCImagePaintArea::CMFCImagePaintArea  
 构造 `CMFCImagePaintArea` 对象。  
  
```  
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pParentDlg`|指向是父级的图像编辑器对话框中的指针。|  
  
##  <a name="getmode"></a>CMFCImagePaintArea::GetMode  
 检索当前绘图模式。  
  
```  
IMAGE_EDIT_MODE GetMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 [IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值，该值指定当前绘图模式。  
  
##  <a name="setbitmap"></a>CMFCImagePaintArea::SetBitmap  
 设置图片区域的位图图像。  
  
```  
void SetBitmap(CBitmap* pBitmap);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `pBitmap`|要显示的新位图图像。|  
  
### <a name="remarks"></a>备注  
 如果`pBitmap`是`NULL`，此方法将可修改绘制区域的大小设置为零。 否则，它将可修改绘制区域的大小设置为提供的位图图像的大小。  
  
##  <a name="setcolor"></a>CMFCImagePaintArea::SetColor  
 设置当前绘图的颜色。  
  
```  
void SetColor(COLORREF color);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `color`|新的绘图颜色。|  
  
### <a name="remarks"></a>备注  
 当从图像编辑器调色板栏中选择一种颜色或颜色选取器，该框架调用此方法以更新当前绘制颜色。 初始绘图的颜色为黑色 (`COLORREF`值为 0)。  
  
 绘图的颜色由图像编辑器对话框中用于所有绘图模式下，除`IMAGE_EDIT_MODE_COLOR`。 关于绘图模式的详细信息，请参阅[cmfcimagepaintarea:: Image_edit_mode 枚举](cmfcimagepaintarea-image-edit-mode-enumeration.md)。  
  
##  <a name="setmode"></a>CMFCImagePaintArea::SetMode  
 设置当前绘图模式。  
  
```  
void SetMode(IMAGE_EDIT_MODE mode);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `mode`|[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)值，该值指定当前绘图模式。|  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog 类](../../mfc/reference/cmfcimageeditordialog-class.md)

