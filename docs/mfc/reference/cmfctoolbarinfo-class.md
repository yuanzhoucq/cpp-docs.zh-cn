---
title: CMFCToolBarInfo 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de968fe53348b4cfa3f46e999da37cdca6f88c90
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo 类
包含处于不同状态的工具栏图像的资源 ID。 `CMFCToolBarInfo` 是用作参数的帮助器类[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>成员  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|用于包含正则 （冷） 的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|用于包含禁用的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|用于包含所选 （热） 工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|用于包含大型、 正则工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|包含大，工具栏位图的资源 ID 禁用工具栏图像。|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|用于包含大型、 所选的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|用于包含禁用的菜单图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|用于包含菜单图像的工具栏位图的资源 ID。|  
  
## <a name="remarks"></a>备注  
 完整的工具栏位图包含，它具有固定大小的小工具栏图像 （按钮）。 存储在每个资源 ID`CMFCToolBarInfo`对象是包含一套完整的单个状态 （用于示例中，选择、 已禁用、 大，或菜单图像） 中的工具栏图像的位图。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxtoolbar.h  
  
##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID  
 指定的工具栏上的所有常规按钮图像的资源 ID。  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID  
 指定一个工具栏按钮不可用图像的资源 ID。  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID  
 指定的工具栏上的所有突出显示的按钮图像的资源 ID。  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID  
 指定的一个工具栏的所有大常规按钮图像的资源 ID。  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID  
 指定的一个工具栏的所有大的禁用的按钮图像的资源 ID。  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID  
 指定的工具栏上的所有大突出显示图像的资源 ID。  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID  
 指定的命令不可用的工具栏图像的资源 ID。  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID  
 指定的工具栏上的所有常规菜单项图像的资源 ID。  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
