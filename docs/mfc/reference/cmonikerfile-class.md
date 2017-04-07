---
title: "CMonikerFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
dev_langs:
- C++
helpviewer_keywords:
- CMonikerFile class
- monikers, MFC
- IMoniker interface, binding
- IMoniker interface
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 0f348328a4be4b934e00acdb43ba47fa919bac75
ms.lasthandoff: 04/01/2017

---
# <a name="cmonikerfile-class"></a>CMonikerFile 类
表示数据的流 ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)) 通过名为[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)。  
  
## <a name="syntax"></a>语法  
  
```  
class CMonikerFile : public COleStreamFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMonikerFile::CMonikerFile](#cmonikerfile)|构造 `CMonikerFile` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|分离和释放流并释放名字对象。|  
|[CMonikerFile::Detach](#detach)|分离`IMoniker`从此`CMonikerFile`对象。|  
|[CMonikerFile::GetMoniker](#getmoniker)|返回当前的名字对象。|  
|[CMonikerFile::Open](#open)|打开指定的文件，以获取流。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|获取绑定上下文，或创建的默认初始化绑定上下文。|  
  
## <a name="remarks"></a>备注  
 标记包含类似于文件的路径名的信息。 如果你有一个指针指向标记对象的`IMoniker`接口，你可以无需任何其他特定的信息，有关该文件所在位置实际获取到的被标识文件的访问权限。  
  
 派生自`COleStreamFile`，`CMonikerFile`采用名字对象或可成为名字对象的字符串表示形式并将绑定到名字对象为其名称的流。 然后，你可以读取并写入该流。 实际用途`CMonikerFile`是提供简单访问`IStream`s 命名`IMoniker`s，以便无需自己，绑定流尚未具有`CFile`写入流的功能。  
  
 `CMonikerFile`不能用于绑定到流之外的任何内容。 如果你想要将绑定到存储或一个对象，则必须使用`IMoniker`直接接口。  
  
 流和名字对象的详细信息，请参阅[COleStreamFile](../../mfc/reference/colestreamfile-class.md)中*MFC 参考*和[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="close"></a>CMonikerFile::Close  
 调用此函数分离并释放流并释放名字对象。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 可以在未打开或已关闭流上调用。  
  
##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile  
 构造 `CMonikerFile` 对象。  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>CMonikerFile::CreateBindContext  
 调用此函数可创建默认初始化绑定上下文。  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>参数  
 `pError`  
 指向文件异常的指针。 发生错误，必须先将它设置为可能的原因。  
  
### <a name="return-value"></a>返回值  
 绑定上下文的指针[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)要成功; 否则为如果将绑定具有**NULL**。 如果实例通过打开`IBindHost`接口，从检索的绑定上下文`IBindHost`。 如果没有任何`IBindHost`界面无法返回的绑定上下文，则创建的绑定上下文。 有关的说明[IBindHost](http://msdn.microsoft.com/library/ie/ms775076)接口，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 绑定上下文是存储有关特定的名字对象绑定操作的信息的对象。 你可以重写此函数可提供一个自定义绑定的上下文。  
  
##  <a name="detach"></a>CMonikerFile::Detach  
 调用此函数可关闭的流。  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pError`  
 指向文件异常的指针。 发生错误，必须先将它设置为可能的原因。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="getmoniker"></a>CMonikerFile::GetMoniker  
 调用此函数可检索指向当前标记的指针。  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前的名字对象接口的指针 ( [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705))。  
  
### <a name="remarks"></a>备注  
 由于`CMonikerFile`不是一个接口，返回的指针引用不递增引用计数 (通过[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379))，并释放标记时`CMonikerFile`释放对象。 如果你想要保存到名字对象或释放它自己，则必须`AddRef`它。  
  
##  <a name="open"></a>CMonikerFile::Open  
 调用此成员函数，以打开文件或标记的对象。  
  
```  
virtual BOOL Open(
    LPCTSTR lpszURL,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    IMoniker* pMoniker,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszURL`  
 URL 或要打开的文件的文件名。  
  
 `pError`  
 指向文件异常的指针。 发生错误，必须先将它设置为可能的原因。  
  
 `pMoniker`  
 指向名字对象接口的指针`IMoniker`用于获取的流。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `lpszURL`参数不能用于在 Macintosh 上。 仅`pMoniker`形式**打开**可以在 Macintosh 上使用。  
  
 你可以使用 URL 或文件名`lpszURL`参数。 例如：  
  
 [!code-cpp[NVC_MFCWinInet # 6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - 或 -  
  
 [!code-cpp[NVC_MFCWinInet # 7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [COleStreamFile 类](../../mfc/reference/colestreamfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)

