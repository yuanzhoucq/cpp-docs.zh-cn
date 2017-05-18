---
title: "CMetaFileDC 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
dev_langs:
- C++
helpviewer_keywords:
- CMetaFileDC class
- Windows metafiles [C++]
- metafiles, implementing
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
caps.latest.revision: 23
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
ms.openlocfilehash: 4bff4d7601c4ffbc6fe5cbe73f5e057b79abf1e5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cmetafiledc-class"></a>CMetaFileDC 类
实现一个 Windows 图元文件，此文件包含一系列图形设备接口 (GDI) 命令，你可以重播此命令来创建所需图像或文本。  
  
## <a name="syntax"></a>语法  
  
```  
class CMetaFileDC : public CDC  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|构造 `CMetaFileDC` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMetaFileDC::Close](#close)|关闭设备上下文，并创建一个图元文件句柄。|  
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|关闭增强型图元文件设备上下文，并创建增强型图元文件句柄。|  
|[CMetaFileDC::Create](#create)|创建 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。|  
|[CMetaFileDC::CreateEnhanced](#createenhanced)|创建增强型格式图元文件的图元文件设备上下文。|  
  
## <a name="remarks"></a>备注  
 若要实现 Windows 图元文件，请首先创建`CMetaFileDC`对象。 调用`CMetaFileDC`构造函数中，然后调用[创建](#create)成员函数，创建 Windows 图元文件设备上下文，并将其附加到它`CMetaFileDC`对象。  
  
 接下来发送`CMetaFileDC`对象的序列`CDC`GDI 的命令，在你计划它来重播。 创建输出，如那些 GDI 命令`MoveTo`和`LineTo`，可以使用。  
  
 所需的命令发送给图元文件后，调用**关闭**成员函数，其关闭图元文件设备上下文，并且返回的图元文件句柄。 然后释放`CMetaFileDC`对象。  
  
 [CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)然后可以使用图元文件句柄图元文件中重复播放。 图元文件还可以通过 Windows 函数如[CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)，它将图元文件复制到磁盘。  
  
 当不再需要图元文件时，它从内存中删除与[DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537) Windows 函数。  
  
 您还可以实现`CMetaFileDC`对象，以便它可以处理输出调用，同时特性 GDI 调用如`GetTextExtent`。 此类图元文件更灵活的详细信息可以轻松地重用常规的 GDI 代码，通常包含多个输出和属性调用。 `CMetaFileDC`类继承的两个设备上下文、`m_hDC`和`m_hAttribDC`，从`CDC`。 `m_hDC`设备上下文可以处理所有[CDC](../../mfc/reference/cdc-class.md) GDI 输出调用和`m_hAttribDC`设备上下文可以处理所有`CDC`GDI 属性调用。 通常情况下，下面的两个设备上下文引用同一个设备。 情况下`CMetaFileDC`，DC 的属性设置为**NULL**默认情况下。  
  
 创建指向屏幕、 打印机或设备不图元文件，然后调用的第二个设备上下文`SetAttribDC`成员函数以将与新的设备上下文相关联`m_hAttribDC`。 有关信息的 GDI 调用现在都定向到新`m_hAttribDC`。 输出 GDI 调用将转到`m_hDC`，它表示该图元文件。  
  
 有关详细信息`CMetaFileDC`，请参阅[设备上下文](../../mfc/device-contexts.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CMetaFileDC`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="close"></a>CMetaFileDC::Close  
 关闭图元文件设备上下文，并创建一个 Windows 图元文件句柄，可用于播放使用图元文件[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile)成员函数。  
  
```  
HMETAFILE Close();
```  
  
