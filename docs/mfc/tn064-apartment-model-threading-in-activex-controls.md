---
title: "TN064: ActiveX 控件中单元模型线程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.controls.activex
dev_langs: C++
helpviewer_keywords:
- OLE controls [MFC], container support
- containers [MFC], multithreaded
- TN064 [MFC]
- multithread container [MFC]
- apartment model threading [MFC]
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07730d6c078dcc8fcd7ea1406f8cff6f665c9919
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn064-apartment-model-threading-in-activex-controls"></a>TN064：ActiveX 控件中的单元模型线程
> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。 因此，某些过程和主题可能已过时或不正确。 要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此技术说明介绍如何启用 ActiveX 控件中的单元模型线程。 请注意仅在 4.2 或更高版本的 Visual c + + 版本支持的单元模型线程。  
  
## <a name="what-is-apartment-model-threading"></a>什么是单元模型线程  
 单元模型是一种方法支持嵌入的对象，如 ActiveX 控件，在多线程的容器应用程序。 尽管应用程序可能具有多个线程，但每个嵌入对象实例将分配给一个"apartment，"将在只有一个线程上执行。 换而言之，对控件的实例的所有调用将在同一线程上都发生。  
  
 但是，相同类型的控件的不同实例可以分配给不同的单元。 因此，如果控件的多个实例共享常见 （例如，静态或全局数据） 中的任何数据，然后对此共享数据的访问将需要受同步对象，例如临界区。  
  
 单元线程模型的完整详细信息，请参阅[进程和线程](http://msdn.microsoft.com/library/windows/desktop/ms684841)中*OLE 程序员参考*。  
  
## <a name="why-support-apartment-model-threading"></a>为什么支持单元模型线程  
 支持的单元模型线程的控件可在多线程的容器应用程序还支持单元模型。 如果不启用单元模型线程处理，将限制潜在的一组无法在其中使用控件的容器。  
  
 启用单元模型线程很容易地大多数控件，特别是当它们有很少或没有共享的数据。  
  
## <a name="protecting-shared-data"></a>保护共享数据  
 如果你的控件使用共享的数据，例如的静态成员变量，访问数据应受到保护，与一个关键部分，以便防止多个线程同时修改数据。 若要为此目的，设置了关键部分，声明类的静态成员变量`CCriticalSection`控件的类中。 使用`Lock`和**解锁**本关键部分的成员函数对象，只要你的代码访问的共享的数据。  
  
 例如，考虑需要维护由所有实例共享的字符串控件类。 此字符串可在静态成员变量中维护和保护的关键部分。 控件的类声明将包含以下各项：  
  
```  
class CSampleCtrl : public COleControl  
{  
 ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 类的实现将包含这些变量的定义：  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 访问`_strShared`静态成员然后受关键部分：  
  
```  
void CSampleCtrl::SomeMethod()  
{  
    _critSect.Lock();
if (_strShared.Empty())  
    _strShared = "<text>";  
    _critSect.Unlock();

 ...  
}  
```  
  
## <a name="registering-an-apartment-model-aware-control"></a>注册的单元模型感知控件  
 支持的单元模型线程的控件应在其下的类 ID 注册表项中的"Apartment"值加上命名的值"ThreadingModel"指示在注册表中，此功能*类 id* \\ **InprocServer32**密钥。 若要使此项以自动注册为您的控件，将传递`afxRegApartmentThreading`中的第六个参数标志`AfxOleRegisterControlClass`:  
  
```  
BOOL CSampleCtrl::CSampleCtrlFactory::UpdateRegistry(BOOL bRegister)  
{  
    if (bRegister)  
    return AfxOleRegisterControlClass(
    AfxGetInstanceHandle(), 
    m_clsid, 
    m_lpszProgID, 
    IDS_SAMPLE, 
    IDB_SAMPLE, 
    afxRegApartmentThreading, 
    _dwSampleOleMisc, 
    _tlid, 
    _wVerMajor, 
    _wVerMinor);

 else  
    return AfxOleUnregisterClass(m_clsid,
    m_lpszProgID);

}  
```  
  
 如果控件项目由 Visual c + + 4.1 或更高版本的 controlwizard 可生成的此标志已将出现在你的代码。 注册的线程模型所需不进行任何更改。  
  
 如果你的项目由早期版本的 controlwizard 可生成的则现有的代码将作为第六个参数具有一个布尔值。 如果现有的参数为 TRUE，将其更改为`afxRegInsertable | afxRegApartmentThreading`。 如果现有的参数为 FALSE，将其更改为`afxRegApartmentThreading`。  
  
 如果控件不遵循单元模型线程处理的规则，你必须通过`afxRegApartmentThreading`此参数中。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

