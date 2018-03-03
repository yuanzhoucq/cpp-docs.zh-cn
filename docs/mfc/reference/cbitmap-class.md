---
title: "CBitmap 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
dev_langs:
- C++
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22922d29c09ee97a8b2a292953b4bf903ab6649e
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2018
---
# <a name="cbitmap-class"></a>CBitmap 类
封装一个 Windows 图形设备接口 (GDI) 位图并提供成员函数以操作位图。  
  
## <a name="syntax"></a>语法  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|构造 `CBitmap` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|初始化具有指定的宽度、 高度和位模式的设备相关的内存位图的对象。|  
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|初始化与位图的宽度、 高度和位模式 （如果指定了一个） 给出的对象**位图**结构。|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|初始化与位图的对象，以便其与指定的设备相兼容。|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|初始化具有指定设备与兼容的可丢弃位图的对象。|  
|[CBitmap::FromHandle](#fromhandle)|返回一个指向`CBitmap`对象提供 Windows 句柄时`HBITMAP`位图。|  
|[CBitmap::GetBitmap](#getbitmap)|填充**位图**位图有关的信息的结构。|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|将指定位图的位复制到指定的缓冲区。|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|返回的宽度和位图的高度。 假定的高度和宽度设置以前的[SetBitmapDimension](#setbitmapdimension)成员函数。|  
|[Cbitmap:: Loadbitmap](#loadbitmap)|通过从应用程序的可执行文件加载命名的位图资源并将位图附加到对象初始化的对象。|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|加载位图并映射到当前的系统颜色的颜色。|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|通过加载一个预定义的 Windows 位图，并将位图附加到对象初始化的对象。|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|将位图的位设置为指定的位值。|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|给以 0.1 毫米为单位的位图的宽度和高度。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](#operator_hbitmap)|返回附加到的 Windows 句柄`CBitmap`对象。|  
  
## <a name="remarks"></a>备注  
 若要使用`CBitmap`对象，构造对象，将位图句柄附加到用之一初始化成员函数，然后调用对象的成员函数。  
  
 有关详细信息使用类似的图形对象`CBitmap`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>惠?  
 **标头:** afxwin.h  
  
##  <a name="cbitmap"></a>CBitmap::CBitmap  
 构造 `CBitmap` 对象。  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>备注  
 必须使用一个初始化成员函数初始化生成的对象。  
  
##  <a name="createbitmap"></a>CBitmap::CreateBitmap  
 初始化具有指定的宽度、高度和位模式的设备相关的内存位图。  
  
```  
BOOL CreateBitmap(
    int nWidth,  
    int nHeight,  
    UINT nPlanes,  
    UINT nBitcount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 指定位图的宽度（以像素为单位）。  
  
 `nHeight`  
 指定位图的高度（以像素为单位）。  
  
 `nPlanes`  
 指定位图中的颜色平面的数量。  
  
 `nBitcount`  
 指定每个显示像素的颜色位的数量。  
  
 `lpBits`  
 指向包含的初始位图位值的字节的数组。 如果它是 **NULL**，新位图则未初始化。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 对于颜色位图， `nPlanes` 或 `nBitcount` 参数应设为 1。 如果这些参数均设为 1， `CreateBitmap` 则会创建一个单色位图。  
  
 无法为显示设备直接选择位图，尽管它可以选择作为"内存设备上下文"的当前位图使用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)和使用复制到任何兼容的设备上下文[Cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)函数。  
  
 完成通过 `CBitmap` 函数创建的 `CreateBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。  
  
 有关详细信息，请参见 **BITMAP** 结构中的 **bmBits** 字段的说明。 [位图](../../mfc/reference/bitmap-structure.md)结构做了介绍[CBitmap::CreateBitmapIndirect](#createbitmapindirect)成员函数。  
  
##  <a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect  
 初始化具有宽度、 高度和提供指向的结构中的位模式 （如果指定） 的位图`lpBitmap`。  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>参数  
 `lpBitmap`  
 指向[位图](../../mfc/reference/bitmap-structure.md)包含位图有关的信息的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 无法为显示设备直接选择位图，尽管它可以选择作为内存设备上下文的当前位图使用[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)和使用复制到任何兼容的设备上下文[Cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函数。 ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt)函数可以当前画笔的位图将直接复制到显示设备上下文。)  
  
 如果**位图**指向结构`lpBitmap`通过使用已填写参数`GetObject`函数未指定位图的位和位图未初始化。 若要初始化位图，应用程序可以使用一个函数如[cdc:: bitblt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973)从中进行复制 bits 由的第一个参数标识位图`CGdiObject::GetObject`到创建的位图`CreateBitmapIndirect`.  
  
 当你完成与`CBitmap`创建与对象`CreateBitmapIndirect`函数，首先选择设备上下文中中的位图，然后删除`CBitmap`对象。  
  
##  <a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap  
 初始化与指定的设备兼容的位图`pDC`。  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指定的设备上下文。  
  
 `nWidth`  
 指定位图的宽度（以像素为单位）。  
  
 `nHeight`  
 指定位图的高度（以像素为单位）。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 位图具有相同数量的颜色平面或与指定的设备上下文的每像素位数格式相同。 它可以选择作为适用于指定的任何内存设备的当前位图`pDC`。  
  
 如果`pDC`是内存设备上下文，位图返回在该设备上下文中具有与当前所选的位图的格式相同。 "内存设备上下文"是内存的表示显示图面块。 它可以用于准备在内存中的映像，然后将其复制到兼容的设备的实际显示图面。  
  
 当创建内存设备上下文时，GDI 会自动为其选择常用的单色位图。  
  
 由于颜色或选择的单色位图有颜色内存设备上下文，因此返回的位图格式`CreateCompatibleBitmap`函数并不总是相同; 但是，无内存设备上下文的兼容位图格式是始终在设备的格式。  
  
 当你完成与`CBitmap`创建与对象`CreateCompatibleBitmap`函数，首先选择设备上下文中中的位图，然后删除`CBitmap`对象。  
  
##  <a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap  
 初始化与由标识的设备上下文兼容的可丢弃位图`pDC`。  
  
```  
BOOL CreateDiscardableBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指定设备上下文。  
  
 `nWidth`  
 指定位图的宽度 （以位为单位）。  
  
 `nHeight`  
 指定位图的高度 （以位为单位）。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 位图具有相同数量的颜色平面或与指定的设备上下文的每像素位数格式相同。 应用程序可以选择将该位图作为适用于指定的内存设备的当前位图`pDC`。  
  
 Windows 可丢弃创建此函数，仅当应用程序没有选择的显示上下文到它的位图。 如果 Windows 将时未选择和更高版本的应用程序尝试以选中它，将丢弃位图[cdc:: selectobject](../../mfc/reference/cdc-class.md#selectobject)函数将返回**NULL**。  
  
 当你完成与`CBitmap`创建与对象`CreateDiscardableBitmap`函数，首先选择设备上下文中中的位图，然后删除`CBitmap`对象。  
  
##  <a name="fromhandle"></a>CBitmap::FromHandle  
 返回一个指向`CBitmap`对象时提供 Windows GDI 位图的句柄。  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>参数  
 `hBitmap`  
 指定 Windows GDI 位图。  
  
### <a name="return-value"></a>返回值  
 指向的指针`CBitmap`对象成功; 否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CBitmap`对象尚未附加到该句柄，一种临时`CBitmap`创建对象并将其附加。 此临时`CBitmap`对象是否有效，仅在下次应用程序在其事件循环中具有空闲时间，直到在哪些时间所有临时图形对象会被删除。 另一种说法是一个窗口消息处理期间才有效临时对象。  
  
##  <a name="getbitmap"></a>CBitmap::GetBitmap  
 检索附加位图的图像属性。  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>参数  
 `pBitMap`  
 指向[位图结构](../../mfc/reference/bitmap-structure.md)结构，它将接收的映像属性。 此参数不能为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getbitmapbits"></a>CBitmap::GetBitmapBits  
 将附加的位图的位模式复制到指定的缓冲区。  
  
```  
DWORD GetBitmapBits(
    DWORD dwCount,  
    LPVOID lpBits) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwCount`  
 要复制到缓冲区的字节数。  
  
 `lpBits`  
 指向将收到位图的缓冲区的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则将复制到缓冲区的字节数否则为 0。  
  
### <a name="remarks"></a>备注  
 使用[CBitmap::GetBitmap](#getbitmap)确定所需的缓冲区大小。  
  
##  <a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension  
 返回的宽度和位图的高度。  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>返回值  
 宽度和高度的位图，以 0.1 毫米为单位。 中的高度是**cy**的成员`CSize`对象和宽度处于**cx**成员。 如果位图宽度和高度不通过使用已设置`SetBitmapDimension`，返回值为 0。  
  
### <a name="remarks"></a>备注  
 假定的高度和宽度以前通过使用设置[SetBitmapDimension](#setbitmapdimension)成员函数。  
  
##  <a name="loadbitmap"></a>Cbitmap:: Loadbitmap  
 加载位图资源通过名为`lpszResourceName`或识别的 ID 号`nIDResource`从应用程序的可执行文件。  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 指向以 null 结尾的字符串，包含位图资源的名称。  
  
 `nIDResource`  
 指定位图资源的资源 ID 号。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 加载的位图附加到`CBitmap`对象。  
  
 如果通过标识位图`lpszResourceName`不存在或如果没有内存不足，无法加载位图，该函数返回 0。  
  
 你可以使用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)可用于删除位图函数加载的`LoadBitmap`函数，或`CBitmap`析构函数将为你删除对象。  
  
> [!CAUTION]
>  你删除对象之前，请确保它不选入设备上下文。  
  
 以下位图已添加到 3.1 及更高版本的 Windows 版本：  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 3.0 及更早版本的 Windows 版本的设备驱动程序不存在这些位图。 有关的位图，并会显示其外观的完整列表，请参阅 Windows SDK。  
  
##  <a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap  
 调用此成员函数以加载位图并映射到当前的系统颜色的颜色。  
  
```  
BOOL LoadMappedBitmap(
    UINT nIDBitmap,  
    UINT nFlags = 0,  
    LPCOLORMAP lpColorMap = NULL,  
    int nMapSize = 0);
```  
  
### <a name="parameters"></a>参数  
 `nIDBitmap`  
 位图资源的 ID。  
  
 `nFlags`  
 位图的标志。 可以为零或**CMB_MASKED**。  
  
 `lpColorMap`  
 指向的指针**颜色映射**结构，其中包含所需映射的位图的颜色信息。 如果此参数为**NULL**，该函数使用默认颜色地图。  
  
 *nMapSize*  
 指向数量的颜色映射`lpColorMap`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，`LoadMappedBitmap`将映射通常用于按钮标志符号的颜色。  
  
 有关创建映射的位图的信息，请参阅 Windows 函数[CreateMappedBitmap](http://go.microsoft.com/fwlink/p/?linkid=230562)和[颜色映射](http://msdn.microsoft.com/library/windows/desktop/bb760448)Windows SDK 中的结构。  
  
##  <a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap  
 加载 Windows 所使用的预定义的位图。  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>参数  
 `nIDBitmap`  
 预定义的 Windows 位图的 ID 号。 从 WINDOWS 下面列出可能的值。H:  
  
|||  
|-|-|  
|**OBM_BTNCORNERS**|**OBM_OLD_RESTORE**|  
|**OBM_BTSIZE**|**OBM_OLD_RGARROW**|  
|**OBM_CHECK**|**OBM_OLD_UPARROW**|  
|**OBM_CHECKBOXES**|**OBM_OLD_ZOOM**|  
|**OBM_CLOSE**|**OBM_REDUCE**|  
|**OBM_COMBO**|**OBM_REDUCED**|  
|**OBM_DNARROW**|**OBM_RESTORE**|  
|**OBM_DNARROWD**|**OBM_RESTORED**|  
|**OBM_DNARROWI**|**OBM_RGARROW**|  
|**OBM_LFARROW**|**OBM_RGARROWD**|  
|**OBM_LFARROWD**|**OBM_RGARROWI**|  
|**OBM_LFARROWI**|**OBM_SIZE**|  
|**OBM_MNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_CLOSE**|**OBM_UPARROWD**|  
|**OBM_OLD_DNARROW**|**OBM_UPARROW**|  
|**OBM_OLD_LFARROW**|**OBM_ZOOM**|  
|**OBM_OLD_REDUCE**|**OBM_ZOOMD**|  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 Bitmap 以开头的名称**OBM_OLD**表示由 3.0 之前的 Windows 版本的位图。  
  
 请注意，该常量**OEMRESOURCE**包括 WINDOWS 之前必须定义。若要使用的任何 H **OBM_**常量。  
  
##  <a name="operator_hbitmap"></a>CBitmap::operator HBITMAP  
 此运算符用于获取附加的 Windows GDI 句柄的`CBitmap`对象。  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄表示`CBitmap`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符是一个强制转换运算符，它支持直接使用`HBITMAP`对象。  
  
 有关使用图形对象的详细信息，请参阅[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)Windows SDK 中。  
  
##  <a name="setbitmapbits"></a>CBitmap::SetBitmapBits  
 将位图的位设置为给定的位值`lpBits`。  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>参数  
 `dwCount`  
 指定指向的字节数`lpBits`。  
  
 `lpBits`  
 指向**字节**数组，其中包含要复制到的像素值`CBitmap`对象。 若要能够正确呈现其图像的位图的顺序，值应进行格式设置以符合 CBitmap 实例已创建时指定的高度、 宽度和颜色深度值。 有关详细信息，请参阅[CBitmap::CreateBitmap](#createbitmap)。  
  
### <a name="return-value"></a>返回值  
 在将位图位; 设置中使用的字节数如果函数失败，则为 0。  
  
##  <a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension  
 给以 0.1 毫米为单位的位图的宽度和高度。  
  
```  
CSize SetBitmapDimension(
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `nWidth`  
 指定的宽度 （以 0.1 毫米为单位） 的位图。  
  
 `nHeight`  
 指定的高度 （以 0.1 毫米为单位） 的位图。  
  
### <a name="return-value"></a>返回值  
 以前的位图维度。 高度处于**cy**成员变量`CSize`对象和宽度都在**cx**成员变量。  
  
### <a name="remarks"></a>备注  
 GDI 不使用这些值，但若要返回它们时应用程序调用除外[GetBitmapDimension](#getbitmapdimension)成员函数。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)

