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
- drawing, tools
- CBitmap class
- GDI bitmap
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: ccfe592bbbae8c0eff22baa6e1baac56754ef6fc
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cbitmap-class"></a>CBitmap 类
封装一个 Windows 图形设备接口 (GDI) 位图并提供成员函数以操作位图。  
  
## <a name="syntax"></a>语法  
  
```  
class CBitmap : public CGdiObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CBitmap::CBitmap](#cbitmap)|构造 `CBitmap` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](#createbitmap)|初始化具有指定的宽度、 高度和位模式的内存设备相关位图对象。|  
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|初始化具有位图的宽度、 高度和 （如果指定） 的位模式中给出的对象**位图**结构。|  
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|初始化与位图的对象，以便它与指定的设备都兼容。|  
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|初始化与指定的设备兼容的可放弃位图对象。|  
|[CBitmap::FromHandle](#fromhandle)|返回一个指向`CBitmap`对象时给出到了 Windows 句柄`HBITMAP`位图。|  
|[CBitmap::GetBitmap](#getbitmap)|填充**位图**结构包含有关该位图的信息。|  
|[CBitmap::GetBitmapBits](#getbitmapbits)|将指定的位图的位复制到指定的缓冲区。|  
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|返回的宽度和位图的高度。 假定的高度和宽度以前已经设置了[SetBitmapDimension](#setbitmapdimension)成员函数。|  
|[Cbitmap:: Loadbitmap](#loadbitmap)|通过从应用程序的可执行文件加载的已命名的位图资源并将该位图附加到对象初始化的对象。|  
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|加载一张位图，并将颜色映射为当前的系统颜色。|  
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|通过加载预定义的 Windows 位图，并将该位图附加到对象初始化的对象。|  
|[CBitmap::SetBitmapBits](#setbitmapbits)|将位图的位设置为指定的位值。|  
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|将宽度和高度都分配给一个位图中 0.1 毫米为单位。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](#operator_hbitmap)|返回附加到的 Windows 句柄`CBitmap`对象。|  
  
## <a name="remarks"></a>备注  
 若要使用`CBitmap`对象，构造对象、 将位图句柄附加到它具有一个成员函数的初始化，然后调用对象的成员函数。  
  
 有关详细信息使用图形对象，如`CBitmap`，请参阅[图形对象](../../mfc/graphic-objects.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cbitmap"></a>CBitmap::CBitmap  
 构造 `CBitmap` 对象。  
  
```  
CBitmap();
```  
  
### <a name="remarks"></a>备注  
 必须使用一个成员函数的初始化初始化生成的对象。  
  
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
  
 尽管位图不能直接选择用于显示设备，它可以选择作为"内存设备上下文"的当前位图使用[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)并复制到任何兼容的设备上下文中使用[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)函数。  
  
 完成通过 `CBitmap` 函数创建的 `CreateBitmap` 对象后，首先选择设备上下文中的位图，然后删除 `CBitmap` 对象。  
  
 有关详细信息，请参见 **BITMAP** 结构中的 **bmBits** 字段的说明。 [位图](../../mfc/reference/bitmap-structure.md)结构做了介绍[CBitmap::CreateBitmapIndirect](#createbitmapindirect)成员函数。  
  
##  <a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect  
 初始化具有宽度、 高度和所指向的结构中给出的位模式 （如果指定） 的位图`lpBitmap`。  
  
```  
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```  
  
### <a name="parameters"></a>参数  
 `lpBitmap`  
 指向[位图](../../mfc/reference/bitmap-structure.md)结构，其中包含有关该位图的信息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 尽管位图不能直接选择用于显示设备，它可以选择作为内存设备上下文的当前位图使用[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)并复制到任何兼容的设备上下文中使用[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt)函数。 ( [CDC::PatBlt](../../mfc/reference/cdc-class.md#patblt)函数可以使当前画笔的位图将直接复制到显示设备上下文。)  
  
 如果**位图**指向结构`lpBitmap`使用已经填写参数`GetObject`函数，未指定位图的位，并且该位图未初始化。 若要初始化该位图，应用程序可以使用一个函数如[CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt)或[SetDIBits](http://msdn.microsoft.com/library/windows/desktop/dd162973)从中进行复制这些位的第一个参数标识的位图`CGdiObject::GetObject`到创建的位图`CreateBitmapIndirect`。  
  
 在使用完`CBitmap`创建与对象`CreateBitmapIndirect`函数，第一次选择从设备上下文的位图，然后删除`CBitmap`对象。  
  
##  <a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap  
 初始化与由指定的设备兼容的位图`pDC`。  
  
```  
BOOL CreateCompatibleBitmap(
    CDC* pDC,  
    int nWidth,  
    int nHeight);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指定设备上下文。  
  
 `nWidth`  
 指定位图的宽度（以像素为单位）。  
  
 `nHeight`  
 指定位图的高度（以像素为单位）。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 位图都有相同的颜色平面数或与指定的设备上下文相同的位每像素格式。 它可以选择是否符合指定的任何内存设备的当前位图作为`pDC`。  
  
 如果`pDC`是内存设备上下文中，返回位图在该设备上下文中具有相同的格式为当前所选的位图。 "内存设备上下文"是内存的一个表示显示图面块。 可用来将其复制到兼容的设备的实际显示图面之前准备在内存中的图像。  
  
 时都会创建一个内存设备上下文，GDI 将自动为其选择股票的单色位图。  
  
 由于颜色内存设备上下文可以具有颜色或选择的单色位图，位图的格式返回`CreateCompatibleBitmap`函数并不总是相同; 但是，为无内存设备上下文的兼容位图的格式并总是以设备的格式。  
  
 在使用完`CBitmap`创建与对象`CreateCompatibleBitmap`函数，第一次选择从设备上下文的位图，然后删除`CBitmap`对象。  
  
