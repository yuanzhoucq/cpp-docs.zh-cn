---
title: CMFCPropertyGridFileProperty 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2b123b5c473c834e958263edb926ef25103d788
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty 类
`CMFCPropertyGridFileProperty`类支持打开文件选择对话框中的属性列表控件项。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|构造 `CMFCPropertyGridFileProperty` 对象。|  
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCPropertyGridFileProperty::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|`CMFCPropertyGridFileProperty::OnClickButton`|(重写[cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|  
  
### <a name="remarks"></a>备注  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)  
  
 [CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxpropertygridctrl.h  
  
##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty  
 构造 `CMFCPropertyGridFileProperty` 对象。  
  
```  
CMFCPropertyGridFileProperty(
    const CString& strName,  
    BOOL bOpenFileDialog,  
    const CString& strFileName,  
    LPCTSTR lpszDefExt=NULL,  
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,  
    LPCTSTR lpszFilter=NULL,  
    LPCTSTR lpszDescr=NULL,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>参数  
 [in] `strName`  
 属性名称。  
  
 [in] `bOpenFileDialog`  
 `TRUE` 若要打开**打开文件**对话框;`FALSE`以打开**保存文件**对话框。  
  
 [in] `strFileName`  
 初始文件名。  
  
 [in] `lpszDefExt`  
 一个或多个文件扩展名字符串。 默认值为 `NULL`。  
  
 [in] `dwFlags`  
 对话框标志。 默认值是 `OFN_HIDEREADONLY` 和 `OFN_OVERWRITEPROMPT` 的按位组合 (OR)。  
  
 [in] `lpszFilter`  
 一个或多个文件筛选器的字符串。 默认值为 `NULL`。  
  
 [in] `lpszDescr`  
 属性项说明。 默认值为 `NULL`。  
  
 [in] `dwData`  
 与属性项相关联的特定于应用程序的数据。 例如，32 位整数或与指向其他数据的指针。 默认值为 0。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 有关可用标志的完整列表，请参阅[OPENFILENAME 结构](https://msdn.microsoft.com/library/ms646839.aspx)。  
  
### <a name="example"></a>示例  
 以下示例演示如何使用 `CMFCPropertyGridFileProperty` 类的构造函数创建对象。 此示例摘自[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl 类](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty 类](../../mfc/reference/cmfcpropertygridproperty-class.md)
