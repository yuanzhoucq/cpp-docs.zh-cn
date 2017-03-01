---
title: "CCriticalSection 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCriticalSection
dev_langs:
- C++
helpviewer_keywords:
- synchronization objects, critical section
- CCriticalSection class
- critical sections
- synchronization classes, CCriticalSection class
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 25d4b124d089441503e9cb457e648695fc54660d
ms.lasthandoff: 02/24/2017

---
# <a name="ccriticalsection-class"></a>CCriticalSection 类
表示一个"临界区"--若要访问资源或代码段的一次允许一个线程的同步对象。  
  
## <a name="syntax"></a>语法  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CCriticalSection::CCriticalSection](#ccriticalsection)|构造 `CCriticalSection` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CCriticalSection::Lock](#lock)|用于访问`CCriticalSection`对象。|  
|[CCriticalSection::Unlock](#unlock)|释放 `CCriticalSection` 对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|检索到的内部指针**CRITICAL_SECTION**对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CCriticalSection::m_sect](#m_sect)|一个**CRITICAL_SECTION**对象。|  
  
## <a name="remarks"></a>备注  
 一次只有一个线程有权修改数据或某些其他受控的资源时，关键部分很有用。 例如，将节点添加到链接的列表是一个过程，它应只允许一个线程通过一次。 通过使用`CCriticalSection`对象来控制在链接的列表，仅一次一个线程可以访问该列表。  
  
> [!NOTE]
>  功能`CCriticalSection`类提供的实际 Win32 **CRITICAL_SECTION**对象。  
  
 临界区使用而不是互斥体 (请参阅[CMutex](../../mfc/reference/cmutex-class.md)) 时速度很关键，该资源不会使用跨进程边界。  
  
 有两种方法来使用`CCriticalSection`对象︰ 独立和嵌入式类中。  
  
-   要使用独立的独立方法`CCriticalSection`对象，请构造`CCriticalSection`对象时需要它。 成功返回后从构造函数，显式锁定的对象通过调用[锁](#lock)。 调用[解锁](#unlock)完成后访问关键节。 这种方法，同时更清晰的给人读取您的源代码，很多容易导致错误因为您必须记住要锁定和解锁的关键部分之前和之后访问。  
  
     更好的方法是使用[CSingleLock](../../mfc/reference/csinglelock-class.md)类。 它还具有`Lock`和`Unlock`方法，但您无需担心如何取消锁定资源，如果发生异常。  
  
-   嵌入方法还可以共享一个类与多个线程通过添加`CCriticalSection`-向类和锁定时所需的数据成员的类型的数据成员。  
  
 有关详细信息使用`CCriticalSection`对象，请参阅文章[多线程处理︰ 如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxmt.h  
  
##  <a name="a-nameccriticalsectiona--ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>CCriticalSection::CCriticalSection  
 构造 `CCriticalSection` 对象。  
  
```  
CCriticalSection();
```  
  
### <a name="remarks"></a>备注  
 若要访问或释放`CCriticalSection`对象，请创建[CSingleLock](../../mfc/reference/csinglelock-class.md)对象，并调用其[锁](../../mfc/reference/csinglelock-class.md#lock)和[解锁](../../mfc/reference/csinglelock-class.md#unlock)成员函数。 如果`CCriticalSection`对象使用独立，则调用其[解锁](#unlock)成员函数以将其释放。  
  
 如果构造函数无法分配所需的系统内存，内存异常 (类型的[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) 会自动引发。  
  
### <a name="example"></a>示例  
  请参阅示例[CCriticalSection::Lock](#lock)。  
  
##  <a name="a-namelocka--ccriticalsectionlock"></a><a name="lock"></a>CCriticalSection::Lock  
 调用此成员函数来访问关键部分对象。  
  
```  
BOOL Lock();  
BOOL Lock(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>参数  
 `dwTimeout`  
 `Lock`将忽略此参数值。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 `Lock`是直到关键部分对象发出信号，将不会返回一个阻塞调用 （可用时）。  
  
 如果定时的等待是必需的则可以使用[CMutex](../../mfc/reference/cmutex-class.md)对象而不是`CCriticalSection`对象。  
  
 如果`Lock`无法分配必需的系统内存，内存异常 (类型的[CMemoryException](../../mfc/reference/cmemoryexception-class.md)) 会自动引发。  
  
### <a name="example"></a>示例  
 此示例演示嵌套的关键节方法控制对共享资源的访问权限来 (静态`_strShared`对象) 使用一个共享`CCriticalSection`对象。 `SomeMethod`函数演示了以安全方式更新共享的资源。  
  
 [!code-cpp[NVC_MFC_Utilities #&11;](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]  
  
##  <a name="a-namemsecta--ccriticalsectionmsect"></a><a name="m_sect"></a>CCriticalSection::m_sect  
 包含由所有的关键部分对象`CCriticalSection`方法。  
  
```  
CRITICAL_SECTION m_sect;  
```  
  
##  <a name="a-nameoperatorcriticalsectionstara--ccriticalsectionoperator-criticalsection"></a><a name="operator_critical_section_star"></a>CCriticalSection::operator CRITICAL_SECTION *  
 检索**CRITICAL_SECTION**对象。  
  
```  
operator CRITICAL_SECTION*();
```   
  
### <a name="remarks"></a>备注  
 调用此函数可检索到的内部指针**CRITICAL_SECTION**对象。  
  
##  <a name="a-nameunlocka--ccriticalsectionunlock"></a><a name="unlock"></a>CCriticalSection::Unlock  
 版本`CCriticalSection`对象以供另一个线程。  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>返回值  
 如果非零`CCriticalSection`对象由该线程已拥有并发布已成功; 否则为 0。  
  
### <a name="remarks"></a>备注  
 如果`CCriticalSection`正在使用独立的`Unlock`必须在完成使用临界区由控制该资源后立即调用。 如果[CSingleLock](../../mfc/reference/csinglelock-class.md)使用对象时，`CCriticalSection::Unlock`的锁对象将调用`Unlock`成员函数。  
  
### <a name="example"></a>示例  
  请参阅示例[CCriticalSection::Lock](#lock)。  
  
## <a name="see-also"></a>另请参阅  
 [CSyncObject 类](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMutex 类](../../mfc/reference/cmutex-class.md)

