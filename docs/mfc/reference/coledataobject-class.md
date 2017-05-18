---
title: "COleDataObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
dev_langs:
- C++
helpviewer_keywords:
- drag and drop [C++], MFC support
- Clipboard [C++], OLE support
- uniform data transfer
- OLE [C++], uniform data transfer
- Clipboard [C++], MFC support
- OLE Clipboard [C++], support
- IDataObject interface, MFC encapsulation
- data transfer [C++]
- data transfer [C++], OLE
- OLE data transfer [C++]
- COleDataObject class
- uniform data transfer, OLE
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: 20
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f30ca208252fe81f1e47d9e8f817cb9137656540
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="coledataobject-class"></a>COleDataObject 类
在数据传输中用于从剪贴板、通过拖放或从嵌入 OLE 项检索各种格式的数据。  
  
## <a name="syntax"></a>语法  
  
```  
class COleDataObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleDataObject::COleDataObject](#coledataobject)|构造 `COleDataObject` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleDataObject::Attach](#attach)|将附加到指定的 OLE 数据对象`COleDataObject`。|  
|[COleDataObject::AttachClipboard](#attachclipboard)|将附加到剪贴板上的数据对象。|  
|[COleDataObject::BeginEnumFormats](#beginenumformats)|准备一个或更多后续`GetNextFormat`调用。|  
|[COleDataObject::Detach](#detach)|分离关联`IDataObject`对象。|  
|[COleDataObject::GetData](#getdata)|将数据从指定的格式中的附加 OLE 数据对象。|  
|[COleDataObject::GetFileData](#getfiledata)|将数据复制到此附加 OLE 数据对象中`CFile`中指定的格式的指针。|  
|[COleDataObject::GetGlobalData](#getglobaldata)|将数据复制到此附加 OLE 数据对象中`HGLOBAL`中指定的格式。|  
|[COleDataObject::GetNextFormat](#getnextformat)|返回的下一步的数据格式。|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|检查数据是否在指定的格式中可用。|  
|[COleDataObject::Release](#release)|分离，并释放关联`IDataObject`对象。|  
  
## <a name="remarks"></a>备注  
 `COleDataObject`没有基类的类。  
  
 这些类型的数据传输包括源和目标。 数据源实现的对象为[COleDataSource](../../mfc/reference/coledatasource-class.md)类。 只要目标应用程序已在其中放置的数据或需要从剪贴板的对象执行粘贴操作`COleDataObject`必须创建的类。  
  
 此类使您能够确定数据是否存在指定的格式。 您可以还枚举可用的数据格式或检查给定的格式是否可用，然后检索中的首选格式的数据。 检索对象的操作可以完成几种不同方式，包括使用[CFile](../../mfc/reference/cfile-class.md)、 `HGLOBAL`，或**STGMEDIUM**结构。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关在您的应用程序中使用数据对象的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `COleDataObject`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="attach"></a>COleDataObject::Attach  
 调用此函数可将相关联`COleDataObject`具有 OLE 数据对象的对象。  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *lpDataObject*  
 指向以 OLE 数据对象。  
  
 `bAutoRelease`  
 **TRUE**如果应 OLE 数据对象时释放`COleDataObject`对象被销毁; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="attachclipboard"></a>COleDataObject::AttachClipboard  
 调用此函数可将附加到剪贴板上的当前数据对象`COleDataObject`对象。  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  调用此函数将锁定剪贴板，直至发布此数据对象。 中的析构函数释放的数据对象`COleDataObject`。 有关详细信息，请参阅[打开剪贴板](http://msdn.microsoft.com/library/windows/desktop/ms649048)和[关闭剪贴板](http://msdn.microsoft.com/library/windows/desktop/ms649035)Win32 文档中。  
  
##  <a name="beginenumformats"></a>COleDataObject::BeginEnumFormats  
 调用此函数准备以便后续调用`GetNextFormat`从该项中检索的数据格式的列表。  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>备注  
 在调用`BeginEnumFormats`，存储此数据对象支持的第一种格式的位置。 对连续调用`GetNextFormat`将枚举数据对象中的可用格式的列表。  
  
 若要检查给定格式的数据的可用性，请使用[COleDataObject::IsDataAvailable](#isdataavailable)。  
  
 有关详细信息，请参阅[IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="coledataobject"></a>COleDataObject::COleDataObject  
 构造 `COleDataObject` 对象。  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>备注  
 调用[COleDataObject::Attach](#attach)或[COleDataObject::AttachClipboard](#attachclipboard)调用其他前必须保持`COleDataObject`函数。  
  
> [!NOTE]
>  由于对拖放处理程序的参数之一是一个指向`COleDataObject`，无需调用此构造函数来支持拖放。  
  
##  <a name="detach"></a>COleDataObject::Detach  
 调用此函数可分离`COleDataObject`与其关联的 OLE 数据对象，而不释放数据对象中的对象。  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向已分离的 OLE 数据对象的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdata"></a>COleDataObject::GetData  
 调用此函数可从指定的格式项中检索数据。  
  
```  
BOOL GetData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 是用要返回的数据格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpStgMedium`  
 指向[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)将接收数据的结构。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述是用来返回数据的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用的默认值**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getfiledata"></a>COleDataObject::GetFileData  
 调用此函数可创建`CFile`或`CFile`-派生的对象和检索到指定的格式中的数据`CFile`指针。  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 是用要返回的数据格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述是用来返回数据的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用的默认值**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 指向新`CFile`或`CFile`-派生的对象包含的数据，如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 指向返回的值的实际类型可能是具体取决于数据存储在介质， `CFile`， `CSharedFile`，或`COleStreamFile`。  
  
> [!NOTE]
>  `CFile`由调用方拥有访问此函数的返回值的对象。 它负责调用方引导到**删除**`CFile`对象，从而关闭文件。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getglobaldata"></a>COleDataObject::GetGlobalData  
 调用此函数以分配全局内存块，检索到指定的格式中的数据`HGLOBAL`。  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 是用要返回的数据格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述是用来返回数据的格式。 为此参数提供一个值，如果您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用的默认值**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 包含的数据，如果成功，则全局内存块的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getnextformat"></a>COleDataObject::GetNextFormat  
 调用此函数重复以获取可用于从该项目中检索数据的所有格式。  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构，它将在函数调用返回时收到格式信息。  
  
### <a name="return-value"></a>返回值  
 如果另一种格式是可用，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 在调用[COleDataObject::BeginEnumFormats](#beginenumformats)，存储此数据对象支持的第一种格式的位置。 对连续调用`GetNextFormat`将枚举数据对象中的可用格式的列表。 使用这些函数可以列出了可用的格式。  
  
 若要检查给定格式的可用性，请调用[COleDataObject::IsDataAvailable](#isdataavailable)。  
  
 有关详细信息，请参阅[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="isdataavailable"></a>COleDataObject::IsDataAvailable  
 调用此函数可确定特定的格式是否可用于从 OLE 项检索数据。  
  
```  
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 指向要在结构中使用的剪贴板数据格式`lpFormatEtc`。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构的结构描述所需的格式。 为此参数提供一个值，仅当您想要指定所指定的剪贴板格式之外的格式的其他信息`cfFormat`。 如果它是**NULL**，对于其他字段中使用的默认值**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 非零，如果数据中指定的格式;否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数十分有用之前调用`GetData`， `GetFileData`，或`GetGlobalData`。  
  
 有关详细信息，请参阅[IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)。  
  
##  <a name="release"></a>COleDataObject::Release  
 调用此函数可释放的所有权[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)以前与相关联的对象`COleDataObject`对象。  
  
```  
void Release();
```  
  
### <a name="remarks"></a>备注  
 `IDataObject`关联`COleDataObject`通过调用**附加**或`AttachClipboard`显式或框架。 如果`bAutoRelease`参数**附加**是**FALSE**、`IDataObject`对象并不会释放。 在这种情况下，调用方负责释放`IDataObject`通过调用[iunknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDataSource 类](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)

