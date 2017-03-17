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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4668672af1b33170ece1cb4d449ed5a20f6040e7
ms.lasthandoff: 02/24/2017

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
  
|名称|说明|  
|----------|-----------------|  
|[CMonikerFile::Close](#close)|分离和释放流并释放名字对象。|  
|[CMonikerFile::Detach](#detach)|分离`IMoniker`从此`CMonikerFile`对象。|  
|[CMonikerFile::GetMoniker](#getmoniker)|返回当前名字对象。|  
|[CMonikerFile::Open](#open)|打开指定的文件，以获取流。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMonikerFile::CreateBindContext](#createbindcontext)|获取绑定上下文，则创建默认情况下初始化绑定上下文。|  
  
## <a name="remarks"></a>备注  
 一个名字对象包含与某个文件的路径名非常相似的信息。 如果您有一个指针指向一个名字对象`IMoniker`接口，您可以获得被标识文件而无关于文件的实际所在位置的其他任何具体信息。  
  
 派生自`COleStreamFile`，`CMonikerFile`采用一个名字对象或可成为名字对象的字符串表示形式，并将绑定到名字对象为其名称的流。 然后，您可以读取和写入到该流。 真正目的`CMonikerFile`是可以方便地访问到`IStream`s 命名`IMoniker`s，因此不需要自己，绑定流尚没有`CFile`写入流的功能。  
  
 `CMonikerFile`不能用于为流以外的任何绑定。 如果你想要将绑定到存储或对象，则必须使用`IMoniker`直接接口。  
  
 流和名字对象的详细信息，请参阅[COleStreamFile](../../mfc/reference/colestreamfile-class.md)中*MFC 参考*和[IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)和[IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 `CMonikerFile`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="close"></a>CMonikerFile::Close  
 调用此函数以了解分离然后释放流并释放名字对象。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>备注  
 可以对未打开还是已关闭的流调用。  
  
##  <a name="cmonikerfile"></a>CMonikerFile::CMonikerFile  
 构造 `CMonikerFile` 对象。  
  
```  
CMonikerFile();
```  
  
##  <a name="createbindcontext"></a>CMonikerFile::CreateBindContext  
 调用此函数可创建默认情况下初始化的绑定上下文。  
  
```  
IBindCtx* CreateBindContext(CFileException* pError);
```  
  
### <a name="parameters"></a>参数  
 `pError`  
 一个指向文件例外。 如果出现错误，必须先将它设置为原因。  
  
### <a name="return-value"></a>返回值  
 绑定上下文的指针[IBindCtx](http://msdn.microsoft.com/library/windows/desktop/ms693755)要与绑定，如果成功，否则为**NULL**。 如果该实例通过打开`IBindHost`接口，从检索的绑定上下文`IBindHost`。 如果没有任何`IBindHost`界面出现故障时要返回的绑定上下文，都会创建一个绑定上下文。 有关的说明[IBindHost](http://msdn.microsoft.com/library/ie/ms775076)接口，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 绑定上下文是存储特定的名字对象绑定操作有关的信息的对象。 您可以重写此函数可提供自定义绑定上下文。  
  
##  <a name="detach"></a>CMonikerFile::Detach  
 调用此函数可关闭流。  
  
```  
BOOL Detach(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pError`  
 一个指向文件例外。 如果出现错误，必须先将它设置为原因。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
##  <a name="getmoniker"></a>CMonikerFile::GetMoniker  
 调用此函数可检索的当前名字对象的指针。  
  
```  
IMoniker* GetMoniker() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向当前名字对象接口的指针 ( [IMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679705))。  
  
### <a name="remarks"></a>备注  
 由于`CMonikerFile`不是一个接口，返回的指针引用不递增引用计数 (通过[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379))，并释放标记时`CMonikerFile`释放对象。 如果您想要保存到名字对象或自己释放，则必须`AddRef`它。  
  
##  <a name="open"></a>CMonikerFile::Open  
 调用该成员函数以打开文件或名字对象的对象。  
  
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
 一个指向文件例外。 如果出现错误，必须先将它设置为原因。  
  
 `pMoniker`  
 指向名字对象接口的指针`IMoniker`要用于获得的流。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 `lpszURL`参数不能用于在 Macintosh 上。 仅`pMoniker`形式**打开**可以在 Macintosh 上使用。  
  
 可以使用的 URL 或文件名`lpszURL`参数。 例如:   
  
 [!code-cpp[NVC_MFCWinInet #&6;](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]  
  
 - 或 -  
  
 [!code-cpp[NVC_MFCWinInet #&7;](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [COleStreamFile 类](../../mfc/reference/colestreamfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)

