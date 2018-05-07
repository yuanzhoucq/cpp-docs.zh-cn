---
title: CCachedDataPathProperty 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29e46f7e65d6c2f9b5c0d29007cd31f660754957
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty 类
实现异步传输并在内存文件中缓冲的 OLE 控件属性。  
  
## <a name="syntax"></a>语法  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|构造 `CCachedDataPathProperty` 对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` 在其中缓存数据的对象。|  
  
## <a name="remarks"></a>备注  
 内存文件存储在 RAM 中，而不是在磁盘上，并可用于快速临时传输。  
  
 连同**CAysncMonikerFile**和`CDataPathProperty`，`CCachedDataPathProperty`异步名字对象中 OLE 控件用于提供功能。 与`CCachedDataPathProperty`对象，你将能够从 URL 或文件的源以异步方式传输数据，并将其存储在内存文件通过`m_Cache`公共变量。 所有数据都存储在内存文件中，并且没有无需重写[OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)除非你想要观看通知并做出响应。 例如，如果要传输较大。GIF 文件并想要更多的数据已到达，它应重绘自己，通知你的控件重写`OnDataAvailable`进行通知。  
  
 类`CCachedDataPathProperty`派生自`CDataPathProperty`。  
  
 有关如何在 Internet 应用程序中使用异步名字对象和 ActiveX 控件的详细信息，请参阅以下主题：  
  
- [Internet 前几个步骤： ActiveX 控件](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet 前几个步骤： 异步名字对象](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>要求  
 **标头：** afxctl.h  
  
##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty  
 构造 `CCachedDataPathProperty` 对象。  
  
```  
CCachedDataPathProperty(COleControl* pControl = NULL);

 
CCachedDataPathProperty(
    LPCTSTR lpszPath,  
    COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pControl`  
 指向要与此关联的 ActiveX 控件对象的指针`CCachedDataPathProperty`对象。  
  
 `lpszPath`  
 路径，这可能是绝对或相对，用于创建异步名字对象引用的属性的实际绝对位置。 `CCachedDataPathProperty` 使用 Url，不是文件名。 如果你想`CCachedDataPathProperty`对象文件中，前面预置 file:// 到路径。  
  
### <a name="remarks"></a>备注  
 `COleControl`指向对象`pControl`由[打开](../../mfc/reference/cdatapathproperty-class.md#open)和检索由派生类。 如果`pControl`是**NULL**，与所使用的控件**打开**应与设置[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)。 如果`lpszPath`是**NULL**，可以在路径中，通过传递**打开**或将其与设置[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)。  
  
##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache  
 包含在其中缓存数据的内存文件的类名称。  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>备注  
 在 RAM 中，而不是在磁盘上存储的内存文件。  
  
## <a name="see-also"></a>请参阅  
 [CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)
