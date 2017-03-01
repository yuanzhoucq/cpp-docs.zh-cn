---
title: "CMFCRibbonButtonsGroup 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonButtonsGroup
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonButtonsGroup class
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
caps.latest.revision: 34
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2d8909ca63bd1d9121e1126d46a08312521cc4ac
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonbuttonsgroup-class"></a>CMFCRibbonButtonsGroup 类
`CMFCRibbonButtonsGroup`类使您可以将一组功能区按钮组织到组。 组中的所有按钮在水平位置上直接彼此相邻并位于边框中。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|构造 `CMFCRibbonButtonsGroup` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|向组中添加一个按钮。|  
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|向组中添加按钮的列表。|  
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|返回一个指针，到位于指定索引处的按钮。|  
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|返回组中的按钮数。|  
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|返回功能区组中的普通图像的图像大小 (重写[CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize)。)|  
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|返回功能区元素的常规大小 (重写[CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize)。)|  
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|报告是否`CMFCRibbonButtonsGroup`对象包含的工具栏图像。|  
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|绘制指定的按钮，具体取决于该按钮是否正常，突出显示或已禁用的相应映像。|  
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|删除所有按钮从`CMFCRibbonButtonsGroup`对象。|  
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|将图像分配给组。|  
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|设置父`CMFCRibbonCategory`的`CMFCRibbonButtonsGroup`对象，并在其中的所有按钮 (将重写[CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory)。)|  
  
## <a name="remarks"></a>备注  
 组派生自[CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md)可以作为单个实体进行操作。 您可以在任何面板或弹出菜单上定位组。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCRibbonButtonsGroup`类。 该示例演示如何构造`CMFCRibbonButtonsGroup`对象、 将图像分配给功能区按钮组并向功能区按钮的组添加一个按钮。 此代码段属于[绘制客户端示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&2;](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxribbonbuttonsgroup.h  
  
##  <a name="a-nameaddbuttona--cmfcribbonbuttonsgroupaddbutton"></a><a name="addbutton"></a>CMFCRibbonButtonsGroup::AddButton  
 向组中添加一个按钮。  
  
```  
void AddButton(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
 指向一个按钮来添加的指针。  
  
##  <a name="a-nameaddbuttonsa--cmfcribbonbuttonsgroupaddbuttons"></a><a name="addbuttons"></a>CMFCRibbonButtonsGroup::AddButtons  
 向组中添加按钮的列表。  
  
```  
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```  
  
### <a name="parameters"></a>参数  
 [in] `lstButtons`  
 指向您想要添加的按钮的指针的列表。  
  
##  <a name="a-namecmfcribbonbuttonsgroupa--cmfcribbonbuttonsgroupcmfcribbonbuttonsgroup"></a><a name="cmfcribbonbuttonsgroup"></a>CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup  
 构造 `CMFCRibbonButtonsGroup` 对象。  
  
```  
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
 指定用于添加对新创建的按钮`CMFCRibbonButtonsGroup`对象。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetbuttona--cmfcribbonbuttonsgroupgetbutton"></a><a name="getbutton"></a>CMFCRibbonButtonsGroup::GetButton  
 返回一个指针，到位于指定索引处的按钮。  
  
```  
CMFCRibbonBaseElement* GetButton(int i) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `i`  
 按钮以返回一个从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 一个指向位于指定索引处的按钮。 `NULL`如果指定的索引超出范围。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetcounta--cmfcribbonbuttonsgroupgetcount"></a><a name="getcount"></a>CMFCRibbonButtonsGroup::GetCount  
 返回组中的按钮数。  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 组中的按钮数。  
  
##  <a name="a-namegetimagesizea--cmfcribbonbuttonsgroupgetimagesize"></a><a name="getimagesize"></a>CMFCRibbonButtonsGroup::GetImageSize  
 检索受保护的源映像大小`CMFCToolBarImages`成员`m_Images`。  
  
```  
const CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果存在，或返回的工具栏图像，图像大小`CSize`的如果不为零。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetregularsizea--cmfcribbonbuttonsgroupgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonButtonsGroup::GetRegularSize  
 检索的功能区组元素的最大可能大小。  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 功能区组的设备上下文的指针。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namehasimagesa--cmfcribbonbuttonsgrouphasimages"></a><a name="hasimages"></a>CMFCRibbonButtonsGroup::HasImages  
 报告是否`CMFCRibbonButtonsGroup`对象包含的工具栏图像。  
  
```  
BOOL HasImages() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果返回 TRUE 的受保护`CMFCToolBarImages`成员`m_Images`不包含任何图像或 false。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawimagea--cmfcribbonbuttonsgroupondrawimage"></a><a name="ondrawimage"></a>CMFCRibbonButtonsGroup::OnDrawImage  
 绘制指定的按钮，具体取决于该按钮是否正常，突出显示或已禁用的相应映像。  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rectImage,  
    CMFCRibbonBaseElement* pButton,  
    int nImageIndex);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针`CMFCRibbonButtonsGroup`对象。  
  
 [in] `rectImage`  
 在其中绘制图像的矩形。  
  
 [in] `pButton`  
 若要绘制图像的按钮。  
  
 [in] `nImageIndex`  
 （在一个正常、 突出显示或已禁用按钮以及三个图像数组） 的按钮上绘制的图像的索引。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameremovealla--cmfcribbonbuttonsgroupremoveall"></a><a name="removeall"></a>CMFCRibbonButtonsGroup::RemoveAll  
 删除所有按钮从`CMFCRibbonButtonsGroup`对象。  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetimagesa--cmfcribbonbuttonsgroupsetimages"></a><a name="setimages"></a>CMFCRibbonButtonsGroup::SetImages  
 将图像分配给功能区按钮的组。  
  
```  
void SetImages(
    CMFCToolBarImages* pImages,  
    CMFCToolBarImages* pHotImages,  
    CMFCToolBarImages* pDisabledImages);
```  
  
### <a name="parameters"></a>参数  
 [in] `pImages`  
 常规映像。  
  
 [in] `pHotImages`  
 热的图像。  
  
 [in] `pDisabledImages`  
 已禁用的图像。  
  
### <a name="remarks"></a>备注  
 调用`SetImages`将按钮添加到组之前。 映像的数目必须大于或等于要添加到组的按钮数。  
  
> [!NOTE]
>  热映像是当用户悬停在按钮上时显示的图像。 已禁用的图像是按钮被禁用时，将显示的图像。  
  
##  <a name="a-namesetparentcategorya--cmfcribbonbuttonsgroupsetparentcategory"></a><a name="setparentcategory"></a>CMFCRibbonButtonsGroup::SetParentCategory  
 设置父`CMFCRibbonCategory`的`CMFCRibbonButtonsGroup`对象，并在其中的所有按钮。  
  
```  
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```  
  
### <a name="parameters"></a>参数  
 [in] `pCategory`  
 指向要设置的父类别 （功能区控件中的选项卡式的组被称为类别）。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)