##  <a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap  
 初始化由标识的设备上下文与兼容的可放弃位图`pDC`。  
  
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
 位图都有相同的颜色平面数或与指定的设备上下文相同的位每像素格式。 应用程序可以选择将该位图作为是否符合指定的内存设备的当前位图`pDC`。  
  
 Windows 可以放弃创建此函数，仅当应用程序尚未选择它显示上下文的位图。 如果 Windows 在将时未选择和更高版本的应用程序尝试以选中它，丢弃位图[CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject)函数将返回**NULL**。  
  
 在使用完`CBitmap`创建与对象`CreateDiscardableBitmap`函数，第一次选择从设备上下文的位图，然后删除`CBitmap`对象。  
  
##  <a name="fromhandle"></a>CBitmap::FromHandle  
 返回一个指向`CBitmap`对象时提供给 Windows GDI 位图的句柄。  
  
```  
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>参数  
 `hBitmap`  
 指定 Windows GDI 位图。  
  
### <a name="return-value"></a>返回值  
 一个指向`CBitmap`对象成功，否则为如果**NULL**。  
  
### <a name="remarks"></a>备注  
 如果`CBitmap`对象尚未附加到该句柄，一种临时`CBitmap`创建对象并将其连接。 此临时`CBitmap`对象是否有效，仅直到下一次应用程序在其事件循环内有空闲时间，在该时间所有临时图形对象会被删除。 另一种说法是一个窗口消息处理过程才有效临时对象。  
  
##  <a name="getbitmap"></a>CBitmap::GetBitmap  
 检索附加位图图像属性。  
  
```  
int GetBitmap(BITMAP* pBitMap);
```  
  
### <a name="parameters"></a>参数  
 `pBitMap`  
 指向[位图结构](../../mfc/reference/bitmap-structure.md)结构，它将接收映像属性。 此参数不能为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则非零值否则为 0。  
  
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
 指向将接收该位图的缓冲区的指针。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则复制到缓冲区的字节数否则为 0。  
  
### <a name="remarks"></a>备注  
 使用[CBitmap::GetBitmap](#getbitmap)来确定所需的缓冲区大小。  
  
##  <a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension  
 返回的宽度和位图的高度。  
  
```  
CSize GetBitmapDimension() const;  
```  
  
### <a name="return-value"></a>返回值  
 宽度和高度在位图中，单位 0.1 毫米为单位。 高度处于**cy**的成员`CSize`对象，而宽度**cx**成员。 如果位图宽度和高度不通过使用已设置`SetBitmapDimension`，返回值为 0。  
  
### <a name="remarks"></a>备注  
 假定的高度和宽度以前已经设置了通过使用[SetBitmapDimension](#setbitmapdimension)成员函数。  
  
##  <a name="loadbitmap"></a>Cbitmap:: Loadbitmap  
 加载由名为的位图资源`lpszResourceName`或者标识的 ID 号`nIDResource`从应用程序的可执行文件。  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>参数  
 `lpszResourceName`  
 指向以 null 结尾的字符串，其中包含位图资源名称。  
  
 `nIDResource`  
 指定位图资源的资源 ID 号。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 加载的位图附加到`CBitmap`对象。  
  
 如果由标识位图`lpszResourceName`不存在或如果内存不足，无法加载位图，该函数返回 0。  
  
 您可以使用[CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject)可用于删除位图函数加载的`LoadBitmap`函数，或`CBitmap`析构函数将为你删除对象。  
  
> [!CAUTION]
>  删除对象之前，请确保不将其选入设备上下文。  
  
 下面的位图已添加到 3.1 及更高版本的 Windows 版本︰  
  
 **OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI**  
  
 3.0 版及更早版本的 Windows 版本的设备驱动程序中未找到这些位图。 位图，并会显示它们的外观的完整列表，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap  
 调用该成员函数以加载位图并映射到当前的系统颜色的颜色。  
  
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
 一个标志的位图。 可为零或**CMB_MASKED**。  
  
 `lpColorMap`  
 一个指向**颜色映射**结构，其中包含要映射位图所需的颜色信息。 如果此参数为**NULL**，该函数使用默认的颜色映射。  
  
 *nMapSize*  
 指向的颜色映射数`lpColorMap`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，`LoadMappedBitmap`目录结构将映射通常用在按钮的标志符号的颜色。  
  
 有关创建映射的位图的信息，请参阅 Windows 函数[CreateMappedBitmap](http://go.microsoft.com/fwlink/linkid=230562)和[颜色映射](http://msdn.microsoft.com/library/windows/desktop/bb760448)结构中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap  
 加载 Windows 所使用的预定义的位图。  
  
```  
BOOL LoadOEMBitmap(UINT nIDBitmap);
```  
  
### <a name="parameters"></a>参数  
 `nIDBitmap`  
 预定义的 Windows 位图的 ID 号。 从 WINDOWS 下面列出了可能的值。H:  
  
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
 位图名称开头**OBM_OLD**表示使用 3.0 之前的 Windows 版本的位图。  
  
 请注意，该常数**OEMRESOURCE**包括 WINDOWS 之前必须进行定义。为了使用其中任何 H **OBM_**常量。  
  
##  <a name="operator_hbitmap"></a>CBitmap::operator HBITMAP  
 使用此运算符将获得附加的 Windows GDI 句柄的`CBitmap`对象。  
  
```  
operator HBITMAP() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，Windows GDI 对象的句柄由表示`CBitmap`对象; 否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 此运算符被强制转换运算符，它支持直接使用`HBITMAP`对象。  
  
 有关使用图形对象的详细信息，请参阅[图形对象](http://msdn.microsoft.com/library/windows/desktop/dd144962)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setbitmapbits"></a>CBitmap::SetBitmapBits  
 将位图的位设置为通过给出的位值`lpBits`。  
  
```  
DWORD SetBitmapBits(
    DWORD dwCount,  
    const void* lpBits);
```  
  
### <a name="parameters"></a>参数  
 `dwCount`  
 指定所指向的字节数`lpBits`。  
  
 `lpBits`  
 指向**字节**数组，其中包含要复制到的像素值`CBitmap`对象。 为了能够正确地呈现其图像的位图，值应进行格式设置以符合 CBitmap 实例创建时指定的高度、 宽度和颜色深度值。 有关详细信息，请参阅[CBitmap::CreateBitmap](#createbitmap)。  
  
### <a name="return-value"></a>返回值  
 将位图位; 设置中使用的字节数如果该函数将失败，则为 0。  
  
##  <a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension  
 将宽度和高度都分配给一个位图中 0.1 毫米为单位。  
  
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
 以前的位图尺寸。 高度处于**cy**成员变量`CSize`对象，而宽度**cx**成员变量。  
  
### <a name="remarks"></a>备注  
 GDI 不使用这些值，但若要返回其应用程序调用除外[GetBitmapDimension](#getbitmapdimension)成员函数。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 MDI](../../visual-cpp-samples.md)   
 [CGdiObject 类](../../mfc/reference/cgdiobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


