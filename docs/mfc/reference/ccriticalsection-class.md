---
title: CCriticalSection 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
dev_langs:
- C++
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d6e713f6d5238d99af8f9311eb05a4b2dd39f7b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="ccriticalsection-class"></a>CCriticalSection 类
表示一个"临界区"-每次访问资源或代码段的允许一个线程的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCriticalSection::CCriticalSection](#ccriticalsection)|构造 `CCriticalSection` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CCriticalSection::Lock](#lock)|用于访问`CCriticalSection`对象。|  
|[CCriticalSection::Unlock](#unlock)|释放 `CCriticalSection` 对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|检索指向内部**CRITICAL_SECTION**对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CCriticalSection::m_sect](#m_sect)|A **CRITICAL_SECTION**对象。|  
  
## <a name="remarks"></a>备注  
 一次只有一个线程可以有权修改数据或某个其他受控的资源时，关键部分很有用。 例如，如果将节点添加到链接的列表中，则是应仅允许一个线程通过一次一个过程。 通过使用`CCriticalSection`对象以控制链接的列表中，仅一次一个线程可以获得对列表的访问。  
  
> [!NOTE]
>  功能`CCriticalSection`类提供的实际 Win32 **CRITICAL_SECTION**对象。  
  
 临界区代替互斥体 (请参阅[CMutex](../../mfc/reference/cmutex-class.md)) 时速度非常重要而且资源不会使用跨进程边界。  
  
 有两种方法来使用`CCriticalSection`对象： 独立和嵌入类中。  
  
-   要使用独立的独立方法`CCriticalSection`对象，构造`CCriticalSection`对象时需要它。 后从构造函数成功返回时，显式锁定的对象通过调用[锁](#lock)。 调用[解锁](#unlock)完成后访问关键部分。 此方法时更清晰的某个人可以读取你的源代码，很多容易导致错误您还必须记得地锁定和解锁的关键部分之前和之后访问。  
  
     多更可取方法是使用[CSingleLock](../../mfc/reference/csinglelock-class.md)类。 它还具有`Lock`和`Unlock`方法，但你无需担心取消锁定资源，如果发生异常。  
  
-   嵌入方法，你还可以共享一个类与多个线程通过添加`CCriticalSection`-类和锁定时所需的数据成员的类型数据成员。  
  
 有关详细信息使用`CCriticalSection`对象，请参阅文章[多线程处理： 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## <a name="requirements"></a>要求  
 **标头：** afxmt.h  
  
##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection  
 构造 `CCriticalSection` 对象。  
  
```  
CCriticalSection();
```  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CCriticalSection`对象，请创建[CSingleLock](../../mfc/reference/csinglelock-class.md)对象并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果`CCriticalSection`对象正在使用独立，调用其[解锁](#unlock)成员函数以将其释放。  
  
 如果构造函数无法分配所需的系统内存，内存不足异常 (类型的[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) 自动引发。  
  
### <a name="example"></a>示例  
  请参阅示例[CCriticalSection::Lock](#lock)。  
  
##  <a name="lock"></a>  CCriticalSection::Lock  
 调用此成员函数可访问的关键部分对象。  
  
```  
BOOL Lock();  
BOOL Lock(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>参数  
 `dwTimeout`  
 `Lock` 将忽略此参数值。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零否则为 0。  
  
### <a name="remarks"></a>备注  
 `Lock` 是一个不会返回之前的关键部分对象处于有信号状态的阻塞调用 （可用时）。  
  
 如果已超时的等待是必需的则可以使用[CMutex](../../mfc/reference/cmutex-class.md)对象而不是`CCriticalSection`对象。  
  
 如果`Lock`无法分配必需的系统内存，内存不足异常 (类型的[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) 自动引发。  
  
### <a name="example"></a>示例  
 此示例演示通过控制对共享资源的访问的嵌套的关键部分方法 (静态`_strShared`对象) 使用共享`CCriticalSection`对象。 `SomeMethod`函数演示了以安全方式更新共享的资源。  
  
 [!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]  
  
##  <a name="m_sect"></a>  CCriticalSection::m_sect  
 包含由所有关键部分对象`CCriticalSection`方法。  
  
```  
CRITICAL_SECTION m_sect;  
```  
  
##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator CRITICAL_SECTION *  
 检索**CRITICAL_SECTION**对象。  
  
```  
operator CRITICAL_SECTION*();
```   
  
### <a name="remarks"></a>备注  
 调用此函数可检索到内部指针**CRITICAL_SECTION**对象。  
  
##  <a name="unlock"></a>  CCriticalSection::Unlock  
 版本`CCriticalSection`以供另一个线程的对象。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>返回值  
 非零如果`CCriticalSection`线程所拥有对象和版本已成功; 否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`CCriticalSection`正在使用独立的`Unlock`必须在完成使用由关键部分控制的资源后立即调用。 如果[CSingleLock](../../mfc/reference/csinglelock-class.md)对象正在使用，`CCriticalSection::Unlock`将由锁对象的调用`Unlock`成员函数。  
  
### <a name="example"></a>示例  
  请参阅示例[CCriticalSection::Lock](#lock)。  
  
## <a name="see-also"></a>请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMutex 类](../../mfc/reference/cmutex-class.md)
