---
title: "CAtlTemporaryFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
dev_langs: C++
helpviewer_keywords: CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5911de856d13d9d66e8c950d446083a36811f535
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile 类
此类提供用于创建和使用的临时文件的方法。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CAtlTemporaryFile
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|构造函数。|  
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlTemporaryFile::Close](#close)|调用此方法关闭临时文件，而且，可以删除其内容或将它们存储在指定的文件名。|  
|[CAtlTemporaryFile::Create](#create)|调用此方法以创建临时文件。|  
|[CAtlTemporaryFile::Flush](#flush)|调用此方法以强制将文件缓冲区写入到临时文件中剩余的任何数据。|  
|[CAtlTemporaryFile::GetPosition](#getposition)|调用此方法以获取当前文件指针位置。|  
|[CAtlTemporaryFile::GetSize](#getsize)|调用此方法以获取以字节为单位的临时文件的大小。|  
|[CAtlTemporaryFile::HandsOff](#handsoff)|调用此方法以从文件取消关联`CAtlTemporaryFile`对象。|  
|[CAtlTemporaryFile::HandsOn](#handson)|调用此方法以打开现有的临时文件并将该文件末尾的指针。|  
|[CAtlTemporaryFile::LockRange](#lockrange)|调用此方法以锁定以防止其他进程对其进行访问的文件中的一个区域。|  
|[CAtlTemporaryFile::Read](#read)|调用此方法以从文件指针指示的位置开始的临时文件中读取数据。|  
|[CAtlTemporaryFile::Seek](#seek)|调用此方法来移动文件指针的临时文件。|  
|[CAtlTemporaryFile::SetSize](#setsize)|调用此方法以设置临时文件的大小。|  
|[CAtlTemporaryFile::TempFileName](#tempfilename)|调用此方法以返回临时文件的名称。|  
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|调用此方法以解锁的临时文件的区域。|  
|[CAtlTemporaryFile::Write](#write)|调用此方法以将数据写入到临时文件从文件指针指示的位置开始。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CAtlTemporaryFile::operator 句柄](#operator_handle)|返回临时文件的句柄。|  
  
## <a name="remarks"></a>备注  
 `CAtlTemporaryFile`可以轻松创建和使用的临时文件。 自动名为、 打开、 关闭和删除文件。 如果关闭该文件后，该文件的内容是必需的可以将它们保存到具有指定名称的新文件。  
  
## <a name="requirements"></a>惠?  
 **标头：** atlfile.h  
  
## <a name="example"></a>示例  
 请参阅示例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile  
 构造函数。  
  
```
CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>备注  
 文件未实际打开之前调用了[CAtlTemporaryFile::Create](#create)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile  
 析构函数。  
  
```
~CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>备注  
 析构函数调用[CAtlTemporaryFile::Close](#close)。  
  
##  <a name="close"></a>CAtlTemporaryFile::Close  
 调用此方法关闭临时文件，而且，可以删除其内容或将它们存储在指定的文件名。  
  
```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 *szNewName*  
 新的文件存储中的临时文件的内容的名称。 如果此参数为 NULL，删除临时文件的内容。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="create"></a>CAtlTemporaryFile::Create  
 调用此方法以创建临时文件。  
  
```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```  
  
### <a name="parameters"></a>参数  
 `pszDir`  
 临时文件的路径。 如果这是 NULL， [GetTempPath](http://msdn.microsoft.com/library/windows/desktop/aa364992)将调用以将分配一个路径。  
  
 `dwDesiredAccess`  
 所需的访问。 请参阅`dwDesiredAccess`中[CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) Windows SDK 中。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="flush"></a>CAtlTemporaryFile::Flush  
 调用此方法以强制将文件缓冲区写入到临时文件中剩余的任何数据。  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 类似于[CAtlTemporaryFile::HandsOff](#handsoff)，只不过不关闭该文件。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="getposition"></a>CAtlTemporaryFile::GetPosition  
 调用此方法以获取当前文件指针位置。  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 以字节为单位位置。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 若要更改的文件指针位置，请使用[CAtlTemporaryFile::Seek](#seek)。  
  
##  <a name="getsize"></a>CAtlTemporaryFile::GetSize  
 调用此方法以获取以字节为单位的临时文件的大小。  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>参数  
 `nLen`  
 文件中的字节数。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff  
 调用此方法以从文件取消关联`CAtlTemporaryFile`对象。  
  
```
HRESULT HandsOff() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 `HandsOff`和[CAtlTemporaryFile::HandsOn](#handson)用于解除关联的文件从该对象，并根据需要将其重新附加。 `HandsOff`将强制写入到临时文件，将文件缓冲区中剩余的任何数据，然后关闭该文件。 如果你想要关闭并永久删除该文件，或如果你想要关闭和保留具有给定名称的文件的内容，请使用[CAtlTemporaryFile::Close](#close)。  
  
##  <a name="handson"></a>CAtlTemporaryFile::HandsOn  
 调用此方法以打开现有的临时文件并将该文件末尾的指针。  
  
```
HRESULT HandsOn() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 [CAtlTemporaryFile::HandsOff](#handsoff)和`HandsOn`用于解除关联的文件从该对象，并根据需要将其重新附加。  
  
##  <a name="lockrange"></a>CAtlTemporaryFile::LockRange  
 调用此方法以锁定以防止其他进程对其进行访问的临时文件中的一个区域。  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 锁应从其中开始文件中的位置。  
  
 `nCount`  
 要锁定的字节范围的长度。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 锁定文件中的字节将阻止其他进程访问这些字节。 你可以锁定多个区域一个文件，但不重叠的区域允许。 若要成功解除区域，使用[CAtlTemporaryFile::UnlockRange](#unlockrange)，确保字节范围完全对应以前锁定的区域。 `LockRange`不会合并相邻区域;如果两个锁定的区域相邻，你必须单独将每个解锁。  
  
##  <a name="operator_handle"></a>CAtlTemporaryFile::operator 句柄  
 返回临时文件的句柄。  
  
```  
operator HANDLE() throw();
```  
  
##  <a name="read"></a>CAtlTemporaryFile::Read  
 调用此方法以从文件指针指示的位置开始的临时文件中读取数据。  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```  
  
### <a name="parameters"></a>参数  
 `pBuffer`  
 指向将接收从文件中读取的数据缓冲区的指针。  
  
 `nBufSize`  
 缓冲区大小（以字节为单位）。  
  
 `nBytesRead`  
 读取的字节数。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 调用[CAtlFile::Read](../../atl/reference/catlfile-class.md#read)。 若要更改的文件指针的位置，请调用[CAtlTemporaryFile::Seek](#seek)。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="seek"></a>CAtlTemporaryFile::Seek  
 调用此方法来移动文件指针的临时文件。  
  
```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>参数  
 `nOffset`  
 偏移量，以字节为单位，从给定的起始点*dwFrom。*  
  
 `dwFrom`  
 起始点 （FILE_BEGIN、 FILE_CURRENT 或 FILE_END）。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 调用[CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek)。 若要获取当前文件指针位置，调用[CAtlTemporaryFile::GetPosition](#getposition)。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
##  <a name="setsize"></a>CAtlTemporaryFile::SetSize  
 调用此方法以设置临时文件的大小。  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>参数  
 `nNewLen`  
 以字节为单位文件的新长度。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 调用[CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize)。 返回时，文件指针定位在文件末尾。  
  
##  <a name="tempfilename"></a>CAtlTemporaryFile::TempFileName  
 调用此方法以返回临时文件的名称。  
  
```
LPCTSTR TempFileName() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回`LPCTSTR`指向的文件名称。  
  
### <a name="remarks"></a>备注  
 在中生成的文件名称[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)通过调用[GetTempFile](http://msdn.microsoft.com/library/windows/desktop/aa364991)Windows SDK 函数。 临时文件，文件扩展名将始终为"TFR"。  
  
##  <a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange  
 调用此方法以解锁的临时文件的区域。  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 解锁应从其中开始文件中的位置。  
  
 `nCount`  
 要解锁的字节范围的长度。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 调用[CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange)。  
  
##  <a name="write"></a>CAtlTemporaryFile::Write  
 调用此方法以将数据写入到临时文件从文件指针指示的位置开始。  
  
```
HRESULT Write(  
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```  
  
### <a name="parameters"></a>参数  
 `pBuffer`  
 包含要写入到文件的数据的缓冲区。  
  
 `nBufSize`  
 要从缓冲区中传输的字节数。  
  
 `pnBytesWritten`  
 写入的字节数。  
  
### <a name="return-value"></a>返回值  
 返回`S_OK`成功，则错误`HRESULT`失败。  
  
### <a name="remarks"></a>备注  
 调用[CAtlFile::Write](../../atl/reference/catlfile-class.md#write)。  
  
### <a name="example"></a>示例  
 请参阅示例[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../../atl/atl-class-overview.md)   
 [CAtlFile 类](../../atl/reference/catlfile-class.md)
