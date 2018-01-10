---
title: "COleDataObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f85a1e6992e8d679401f4e0f97080efcf991446
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[COleDataObject::BeginEnumFormats](#beginenumformats)|准备一个或多后续`GetNextFormat`调用。|  
|[COleDataObject::Detach](#detach)|分离关联`IDataObject`对象。|  
|[COleDataObject::GetData](#getdata)|将数据从指定的格式中的附加 OLE 数据对象。|  
|[COleDataObject::GetFileData](#getfiledata)|将数据复制到此附加 OLE 数据对象中`CFile`中指定的格式的指针。|  
|[COleDataObject::GetGlobalData](#getglobaldata)|将数据复制到此附加 OLE 数据对象中`HGLOBAL`中指定的格式。|  
|[COleDataObject::GetNextFormat](#getnextformat)|返回的下一步的数据格式。|  
|[COleDataObject::IsDataAvailable](#isdataavailable)|检查数据是否在指定的格式中可用。|  
|[COleDataObject::Release](#release)|分离并释放关联`IDataObject`对象。|  
  
## <a name="remarks"></a>备注  
 `COleDataObject`没有基类。  
  
 这些类型的数据传输包括源和目标。 数据源的对象作为实现[COleDataSource](../../mfc/reference/coledatasource-class.md)类。 每当目标应用程序已在其中放置的数据或要求从剪贴板的对象执行粘贴操作`COleDataObject`必须创建类。  
  
 此类使您能够确定数据是否存在指定的格式。 你可以还枚举的可用数据格式或检查给定的格式是否可用，然后检索中的首选格式的数据。 检索对象，可采用多种不同的方法，包括使用[CFile](../../mfc/reference/cfile-class.md)、 `HGLOBAL`，或**STGMEDIUM**结构。  
  
 有关详细信息，请参阅[STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) Windows SDK 中的结构。  
  
 有关应用程序中使用数据对象的详细信息，请参阅文章[数据对象和数据源 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `COleDataObject`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxole.h  
  
##  <a name="attach"></a>COleDataObject::Attach  
 调用此函数可将相关联`COleDataObject`与 OLE 数据对象的对象。  
  
```  
void Attach(
    LPDATAOBJECT lpDataObject,  
    BOOL bAutoRelease = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *lpDataObject*  
 指向 OLE 数据对象的指针。  
  
 `bAutoRelease`  
 **TRUE**如果 OLE 数据对象应为发布时`COleDataObject`对象被销毁; 否则为**FALSE**。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) Windows SDK 中。  
  
##  <a name="attachclipboard"></a>COleDataObject::AttachClipboard  
 调用此函数可将附加当前到剪贴板上的数据对象`COleDataObject`对象。  
  
```  
BOOL AttachClipboard();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
  
> [!NOTE]
>  调用此函数锁定剪贴板，直到此数据对象被释放。 中的析构函数释放的数据对象`COleDataObject`。 有关详细信息，请参阅[打开剪贴板](http://msdn.microsoft.com/library/windows/desktop/ms649048)和[CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) Win32 文档中。  
  
##  <a name="beginenumformats"></a>COleDataObject::BeginEnumFormats  
 调用此函数可准备以便后续调用`GetNextFormat`用于检索从项的数据格式的列表。  
  
```  
void BeginEnumFormats();
```  
  
### <a name="remarks"></a>备注  
 调用了`BeginEnumFormats`，存储此数据对象支持的第一个格式的位置。 对连续调用`GetNextFormat`将枚举在数据对象中的可用格式的列表。  
  
 若要检查给定格式的数据的可用性，请使用[COleDataObject::IsDataAvailable](#isdataavailable)。  
  
 有关详细信息，请参阅[IDataObject::EnumFormatEtc](http://msdn.microsoft.com/library/windows/desktop/ms683979) Windows SDK 中。  
  
##  <a name="coledataobject"></a>COleDataObject::COleDataObject  
 构造 `COleDataObject` 对象。  
  
```  
COleDataObject();
```  
  
### <a name="remarks"></a>备注  
 调用[COleDataObject::Attach](#attach)或[COleDataObject::AttachClipboard](#attachclipboard)必须在调用其他之前进行`COleDataObject`函数。  
  
> [!NOTE]
>  由于拖放处理程序的参数之一是一个指向`COleDataObject`，无需调用此构造函数，以支持拖放。  
  
##  <a name="detach"></a>COleDataObject::Detach  
 调用此函数可分离`COleDataObject`其关联的 OLE 数据对象，而不释放数据对象中的对象。  
  
```  
LPDATAOBJECT Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向已分离的 OLE 数据对象的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdata"></a>COleDataObject::GetData  
 调用此函数可从指定的格式中的项中检索数据。  
  
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
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述是用要返回数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息`cfFormat`。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[idataobject:: Getdata](http://msdn.microsoft.com/library/windows/desktop/ms678431)， [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812)，和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="getfiledata"></a>COleDataObject::GetFileData  
 调用此函数可创建`CFile`或`CFile`-派生对象并检索到指定的格式中的数据`CFile`指针。  
  
```  
CFile* GetFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 是用要返回的数据格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述是用要返回数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息`cfFormat`。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 指向新`CFile`或`CFile`-派生的对象包含的数据，如果成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 根据数据存储中的介质，指向返回的值的实际类型可能`CFile`， `CSharedFile`，或`COleStreamFile`。  
  
> [!NOTE]
>  `CFile`由调用方拥有访问通过此函数的返回值的对象。 调用方负责**删除**`CFile`对象，从而关闭文件。  
  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="getglobaldata"></a>COleDataObject::GetGlobalData  
 调用此函数可分配全局内存块并检索到指定的格式中的数据`HGLOBAL`。  
  
```  
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cfFormat`  
 是用要返回的数据格式。 此参数可以是预定义的剪贴板格式或本机 Windows 返回的值之一[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049)函数。  
  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述是用要返回数据的格式。 为此参数提供一个值，如果你想要指定超出指定的剪贴板格式的格式的其他信息`cfFormat`。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 包含如果成功，则会显示数据的全局内存块的句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
##  <a name="getnextformat"></a>COleDataObject::GetNextFormat  
 调用此函数重复可获取可用于从项中检索数据的所有格式。  
  
```  
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```  
  
### <a name="parameters"></a>参数  
 `lpFormatEtc`  
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)函数调用返回时接收的格式信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果另一个非零的格式是可用;否则为 0。  
  
### <a name="remarks"></a>备注  
 调用了[COleDataObject::BeginEnumFormats](#beginenumformats)，存储此数据对象支持的第一个格式的位置。 对连续调用`GetNextFormat`将枚举在数据对象中的可用格式的列表。 使用这些函数列出可用的格式。  
  
 若要检查给定格式的可用性，请调用[COleDataObject::IsDataAvailable](#isdataavailable)。  
  
 有关详细信息，请参阅[IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) Windows SDK 中。  
  
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
 指向[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177)结构描述所需的格式。 为此参数提供一个值，仅当你想要指定超出指定的剪贴板格式的格式的其他信息`cfFormat`。 如果它是**NULL**，默认值用于中的其他字段中**FORMATETC**结构。  
  
### <a name="return-value"></a>返回值  
 如果数据中指定的格式; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数很有用之前调用`GetData`， `GetFileData`，或`GetGlobalData`。  
  
 有关详细信息，请参阅[IDataObject::QueryGetData](http://msdn.microsoft.com/library/windows/desktop/ms680637)和[FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) Windows SDK 中。  
  
 有关详细信息，请参阅[RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) Windows SDK 中。  
  
### <a name="example"></a>示例  
  请参阅示例[CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)。  
  
##  <a name="release"></a>COleDataObject::Release  
 调用此函数可释放的所有权[IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421)以前有关联的对象`COleDataObject`对象。  
  
```  
void Release();
```  
  
### <a name="remarks"></a>备注  
 `IDataObject`与关联`COleDataObject`通过调用**附加**或`AttachClipboard`显式或框架。 如果`bAutoRelease`参数**附加**是**FALSE**、`IDataObject`对象将不会被释放。 在这种情况下，调用方负责释放`IDataObject`通过调用[iunknown:: Release](http://msdn.microsoft.com/library/windows/desktop/ms682317)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 HIERSVR](../../visual-cpp-samples.md)   
 [MFC 示例 OCLIENT](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [COleDataSource 类](../../mfc/reference/coledatasource-class.md)   
 [COleClientItem 类](../../mfc/reference/coleclientitem-class.md)   
 [COleServerItem 类](../../mfc/reference/coleserveritem-class.md)
