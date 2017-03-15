---
title: "CDataPathProperty 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataPathProperty
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- OLE controls [C++], asynchronous
- CDataPathProperty class
- asynchronous controls [C++]
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d767cf950d8b86959aadc2fd4d77401134a6dc75
ms.lasthandoff: 02/24/2017

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
|[CDataPathProperty::GetPath](#getpath)|检索此属性的路径名。|  
|[CDataPathProperty::Open](#open)|启动加载相关联的 ActiveX (OLE) 控件的异步属性。|  
|[CDataPathProperty::ResetData](#resetdata)|调用`CAsyncMonikerFile::OnDataAvailable`以通知容器控件属性已更改。|  
|[CDataPathProperty::SetControl](#setcontrol)|设置与属性关联的异步的 ActiveX (OLE) 控制。|  
|[CDataPathProperty::SetPath](#setpath)|设置该属性的路径名。|  
  
## <a name="remarks"></a>备注  
 可以在同步启动之后加载异步属性。  
  
 此类`CDataPathProperty`派生自**CAysncMonikerFile**。 若要在 OLE 控件中实现异步属性，从派生类`CDataPathProperty`，并重写[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。  
  
 有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息，请参阅以下文章︰  
  
- [Internet 前几个步骤︰ ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet 前几个步骤︰ 异步名字对象](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxctl.h  
  
##  <a name="a-namecdatapathpropertya--cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty  
 构造 `CDataPathProperty` 对象。  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 指向要与此相关联的 OLE 控件对象的指针`CDataPathProperty`对象。  
  
 `lpszPath`  
 路径，这可能是绝对值或相对值，用来创建异步名字对象引用的属性的实际绝对位置。 `CDataPathProperty`使用 Url，不是文件名。 如果您希望`CDataPathProperty`对象的文件，请在前面添加`file://`到路径。  
  
### <a name="remarks"></a>备注  
 `COleControl`指向对象`pControl`由**打开**并检索由派生类。 如果`pControl`是**NULL**，与所使用的控件**打开**应与设置`SetControl`。 如果`lpszPath`是**NULL**，可以在路径中，通过传递**打开**或其设置了`SetPath`。  
  
##  <a name="a-namegetcontrola--cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>CDataPathProperty::GetControl  
 调用此成员函数以检索`COleControl`与关联对象`CDataPathProperty`对象。  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>返回值  
 返回指向 OLE 控件的指针与关联`CDataPathProperty`对象。 **NULL**如果不控件相关联。  
  
##  <a name="a-namegetpatha--cdatapathpropertygetpath"></a><a name="getpath"></a>CDataPathProperty::GetPath  
 调用此成员函数要检索的路径，请将何时`CDataPathProperty`对象已构造的或在指定**打开**，或对上一个调用中指定`SetPath`成员函数。  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回于属性自身的路径名。 可以为空，如果不指定任何路径。  
  
##  <a name="a-nameopena--cdatapathpropertyopen"></a><a name="open"></a>CDataPathProperty::Open  
 调用该成员函数以启动加载的关联控件的异步属性。  
  
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
 `pControl`  
 指向要与此相关联的 OLE 控件对象的指针`CDataPathProperty`对象。  
  
 `pError`  
 一个指向文件例外。 发生错误时将设置的原因。  
  
 `lpszPath`  
 路径，这可能是绝对值或相对值，用来创建异步名字对象引用的属性的实际绝对位置。 `CDataPathProperty`使用 Url，不是文件名。 如果您希望`CDataPathProperty`对象的文件，请在前面添加`file://`到路径。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 函数将尝试获取`IBindHost`从控件的接口。  
  
 之前，先调用**打开**没有一个路径，该属性的路径的值必须设置。 这可在对象构造，或通过调用时`SetPath`成员函数。  
  
 之前，先调用**打开**而无需控制 ActiveX 控件 （以前称为 OLE 控件） 可以是与对象关联。 这可在对象构造，或通过调用时`SetControl`。  
  
 所有重载[CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open)还可以从中`CDataPathProperty`。  
  
##  <a name="a-nameresetdataa--cdatapathpropertyresetdata"></a><a name="resetdata"></a>CDataPathProperty::ResetData  
 调用此函数可获取`CAsyncMonikerFile::OnDataAvailable`以通知容器控件属性已更改，并以异步方式加载的所有信息都不再有用。  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>备注  
 打开，应重新启动。 派生的类可以重写此函数以使用不同的默认值。  
  
##  <a name="a-namesetcontrola--cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPathProperty::SetControl  
 调用此成员函数以将具有的异步 OLE 控件相关联`CDataPathProperty`对象。  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 指向异步的 OLE 控件，使其与属性关联的指针。  
  
##  <a name="a-namesetpatha--cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPathProperty::SetPath  
 调用此成员函数可设置该属性的路径名。  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>参数  
 `lpszPath`  
 路径，它可以是绝对或相对的到异步加载的属性。 `CDataPathProperty`使用 Url，不是文件名。 如果您希望`CDataPathProperty`对象的文件，请在前面添加`file://`到路径。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例图像](../../visual-cpp-samples.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)