### <a name="return-value"></a>返回值  
 一个有效**HMETAFILE**如果该函数成功，否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 Windows 图元文件句柄还可用于操作 Windows 函数与图元文件，如[CopyMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183480)。  
  
 在使用后通过调用 Windows 删除图元文件[DeleteMetaFile](http://msdn.microsoft.com/library/windows/desktop/dd183537)函数。  
  
##  <a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced  
 关闭增强型图元文件设备上下文，并返回标识增强格式图元文件的句柄。  
  
```  
HENHMETAFILE CloseEnhanced();
```  
  
### <a name="return-value"></a>返回值  
 增强型图元文件，如果成功，则一个句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 应用程序可以使用此函数返回的增强型图元文件句柄来执行以下任务︰  
  
-   显示存储在增强型图元文件中的图片  
  
-   创建增强型图元文件的副本  
  
-   枚举、 编辑或复制单个记录中的增强型图元文件  
  
-   增强型图元文件标头中检索的图元文件内容的可选描述  
  
-   检索的增强型图元文件标头的副本  
  
-   检索二进制增强型图元文件的副本  
  
-   枚举可选调色板中的颜色  
  
-   将增强型格式图元文件转换为 Windows 格式图元文件  
  
 当应用程序不再需要的增强型图元文件句柄时，它应释放该句柄，通过调用 Win32 **DeleteEnhMetaFile**函数。  
  
##  <a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC  
 构造`CMetaFileDC`两个步骤中的对象。  
  
```  
CMetaFileDC();
```  
  
### <a name="remarks"></a>备注  
 首先，调用`CMetaFileDC`，然后调用**创建**，它创建 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。  
  
##  <a name="create"></a>CMetaFileDC::Create  
 构造`CMetaFileDC`两个步骤中的对象。  
  
```  
BOOL Create(LPCTSTR lpszFilename = NULL);
```  
  
### <a name="parameters"></a>参数  
 *lpszFilename*  
 指向以 null 结尾的字符串。 指定图元文件来创建的文件名。 如果*lpszFilename*是**NULL**，创建一个新的内存中的图元文件。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为非 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 首先，调用构造函数`CMetaFileDC`，然后调用**创建**，它创建 Windows 图元文件设备上下文，并将其附加到`CMetaFileDC`对象。  
  
##  <a name="createenhanced"></a>CMetaFileDC::CreateEnhanced  
 创建增强型格式图元文件设备上下文。  
  
```  
BOOL CreateEnhanced(
    CDC* pDCRef,  
    LPCTSTR lpszFileName,  
    LPCRECT lpBounds,  
    LPCTSTR lpszDescription);
```  
  
### <a name="parameters"></a>参数  
 `pDCRef`  
 标识用于增强型图元文件的引用设备。  
  
 `lpszFileName`  
 指向以 null 结尾的字符串。 指定要创建增强型图元文件的文件名。 如果此参数为**NULL**，增强型图元文件为基于内存的丢失或时销毁该对象及其内容 Win32 **DeleteEnhMetaFile**调用函数。  
  
 `lpBounds`  
 指向[RECT](../../mfc/reference/rect-structure1.md)数据结构或[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定的尺寸以**HIMETRIC**单位 （以&0;.1 毫米增量） 的图片存储在增强型图元文件中。  
  
 `lpszDescription`  
 指向以零结尾的字符串，指定创建该图片，以及图片的标题的应用程序的名称。  
  
### <a name="return-value"></a>返回值  
 增强型图元文件，如果成功，则设备上下文句柄否则为**NULL**。  
  
### <a name="remarks"></a>备注  
 该 DC 可以用于存储独立于设备的图片。  
  
 Windows 使用标识的引用设备`pDCRef`参数，以记录的解决方法和图片最初出现的设备的单位。 如果`pDCRef`参数是**NULL**，它使用当前的显示设备进行引用。  
  
 Left 和 top 成员`RECT`指向数据结构`lpBounds`参数必须是小于右边和底边成员分别。 在图片中包含的矩形的边缘点时。 如果`lpBounds`是**NULL**，图形设备接口 (GDI) 计算可以在将包含由应用程序绘制图片的最小矩形的尺寸。 `lpBounds`应提供参数，在可能的情况。  
  
 指向的字符串`lpszDescription`参数必须包含 null 字符的应用程序名称和图片名称之间，并且必须使用两个 null 字符结束 — 例如，"XYZ 图形 Editor\0Bald Eagle\0\0，"\0 其中表示 null 字符。 如果`lpszDescription`是**NULL**，增强型图元文件标头中没有对应项。  
  
 应用程序使用此函数创建的 DC 将图形图片存储在增强型图元文件。 用于标识该 DC 的句柄可以传递给任何 GDI 函数。  
  
 应用程序将图片存储在增强型图元文件后，它可以显示该图片在任何输出设备上通过调用`CDC::PlayMetaFile`函数。 Windows 在显示该图片，请使用指向该矩形`lpBounds`参数，并从引用设备来定位和缩放图片的分辨率数据。 此函数返回的设备上下文包含同一个与任何新 DC 相关联的默认属性。  
  
 应用程序必须使用 Win32 **GetWinMetaFileBits**函数将增强型图元文件转换为较旧的 Windows 图元文件格式。  
  
 应使用增强型图元文件的文件名。EMF 扩展。  
  
## <a name="see-also"></a>另请参阅  
 [CDC 类](../../mfc/reference/cdc-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




