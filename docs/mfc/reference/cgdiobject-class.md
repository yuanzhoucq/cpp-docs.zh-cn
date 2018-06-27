---
title: CGdiObject 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eb8cc37396069dc7e0ea53506436b536100bdbb4
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956124"
---
# <a name="cgdiobject-class"></a>CGdiObject 类
为各种 Windows 图形设备接口 (GDI) 对象（如位图、区域、画笔、笔、调色板和字体）提供基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CGdiObject : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](#cgdiobject)|构造 `CGdiObject` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CGdiObject::Attach](#attach)|将附加到一个 Windows GDI 对象`CGdiObject`对象。|  
|[CGdiObject::CreateStockObject](#createstockobject)|检索 Windows 预定义股票钢笔、 画笔或字体之一的句柄。|  
|[CGdiObject::DeleteObject](#deleteobject)|删除 Windows GDI 对象附加到`CGdiObject`从通过释放与对象关联的所有系统存储的内存的对象。|  
|[CGdiObject::DeleteTempMap](#deletetempmap)|删除任何临时`CGdiObject`创建的对象`FromHandle`。|  
|[CGdiObject::Detach](#detach)|分离中的 Windows GDI 对象`CGdiObject`对象并返回 Windows GDI 对象的句柄。|  
|[CGdiObject::FromHandle](#fromhandle)|返回一个指向`CGdiObject`提供 Windows GDI 对象的句柄的对象。|  
|[CGdiObject::GetObject](#getobject)|填充具有描述 Windows GDI 对象的数据的缓冲区附加到`CGdiObject`对象。|  
|[CGdiObject::GetObjectType](#getobjecttype)|检索的 GDI 对象的类型。|  
|[CGdiObject::GetSafeHandle](#getsafehandle)|返回`m_hObject`除非`this`是`NULL`，在这种情况下`NULL`返回。|  
|[CGdiObject::UnrealizeObject](#unrealizeobject)|重置的源的画笔或重置逻辑调色板。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CGdiObject::operator ！ =](#operator_neq)|确定两个 GDI 对象是否以逻辑方式不相等。|  
|[CGdiObject::operator = =](#operator_eq_eq)|确定两个 GDI 对象是否逻辑上相等。|  
|[CGdiObject::operator HGDIOBJ](#operator_hgdiobj)|检索`HANDLE`到附加的 Windows GDI 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CGdiObject::m_hObject](#m_hobject)|A`HANDLE`包含`HBITMAP`， `HPALETTE`， `HRGN`， `HBRUSH`， `HPEN`，或`HFONT`附加到此对象。|  
  
## <a name="remarks"></a>备注  
 切勿创建`CGdiObject`直接。 相反，创建的对象从其派生类之一如`CPen`或`CBrush`。  
  
 有关详细信息`CGdiObject`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="attach"></a>  CGdiObject::Attach  
 将附加到一个 Windows GDI 对象`CGdiObject`对象。  
  
```  
BOOL Attach(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>参数  
 *hObject*  
 A`HANDLE`与 Windows GDI 对象 (例如，`HPEN`或`HBRUSH`)。  
  
### <a name="return-value"></a>返回值  
 如果附件成功; 则为非 0否则为 0。  
  
##  <a name="cgdiobject"></a>  CGdiObject::CGdiObject  
 构造 `CGdiObject` 对象。  
  
```  
CGdiObject();
```  
  
### <a name="remarks"></a>备注  
 切勿创建`CGdiObject`直接。 相反，创建的对象从其派生类之一如`CPen`或`Cbrush`。  
  
##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject  
 检索预定义的常用 Windows GDI 钢笔、 画笔或字体，之一的句柄，并将附加到的 GDI 对象`CGdiObject`对象。  
  
```  
BOOL CreateStockObject(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 一个常数，它指定所需的常用对象的类型。 请参阅参数*fnObject*为[GetStockObject](http://msdn.microsoft.com/library/windows/desktop/dd144925) Windows SDK for 相应值的说明中。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此函数带一个派生的类的对应 Windows GDI 对象类型，如`CPen`的常用的画笔。  
  
##  <a name="deleteobject"></a>  CGdiObject::DeleteObject  
 通过释放与 Windows GDI 对象相关联的所有系统存储从内存中删除附加的 Windows GDI 对象。  
  
```  
BOOL DeleteObject();
```  
  
### <a name="return-value"></a>返回值  
 已成功删除的 GDI 对象; 如果非零否则为 0。  
  
### <a name="remarks"></a>备注  
 与关联的存储`CGdiObject`对象不受此调用。 应用程序不应调用`DeleteObject`上`CGdiObject`当前所选入设备上下文的对象。  
  
 当删除模式画笔时，不会删除与画笔相关联的位图。 必须单独删除位图。  
  
##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap  
 自动调用`CWinApp`空闲时间处理程序，`DeleteTempMap`删除任何临时`CGdiObject`创建的对象`FromHandle`。  
  
```  
static void PASCAL DeleteTempMap();
```  
  
### <a name="remarks"></a>备注  
 `DeleteTempMap` 分离附加到一个临时的 Windows GDI 对象`CGdiObject`对象在删除之前`CGdiObject`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]  
  
##  <a name="detach"></a>  CGdiObject::Detach  
 分离中的 Windows GDI 对象`CGdiObject`对象并返回 Windows GDI 对象的句柄。  
  
```  
HGDIOBJ Detach();
```  
  
### <a name="return-value"></a>返回值  
 A`HANDLE`到 Windows GDI 对象分离; 否则为**NULL**如果附加没有任何 GDI 对象。  
  
##  <a name="fromhandle"></a>  CGdiObject::FromHandle  
 返回一个指向`CGdiObject`提供 Windows GDI 对象的句柄的对象。  
  
```  
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```  
  
### <a name="parameters"></a>参数  
 *hObject*  
 A`HANDLE`与 Windows GDI 对象。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CGdiObject`这可能是临时的还是永久。  
  
### <a name="remarks"></a>备注  
 如果`CGdiObject`对象尚未附加到 Windows GDI 对象，一个临时`CGdiObject`创建对象并将其附加。  
  
 此临时`CGdiObject`对象只有在应用程序在其事件循环，删除这段时间的所有临时图形对象具有空闲时间的下一步时才有效。 另一种说法是一个窗口消息处理期间才有效临时对象。  
  
##  <a name="getobject"></a>  CGdiObject::GetObject  
 定义指定的对象的数据填充缓冲区。  
  
```  
int GetObject(
    int nCount,  
    LPVOID lpObject) const;  
```  
  
### <a name="parameters"></a>参数  
 *nCount*  
 指定要将复制到的字节数*lpObject*缓冲区。  
  
 *lpObject*  
 指向以将接收信息的用户提供的缓冲区。  
  
### <a name="return-value"></a>返回值  
 检索的字节的数量;否则 0 如果检测到错误发生。  
  
### <a name="remarks"></a>备注  
 函数将检索其类型取决于图形对象的类型的数据结构，如以下列表所示：  
  
|对象|缓冲区类型|  
|------------|-----------------|  
|`CPen`|[LOGPEN](../../mfc/reference/logpen-structure.md)|  
|`CBrush`|[LOGBRUSH](../../mfc/reference/logbrush-structure.md)|  
|`CFont`|[LOGFONT](http://msdn.microsoft.com/library/windows/desktop/dd145037)|  
|`CBitmap`|[位图](../../mfc/reference/bitmap-structure.md)|  
|`CPalette`|**WORD**|  
|`CRgn`|不支持|  
  
 如果对象是`CBitmap`对象，`GetObject`返回宽度、 高度和颜色位图格式信息。 可以使用检索的实际位[CBitmap::GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)。  
  
 如果对象是`CPalette`对象，`GetObject`检索**WORD** ，调色板中指定的条目数。 该函数不会检索[LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040)定义调色板的结构。 应用程序可以获取调色板条目的信息，通过调用[CPalette::GetPaletteEntries](../../mfc/reference/cpalette-class.md#getpaletteentries)。  
  
##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType  
 检索的 GDI 对象的类型。  
  
```  
UINT GetObjectType() const;  
```  
  
### <a name="return-value"></a>返回值  
 对象，如果成功，则的类型否则为 0。 值可以是下列任一值：  
  
- **OBJ_BITMAP**位图  
  
- **OBJ_BRUSH**画笔  
  
- **OBJ_FONT**字体  
  
- **OBJ_PAL**调色板  
  
- **OBJ_PEN**钢笔  
  
- **OBJ_EXTPEN**扩展钢笔  
  
- **OBJ_REGION**区域  
  
- **OBJ_DC**设备上下文  
  
- **OBJ_MEMDC**内存设备上下文  
  
- **OBJ_METAFILE**图元文件  
  
- **OBJ_METADC**图元文件设备上下文  
  
- **OBJ_ENHMETAFILE**增强型图元文件  
  
- **OBJ_ENHMETADC**增强型图元文件设备上下文  
  
##  <a name="getsafehandle"></a>  CGdiObject::GetSafeHandle  
 返回`m_hObject`除非**这**是**NULL**，在这种情况下**NULL**返回。  
  
```  
HGDIOBJ GetSafeHandle() const;  
```  
  
### <a name="return-value"></a>返回值  
 A`HANDLE`到附加的 Windows GDI 对象; 否则为**NULL**如果附加没有任何对象。  
  
### <a name="remarks"></a>备注  
 这是常规的句柄界面范例的一部分，很有用**NULL**是句柄值有效或特殊的值。  
  
### <a name="example"></a>示例  
  请参阅示例[CWnd::IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)。  
  
##  <a name="m_hobject"></a>  CGdiObject::m_hObject  
 A`HANDLE`包含`HBITMAP`， **HRGN**， `HBRUSH`， `HPEN`， `HPALETTE`，或**HFONT**附加到此对象。  
  
```  
HGDIOBJ m_hObject;  
```  
  
##  <a name="operator_neq"></a>  CGdiObject::operator ！ =  
 确定两个 GDI 对象是否以逻辑方式不相等。  
  
```  
BOOL operator!=(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>参数  
 *obj*  
 指向现有`CGdiObject`。  
  
### <a name="remarks"></a>备注  
 确定在左侧的 GDI 对象是否不等于右侧的 GDI 对象。  
  
##  <a name="operator_eq_eq"></a>  CGdiObject::operator = =  
 确定两个 GDI 对象是否逻辑上相等。  
  
```  
BOOL operator==(const CGdiObject& obj) const;  
```  
  
### <a name="parameters"></a>参数  
 *obj*  
 对现有的引用`CGdiObject`。  
  
### <a name="remarks"></a>备注  
 确定在左侧的 GDI 对象是否等于右侧的 GDI 对象。  
  
##  <a name="operator_hgdiobj"></a>  CGdiObject::operator HGDIOBJ  
 检索`HANDLE`到附加的 Windows GDI 对象; 否则为**NULL**如果附加没有任何对象。  
  
```  
operator HGDIOBJ() const;  
```  
  
##  <a name="unrealizeobject"></a>  CGdiObject::UnrealizeObject  
 重置的源的画笔或重置逻辑调色板。  
  
```  
BOOL UnrealizeObject();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 虽然`UnrealizeObject`是成员函数的`CGdiObject`类，它应仅对调用`CBrush`或`CPalette`对象。  
  
 有关`CBrush`对象，`UnrealizeObject`指示系统在它被选入设备上下文的下一步时间重置给定画笔的原点。 如果对象是`CPalette`对象，`UnrealizeObject`指示系统在实现调色板，就好像它具有不以前已实现。 在应用程序调用的下一步时间[CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)函数指定调色板，系统完全重新映射到系统调色板逻辑调色板。  
  
 `UnrealizeObject`函数不应使用与常用的对象。 `UnrealizeObject`每当设置新的画笔源时，必须调用函数 (通过[CDC::SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)函数)。 `UnrealizeObject`必须不为当前所选的画笔或当前所选的任何的调色板显示上下文中调用函数。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CBitmap 类](../../mfc/reference/cbitmap-class.md)   
 [CBrush 类](../../mfc/reference/cbrush-class.md)   
 [CFont 类](../../mfc/reference/cfont-class.md)   
 [CPalette 类](../../mfc/reference/cpalette-class.md)   
 [CPen 类](../../mfc/reference/cpen-class.md)   
 [CRgn 类](../../mfc/reference/crgn-class.md)
