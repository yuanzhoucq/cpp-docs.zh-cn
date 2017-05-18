---
title: "CDragListBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
dev_langs:
- C++
helpviewer_keywords:
- drag list box [C++]
- dragging list items
- CDragListBox class
- Windows [C++], list boxes
- list boxes
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 3010fd9a363aa1ca1c946a6fe967a7ba415649d4
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cdraglistbox-class"></a>CDragListBox 类
除了提供 Windows 列表框中，功能`CDragListBox`类允许用户在列表框内移动文件名等列表框项。  
  
## <a name="syntax"></a>语法  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|构造 `CDragListBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|拖动操作开始时由框架调用。|  
|[CDragListBox::CancelDrag](#canceldrag)|在取消拖动操作时由框架调用。|  
|[CDragListBox::Dragging](#dragging)|在拖动操作期间由框架调用。|  
|[CDragListBox::DrawInsert](#drawinsert)|绘制拖动列表框中的插入参考线。|  
|[CDragListBox::Dropped](#dropped)|由框架调用后丢弃该项。|  
|[CDragListBox::ItemFromPt](#itemfrompt)|返回所拖动的项的坐标。|  
  
## <a name="remarks"></a>备注  
 借助这项功能的列表框允许用户在列表中以任何方式对他们最有用的项进行排序。 默认情况下，列表框中将这些项移至列表中的新位置。 但是，`CDragListBox`对象可以进行自定义复制而不是将其移动的项。  
  
 列表框控件与`CDragListBox`类必须没有**LBS_SORT**或**LBS_MULTIPLESELECT**样式。 列表框样式的说明，请参阅[列表框样式](../../mfc/reference/list-box-styles.md)。  
  
 若要使用您的应用程序的现有对话框中的拖动列表框，将列表框控件添加到您使用对话框编辑器的对话框模板，并将成员变量 (类别的`Control`和变量类型`CDragListBox`) 对应于列表框控件在对话框模板中。  
  
 将控件分配给成员变量的详细信息，请参阅[为对话框控件定义成员变量的快捷方式](../../windows/defining-member-variables-for-dialog-controls.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="begindrag"></a>CDragListBox::BeginDrag  
 由框架在事件发生时无法开始拖动操作，例如，按下鼠标左键。  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含要拖动的项的坐标。  
  
### <a name="return-value"></a>返回值  
 如果拖动允许，否则为 0，非零值。  
  
### <a name="remarks"></a>备注  
 如果您想要控制在拖动操作开始时，会发生什么情况，重写此函数。 默认实现捕获到鼠标，并保留在拖动模式，直到用户单击鼠标左键或右键按钮或按 esc 键，此时取消拖放操作。  
  
##  <a name="canceldrag"></a>CDragListBox::CancelDrag  
 在取消拖动操作时由框架调用。  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含要拖动的项的坐标。  
  
### <a name="remarks"></a>备注  
 重写此函数来处理您的列表框控件的任何特殊处理。  
  
##  <a name="cdraglistbox"></a>CDragListBox::CDragListBox  
 构造 `CDragListBox` 对象。  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>CDragListBox::Dragging  
 在拖动列表框项，则由框架调用`CDragListBox`对象。  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含 x 和 y 屏幕坐标表示的光标。  
  
### <a name="return-value"></a>返回值  
 要显示的光标资源 ID。 可能的值如下︰  
  
- `DL_COPYCURSOR`指示要复制该项目。  
  
- `DL_MOVECURSOR`指示将移动该项目。  
  
- `DL_STOPCURSOR`表示当前的拖放目标不是可接受。  
  
### <a name="remarks"></a>备注  
 默认行为返回`DL_MOVECURSOR`。 如果你想要提供其他功能，重写此函数。  
  
##  <a name="drawinsert"></a>CDragListBox::DrawInsert  
 由框架来绘制插入指南与所指示的索引项之前调用。  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 在插入点的从零开始索引。  
  
### <a name="remarks"></a>备注  
 值为-1 清除插入指南。 重写此函数可修改的外观或行为插入指南。  
  
##  <a name="dropped"></a>CDragListBox::Dropped  
 在删除某项时由框架调用`CDragListBox`对象。  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 *nSrcIndex*  
 指定删除字符串的从零开始索引。  
  
 `pt`  
 一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含放置站点的坐标。  
  
### <a name="remarks"></a>备注  
 默认行为将列表框项和其数据复制到新位置，然后删除原始项目。 重写此函数可自定义默认行为，例如启用列表框项拖动到列表中的其他位置的副本。  
  
##  <a name="itemfrompt"></a>CDragListBox::ItemFromPt  
 调用此函数可检索列表框中项的从零开始的索引位于`pt`。  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 一个[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，它包含在列表框中点的坐标。  
  
 *bAutoScroll*  
 如果允许滚动，否则为 0，非零值。  
  
### <a name="return-value"></a>返回值  
 将列表框中项的从零开始索引。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 TSTCON](../../visual-cpp-samples.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)

