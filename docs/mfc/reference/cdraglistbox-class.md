---
title: "CDragListBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 424d9db088aa171bdbca868326eb80144a10704b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cdraglistbox-class"></a>CDragListBox 类
除了提供 Windows 列表框，功能`CDragListBox`类允许用户在列表框内移动文件名等列表框项。  
  
## <a name="syntax"></a>语法  
  
```  
class CDragListBox : public CListBox  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDragListBox::CDragListBox](#cdraglistbox)|构造 `CDragListBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDragListBox::BeginDrag](#begindrag)|拖动操作开始时，由框架调用。|  
|[CDragListBox::CancelDrag](#canceldrag)|已取消拖动操作时，由框架调用。|  
|[CDragListBox::Dragging](#dragging)|在拖动操作期间由框架调用。|  
|[CDragListBox::DrawInsert](#drawinsert)|绘制拖列表框的插入参考线。|  
|[CDragListBox::Dropped](#dropped)|已丢弃该项后，由框架调用。|  
|[CDragListBox::ItemFromPt](#itemfrompt)|返回要拖动的项的坐标。|  
  
## <a name="remarks"></a>备注  
 使用这项功能的列表框允许用户在任何方式是对他们最有用的列表中的项进行排序。 默认情况下，列表框中将这些项移至列表中的新位置。 但是，`CDragListBox`对象可以进行自定义项而不是将它们复制。  
  
 列表框控件与`CDragListBox`类必须没有**LBS_SORT**或**LBS_MULTIPLESELECT**样式。 列表框样式的说明，请参阅[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)。  
  
 若要使用你的应用程序的一个现有的对话框中的拖列表框，将列表框控件添加到对话框模板使用对话框编辑器，并将成员变量 (类别的`Control`和变量类型`CDragListBox`) 对应于列表框在对话框模板中控制。  
  
 将控件分配给成员变量的详细信息，请参阅[对话框控件定义成员变量的快捷方式](../../windows/defining-member-variables-for-dialog-controls.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CDragListBox`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxcmn.h  
  
##  <a name="begindrag"></a>CDragListBox::BeginDrag  
 由框架事件发生时无法开始拖动操作，如按鼠标左键。  
  
```  
virtual BOOL BeginDrag(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含要拖动的项的坐标。  
  
### <a name="return-value"></a>返回值  
 如果拖动允许，否则为 0，则为非 0。  
  
### <a name="remarks"></a>备注  
 如果你想要控制拖动操作开始时，会发生什么情况，重写此函数。 默认实现捕获鼠标，并保留在拖动模式，直到用户单击左或向右鼠标按钮或按的 ESC，此时取消拖放操作。  
  
##  <a name="canceldrag"></a>CDragListBox::CancelDrag  
 已取消拖动操作时，由框架调用。  
  
```  
virtual void CancelDrag(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含要拖动的项的坐标。  
  
### <a name="remarks"></a>备注  
 重写此函数可处理你的列表框控件的任何特殊处理。  
  
##  <a name="cdraglistbox"></a>CDragListBox::CDragListBox  
 构造 `CDragListBox` 对象。  
  
```  
CDragListBox();
```  
  
##  <a name="dragging"></a>CDragListBox::Dragging  
 正在将列表框项拖内时由框架调用`CDragListBox`对象。  
  
```  
virtual UINT Dragging(CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含 x 和 y 屏幕坐标表示的光标。  
  
### <a name="return-value"></a>返回值  
 要显示的光标资源 ID。 还可能有以下值：  
  
- `DL_COPYCURSOR`指示将复制该项目。  
  
- `DL_MOVECURSOR`指示将移动该项目。  
  
- `DL_STOPCURSOR`指示当前的拖放目标不是可接受。  
  
### <a name="remarks"></a>备注  
 默认行为返回`DL_MOVECURSOR`。 如果你想要提供其他功能，重写此函数。  
  
##  <a name="drawinsert"></a>CDragListBox::DrawInsert  
 由框架调用以绘制指示索引的项之前插入参考线。  
  
```  
virtual void DrawInsert(int nItem);
```  
  
### <a name="parameters"></a>参数  
 `nItem`  
 在插入点的从零开始索引。  
  
### <a name="remarks"></a>备注  
 值为-1 清除插入参考线。 重写此函数可修改的外观或行为插入参考线。  
  
##  <a name="dropped"></a>CDragListBox::Dropped  
 在删除项时，由框架调用`CDragListBox`对象。  
  
```  
virtual void Dropped(
    int nSrcIndex,  
    CPoint pt);
```  
  
### <a name="parameters"></a>参数  
 *nSrcIndex*  
 指定删除字符串的从零开始的索引。  
  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)包含放置站点的坐标的对象。  
  
### <a name="remarks"></a>备注  
 默认行为将列表框项和其数据复制到新位置，然后删除原始的项目。 重写此函数可自定义的默认行为，例如启用列表框项拖动到列表中其他位置的副本。  
  
##  <a name="itemfrompt"></a>CDragListBox::ItemFromPt  
 调用此函数可检索的列表框项的从零开始的索引位于`pt`。  
  
```  
int ItemFromPt(
    CPoint pt,  
    BOOL bAutoScroll = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 `pt`  
 A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)对象，其中包含在列表框中点的坐标。  
  
 *bAutoScroll*  
 如果滚动允许，否则为 0，则为非 0。  
  
### <a name="return-value"></a>返回值  
 将列表框项的从零开始索引。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 TSTCON](../../visual-cpp-samples.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)
