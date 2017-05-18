---
title: "CGdiObject 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
dev_langs:
- C++
helpviewer_keywords:
- brushes, base class for
- fonts, base class for
- regions, base class for
- pens, base class for
- palettes, base class for
- CGdiObject class
- GDI objects, base class for
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
caps.latest.revision: 21
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 7fb0cd49c6a20263a5cae305b7f08f2733033ff2
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cgdiobject-class"></a>CGdiObject 类
为各种 Windows 图形设备接口 (GDI) 对象（如位图、区域、画笔、笔、调色板和字体）提供基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|构造 `CGdiObject` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|Windows GDI 将对象附加到`CGdiObject`对象。|  
|[CGdiObject::CreateStockObject](#createstockobject)|检索 Windows 预定义的股票钢笔、 画笔或字体之一的句柄。|  
|[CGdiObject::DeleteObject](#deleteobject)|删除 Windows GDI 对象附加到`CGdiObject`通过释放与对象关联的所有系统存储内存中的对象。|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|删除任何临时`CGdiObject`由创建的对象`FromHandle`。|  
|[CGdiObject::Detach](#detach)|Windows GDI 从分离对象`CGdiObject`对象，并返回 Windows GDI 对象的句柄。|  
|[CGdiObject::FromHandle](#fromhandle)|返回一个指向`CGdiObject`提供给 Windows GDI 对象的句柄的对象。|  
|[CGdiObject::GetObject](#getobject)|填充的缓冲区时，用于描述 Windows GDI 对象的数据附加到`CGdiObject`对象。|  
|[CGdiObject::GetObjectType](#getobjecttype)|检索的 GDI 对象的类型。|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|返回`m_hObject`除非`this`是`NULL`，在这种情况下`NULL`返回。|  
|[CGdiObject::UnrealizeObject](#unrealizeobject)|重置画笔的原点或重置逻辑调色板。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CGdiObject::operator ！ =](#operator_neq)|确定两个 GDI 对象在逻辑上非是否相等。|  
|[CGdiObject::operator = =](#operator_eq_eq)|确定两个 GDI 对象是否在逻辑上相等。|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|检索`HANDLE`对附加的 Windows GDI 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|一个`HANDLE`包含`HBITMAP`， `HPALETTE`， `HRGN`， `HBRUSH`， `HPEN`，或`HFONT`附加到此对象。|  
  
## <a name="remarks"></a>备注  
 切勿创建`CGdiObject`直接。 相反，您创建一个对象从其派生类之一，如`CPen`或`CBrush`。  
  
 有关详细信息`CGdiObject`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="attach"></a>CGdiObject::Attach  
 Windows GDI 将对象附加到`CGdiObject`对象。  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 一个`HANDLE`对 Windows GDI 对象 (例如，`HPEN`或`HBRUSH`)。  
  
### <a name="return-value"></a>返回值  
 如果附件成功，则非零值否则为 0。  
  
##  <a name="cgdiobject"></a>CGdiObject::CGdiObject  
 构造 `CGdiObject` 对象。  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>备注  
 切勿创建`CGdiObject`直接。 相反，您创建一个对象从其派生类之一，如`CPen`或**Cbrush**。  
  
##  <a name="createstockobject"></a>CGdiObject::CreateStockObject  
 检索到其中一个预定义的股票 Windows GDI 钢笔、 画笔或字体的句柄和 GDI 将对象附加到`CGdiObject`对象。  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个常数，它指定所需的常用对象的类型。 请参阅参数*fnObject*为[GetStockObject](http://msdn.microsoft.com/library/windows/desktop/dd144925)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关适当的值的说明。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数具有一个将派生的类，这些类对应于 Windows GDI 对象类型，如`CPen`为常用的画笔。  
  
##  <a name="deleteobject"></a>CGdiObject::DeleteObject  
 释放与 Windows GDI 对象相关联的所有系统存储内存中删除附加的 Windows GDI 对象。  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>返回值  
 已成功删除的 GDI 对象; 如果非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 与关联的存储`CGdiObject`对象不受此调用。 应用程序不应调用`DeleteObject`上`CGdiObject`实际选入设备上下文的对象。  
  
 当删除图案画笔时，不会删除相关联画笔的位图。 必须单独删除位图。  
  
##  <a name="deletetempmap"></a>CGdiObject::DeleteTempMap  
 自动调用`CWinApp`空闲时间处理程序中，`DeleteTempMap`删除任何临时`CGdiObject`由创建的对象`FromHandle`。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>备注  
 `DeleteTempMap`分离 Windows GDI 对象附加到一个临时`CGdiObject`之前删除对象`CGdiObject`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView #&175;](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>CGdiObject::Detach  
 Windows GDI 从分离对象`CGdiObject`对象，并返回 Windows GDI 对象的句柄。  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>返回值  
 一个`HANDLE`向 Windows GDI 对象分离; 否则为**NULL**如果连接没有 GDI 对象。  
  
##  <a name="fromhandle"></a>CGdiObject::FromHandle  
 返回一个指向`CGdiObject`提供给 Windows GDI 对象的句柄的对象。  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 一个`HANDLE`对 Windows GDI 对象。  
  
### <a name="return-value"></a>返回值  
 一个指向`CGdiObject`这可能是临时的还是永久。  
  
### <a name="remarks"></a>备注  
 如果`CGdiObject`对象尚未附加到 Windows GDI 对象，一个临时`CGdiObject`创建对象并将其连接。  
  
 此临时`CGdiObject`对象直到下次该应用程序在其事件循环中，删除这段时间所有临时的图形对象有空闲时间才有效。 另一种说法是一个窗口消息处理过程才有效临时对象。  
  
##  <a name="getobject"></a>CGdiObject::GetObject  
 定义指定的对象的数据填充缓冲区。  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>参数  
 `nCount`  
 指定要将复制到的字节数`lpObject`缓冲区。  
  
 `lpObject`  
 指向用户提供的缓冲区，则要接收的信息。  
  
### <a name="return-value"></a>返回值  
 检索的字节数;否则 0 如果检测到错误发生。  
  
### <a name="remarks"></a>备注  
 此函数检索其类型取决于图形对象的类型的数据结构，如以下列表所示︰  
  
|对象|缓冲区类型|  
|------------|-----------------|  
|`CPen`|[LOGPEN](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)|  
|`CBitmap`|[位图](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|**WORD**|  
|`CRgn`|不支持|  
  
 如果对象是`CBitmap`对象，`GetObject`返回宽度、 高度和位图的颜色的格式信息。 可以使用检索实际位数[CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)。  
  
 如果对象是`CPalette`对象，`GetObject`检索**WORD**调色板中指定的条目数。 该函数不会检索[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)结构，它定义调色板。 应用程序可以通过调用获取调色板条目的信息[CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)。  
  
##  <a name="getobjecttype"></a>CGdiObject::GetObjectType  
 检索的 GDI 对象的类型。  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>返回值  
 类型的对象，如果成功，则否则为 0。 值可以是以下项之一︰  
  
- **OBJ_BITMAP**位图  
  
- **OBJ_BRUSH**画笔  
  
- **OBJ_FONT**字体  
  
- **OBJ_PAL**调色板  
  
- **OBJ_PEN**笔  
  
- **OBJ_EXTPEN**扩展笔  
  
- **OBJ_REGION**区域  
  
- **OBJ_DC**设备上下文  
  
- **OBJ_MEMDC**内存设备上下文  
  
- **OBJ_METAFILE**图元文件  
  
- **OBJ_METADC**图元文件设备上下文  
  
- **OBJ_ENHMETAFILE**增强型图元文件  
  
- **OBJ_ENHMETADC**增强型图元文件设备上下文  
  
##  <a name="getsafehandle"></a>CGdiObject::GetSafeHandle  
 返回`m_hObject`除非**这**是**NULL**，在这种情况下**NULL**返回。  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`HANDLE`对附加的 Windows GDI 对象; 否则为**NULL**如果连接没有任何对象。  
  
### <a name="remarks"></a>备注  
 这是常规的句柄接口模式的一部分，是有用**NULL**有效或特殊值，当一个句柄。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)。  
  
##  <a name="m_hobject"></a>CGdiObject::m_hObject  
 一个`HANDLE`包含`HBITMAP`， **HRGN**， `HBRUSH`， `HPEN`， `HPALETTE`，或**HFONT**附加到此对象。  
  
```  
HGDIOBJ m_hObject;  
```  
  
##  <a name="operator_neq"></a>CGdiObject::operator ！ =  
 确定两个 GDI 对象在逻辑上非是否相等。  
  
```  
BOOL operator!=(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>参数  
 `obj`  
 一个指向现有`CGdiObject`。  
  
### <a name="remarks"></a>备注  
 确定在左侧的 GDI 对象是否不等于右侧的 GDI 对象。  
  
##  <a name="operator_eq_eq"></a>CGdiObject::operator = =  
 确定两个 GDI 对象是否在逻辑上相等。  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>参数  
 `obj`  
 对现有的引用`CGdiObject`。  
  
### <a name="remarks"></a>备注  
 确定在左侧的 GDI 对象是否等于右侧的 GDI 对象。  
  
##  <a name="operator_hgdiobj"></a>CGdiObject::operator HGDIOBJ  
 检索`HANDLE`对附加的 Windows GDI 对象; 否则为**NULL**如果连接没有任何对象。  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>CGdiObject::UnrealizeObject  
 重置画笔的原点或重置逻辑调色板。  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 虽然`UnrealizeObject`是成员函数的`CGdiObject`类，它应只对调用`CBrush`或`CPalette`对象。  
  
 有关`CBrush`对象，`UnrealizeObject`指示系统在重置给定画笔的原点选入设备上下文的下一个时间。 如果对象是`CPalette`对象，`UnrealizeObject`指示系统，就好像它有没有以前已意识到实现调色板。 下一次应用程序调用[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)函数指定的调色板中，系统完全重新映射到系统调色板逻辑的调色板。  
  
 `UnrealizeObject`函数不应与常用的对象使用。 `UnrealizeObject`必须调用函数，只要设置新的画笔原点 (通过[CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函数)。 `UnrealizeObject`不得调用函数，为当前选定的画笔或当前所选的任何上下文中显示的调色板。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBitmap 类](../../mfc/reference/cbitmap-class.md)   
 [CBrush 类](../../mfc/reference/cbrush-class.md)   
 [CFont 类](../../mfc/reference/cfont-class.md)   
 [CPalette 类](../../mfc/reference/cpalette-class.md)   
 [CPen 类](../../mfc/reference/cpen-class.md)   
 [CRgn 类](../../mfc/reference/crgn-class.md)

