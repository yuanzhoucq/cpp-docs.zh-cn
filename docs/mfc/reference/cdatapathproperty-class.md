---
title: CDataPathProperty 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 164742ea39f92194a3354ae24a90eeff9512f59c
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335966"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty 类
实现可异步加载的 OLE 控件属性。  
  
## <a name="syntax"></a>语法  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|构造 `CDataPathProperty` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|检索与关联的异步 OLE 控件`CDataPathProperty`对象。|  
|[CDataPathProperty::GetPath](#getpath)|检索的属性的路径名。|  
|[CDataPathProperty::Open](#open)|启动加载的相关联的 ActiveX (OLE) 控件的异步属性。|  
|[CDataPathProperty::ResetData](#resetdata)|调用`CAsyncMonikerFile::OnDataAvailable`通知的控件属性已更改的容器。|  
|[CDataPathProperty::SetControl](#setcontrol)|设置与属性关联的异步 ActiveX (OLE) 控件。|  
|[CDataPathProperty::SetPath](#setpath)|设置该属性的路径名。|  
  
## <a name="remarks"></a>备注  
 可以在同步启动之后加载异步属性。  
  
 该类`CDataPathProperty`派生自`CAysncMonikerFile`。 若要在 OLE 控件中实现异步属性，从派生类`CDataPathProperty`，并重写[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。  
  
 有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息，请参阅以下文章：  
  
- [Internet 前几个步骤： ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)  
  
- [异步名字对象 Internet 前几个步骤：](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>要求  
 **标头：** afxctl.h  
  
##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty  
 构造 `CDataPathProperty` 对象。  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pControl*  
 指向要与此相关联的 OLE 控件对象的指针`CDataPathProperty`对象。  
  
 *lpszPath*  
 路径可以是绝对或相对，用于创建异步名字对象引用的属性的实际绝对位置。 `CDataPathProperty` 使用 Url，不是文件名。 如果你想`CDataPathProperty`对象的文件，请在前面添加`file://`到路径。  
  
### <a name="remarks"></a>备注  
 `COleControl`指向对象*pControl*由`Open`和派生类来检索。 如果*pControl*为 NULL，与所使用的控件`Open`应与设置`SetControl`。 如果*lpszPath*为 NULL，可以在路径中，通过传递`Open`或将其与设置`SetPath`。  
  
##  <a name="getcontrol"></a>  CDataPathProperty::GetControl  
 调用此成员函数以检索`COleControl`对象与关联`CDataPathProperty`对象。  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>返回值  
 返回指向 OLE 控件的关联与`CDataPathProperty`对象。 为 NULL，如果不是控件都相关联。  
  
##  <a name="getpath"></a>  CDataPathProperty::GetPath  
 调用此成员函数可检索的路径，设置何时`CDataPathProperty`对象已构造的或在指定`Open`，或上一个调用中指定`SetPath`成员函数。  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回到该属性本身的路径名。 可以为空，如果不指定任何路径。  
  
##  <a name="open"></a>  CDataPathProperty::Open  
 调用此成员函数以启动加载的关联控件的异步属性。  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pControl*  
 指向要与此相关联的 OLE 控件对象的指针`CDataPathProperty`对象。  
  
 *pError*  
 指向文件异常的指针。 发生错误时将设置的原因。  
  
 *lpszPath*  
 路径可以是绝对或相对，用于创建异步名字对象引用的属性的实际绝对位置。 `CDataPathProperty` 使用 Url，不是文件名。 如果你想`CDataPathProperty`对象的文件，请在前面添加`file://`到路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该函数尝试获取`IBindHost`从控件的接口。  
  
 然后再调用`Open`不使用路径，该属性的路径的值必须设置。 这可以构造，或通过调用对象时`SetPath`成员函数。  
  
 然后再调用`Open`不控制 ActiveX 控件 （以前称为 OLE 控件） 可以与对象相关联。 这可以构造，或通过调用对象时`SetControl`。  
  
 所有重载[CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open)此外，还提供从`CDataPathProperty`。  
  
##  <a name="resetdata"></a>  CDataPathProperty::ResetData  
 调用此函数可获取`CAsyncMonikerFile::OnDataAvailable`以通知容器的控件属性已更改，并以异步方式加载的所有信息都将不再有用。  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>备注  
 打开应重新启动。 派生的类可以重写此函数以使用不同的默认值。  
  
##  <a name="setcontrol"></a>  CDataPathProperty::SetControl  
 调用此成员函数将使用异步 OLE 控件相关联`CDataPathProperty`对象。  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>参数  
 *pControl*  
 指向要与属性相关联的异步 OLE 控件的指针。  
  
##  <a name="setpath"></a>  CDataPathProperty::SetPath  
 调用此成员函数可设置的属性的路径名。  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>参数  
 *lpszPath*  
 路径，它可以是绝对或相对的以异步方式加载的属性。 `CDataPathProperty` 使用 Url，不是文件名。 如果你想`CDataPathProperty`对象的文件，请在前面添加`file://`到路径。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例图像](../../visual-cpp-samples.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)
