---
title: "CMFCToolBarInfo 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarInfo class
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: 22
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
ms.openlocfilehash: a9e66ffa0b5a751a7e5711ed20927a6adcede45d
ms.lasthandoff: 02/24/2017

---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo 类
包含处于不同状态的工具栏图像的资源 ID。 `CMFCToolBarInfo`是用作参数的帮助器类[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>成员  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|包含正则 （冷） 的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|包含已禁用的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|包含所选 （热） 的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|包含的大型、 常规的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|资源 ID 的工具栏位图，其中包含很大，禁用的工具栏图像。|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|包含大、 所选的工具栏图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|包含禁用的菜单图像的工具栏位图的资源 ID。|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|包含菜单图像的工具栏位图的资源 ID。|  
  
## <a name="remarks"></a>备注  
 完整工具栏位图包含，它具有固定大小的小型的工具栏图像 （按钮）。 存储在每个资源 ID`CMFCToolBarInfo`对象是包含一套完整的 （如示例中，选择、 已禁用大或菜单的图像） 的单个状态中的工具栏图像的位图。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtoolbar.h  
  
##  <a name="a-namemuicoldresida--cmfctoolbarinfomuicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID  
 指定的工具栏上的所有常规按钮图像的资源 ID。  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="a-namemuidisabledresida--cmfctoolbarinfomuidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID  
 指定工具栏的按钮不可用的图像的资源 ID。  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="a-namemuihotresida--cmfctoolbarinfomuihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID  
 指定的工具栏上的所有突出显示的按钮图像的资源 ID。  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="a-namemuilargecoldresida--cmfctoolbarinfomuilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID  
 指定的工具栏上的所有大型的常规按钮图像的资源 ID。  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="a-namemuilargedisabledresida--cmfctoolbarinfomuilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID  
 指定的工具栏上的所有大型的禁用的按钮图像的资源 ID。  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="a-namemuilargehotresida--cmfctoolbarinfomuilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID  
 指定的工具栏上的所有大突出显示图像的资源 ID。  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="a-namemuimenudisabledresida--cmfctoolbarinfomuimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID  
 指定工具栏的命令不可用的图像的资源 ID。  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="a-namemuimenuresida--cmfctoolbarinfomuimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID  
 指定工具栏的所有正则菜单项图像的资源 ID。  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)

