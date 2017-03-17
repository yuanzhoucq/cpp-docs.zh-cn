---
title: "CWaitCursor 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs:
- C++
helpviewer_keywords:
- cursors, wait cursor
- CWaitCursor class
- wait cursors
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f72598c356add5d891b013f1fd7b87665c5a6c63
ms.lasthandoff: 02/24/2017

---
# <a name="cwaitcursor-class"></a>CWaitCursor 类
在单行中显示等待光标，在你执行较长操作时，此光标通常显示为一个沙漏。  
  
## <a name="syntax"></a>语法  
  
```  
class CWaitCursor  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](#cwaitcursor)|构造`CWaitCursor`对象，并显示等待光标。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|将等待光标恢复后进行了更改。|  
  
## <a name="remarks"></a>备注  
 `CWaitCursor`没有基类的类。  
  
 很好的 Windows 编程实践要求时要执行的操作将花费大量的时间显示等待光标。  
  
 若要显示等待光标，只需定义`CWaitCursor`变量之前执行长时间操作的代码。 对象的构造函数会自动导致将显示等待光标。  
  
 当对象超出范围 (在其中的块的末尾`CWaitCursor`声明对象)，其析构函数将光标设置为上一个游标。 换而言之，则对象将自动执行必要的清理。  
  
> [!NOTE]
>  由于其构造函数和析构函数的工作原理`CWaitCursor`始终将对象声明为局部变量 — 它们永远不会声明为全局变量，也不它们用分配**新**。  
  
 如果执行操作，这可能会造成更改，例如，显示消息框或对话框中，调用的光标[还原](#restore)成员函数以还原将等待光标。 可以调用**还原**甚至当等待光标当前显示。  
  
 若要显示等待光标的另一种方法是使用的组合[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)， [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，也许还有[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。 但是，`CWaitCursor`易于使用，因为不需要将光标设置到上一个游标，当你已完成长时间的操作。  
  
> [!NOTE]
>  MFC 设置并还原游标使用[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虚函数。 您可以重写此函数可提供自定义行为。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CWaitCursor`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
## <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&62;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>CWaitCursor::CWaitCursor  
 若要显示等待光标，只需声明`CWaitCursor`执行耗时较长的操作的代码之前的对象。  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>备注  
 构造函数会自动导致将显示等待光标。  
  
 当对象超出范围 (在其中的块的末尾`CWaitCursor`声明对象)，其析构函数将光标设置为上一个游标。 换而言之，则对象将自动执行必要的清理。  
  
 您可以利用这一事实，析构函数调用了 （这可能是在函数末尾之前） 的块的末尾以使将等待光标处于活动状态中属于您的函数。 这种方法是在下面的第二个示例所示。  
  
> [!NOTE]
>  由于其构造函数和析构函数的工作原理`CWaitCursor`始终将对象声明为局部变量 — 它们永远不会声明为全局变量，也不它们用分配**新**。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&63;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>CWaitCursor::Restore  
 若要还原将等待光标，请在执行操作，例如显示消息框或对话框中，可以将等待光标更改为另一个游标之后调用此函数。  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>备注  
 它是确定以调用**还原**甚至将等待光标当前显示时。  
  
 如果需要还原在函数不是在其中一个将等待光标`CWaitCursor`声明对象，您可以调用[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&64;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [I︰ 如何更改 Microsoft 基础类应用程序中的鼠标光标](http://go.microsoft.com/fwlink/linkid=128044)




