---
title: "TN064：ActiveX 控件中的单元模型线程 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.activex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "单元模型线程"
  - "容器 [C++], 多线程"
  - "多线程容器"
  - "OLE 控件, 容器支持"
  - "TN064"
ms.assetid: b2ab4c88-6954-48e2-9a74-01d4a60df073
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN064：ActiveX 控件中的单元模型线程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 此技术声明说明如何在 ActiveX 控件的单元模型线程处理。  请注意、单元模型线程处理在 Visual C\+\+ 版本 4.2 或更高版本才能支持。  
  
## 什么是单元线程处理模型？  
 单元模型是方法。支持嵌入对象，如 ActiveX 控件，在多线程程序中用于控制容器应用程序。  尽管应用程序可能具有多线程，嵌入对象的每个实例都将分配为一个单元，“”将只执行一个线程。  换句话说，调用控件的所有实例中在同一线程上发生。  
  
 但是，同一种控件不同的实例分配给不同的单元。  对此的，因而，如果该控件的多个实例共享的任意数据共同 \(例如，静态或全局数据\)，然后访问共享数据将需要由一个同步对象保护，如临界区。  
  
 有关单元线程模型的完整详细信息中看到在 *OLE 程序员参考》\) 中的*[进程和线程](http://msdn.microsoft.com/library/windows/desktop/ms684841)。  
  
## 为什么支持单元模型线程？  
 单元模型支持线程处理的控件还支持可以在单元模式的多线程 \(msvcrt.lib\) 的容器应用程序。  如果不启用单元模型线程，您将限制可能可以使用容器控件的设置。  
  
 特别是，如果他们具有极少代码或甚至不共享数据，使单元线程处理模型对于大多数控件非常容易。  
  
## 保护共享数据  
 如果控件使用共享的数据，如是静态成员变量，该的访问应保护数据与临界防止多个线程同时修改数据。  因此若要设置临界，声明 `CCriticalSection` 类的静态成员变量。控件的类。  使用此外键部分对象的 `Lock` 和 **解锁** 成员函数中，无论代码访问共享的数据。  
  
 例如，考虑，维护字符串由所有实例共享一个控件类。  此字符串在静态成员变量可能维护和由临界区以保护。  控件的类声明中包含以下内容：  
  
```  
class CSampleCtrl : public COleControl  
{  
    ...  
    static CString _strShared;  
    static CCriticalSection _critSect;  
};  
```  
  
 类的实现将包括这些变量的定义：  
  
```  
int CString CSampleCtrl::_strShared;  
CCriticalSection CSampleCtrl::_critSect;  
```  
  
 给 `_strShared` 静态成员的访问权限可能由临界然后：保护  
  
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
  
## 注册一单元模型识别控件  
 单元模型支持线程处理的控件应通过添加名为值指示注册表中的以下功能，“ThreadingModel”的值“单元”的类 ID 注册表项。*类 ID*\\**InprocServer32** 项下。  若要使此密钥。控件自动注册，请将第六个参数的 `afxRegApartmentThreading` 标志设置为 `AfxOleRegisterControlClass`:  
  
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
        return AfxOleUnregisterClass(m_clsid, m_lpszProgID);  
}  
```  
  
 如果控件项目由 Visual C\+\+ 版本 4.1 或更高版本的 ControlWizard 生成，此标志已经存在于代码。  更改不需要注册线程模型。  
  
 如果项目是由 ControlWizard 早期生成，现有的代码将有布尔值作为第六个参数。  如果现有参数为 true，将其更改为 `afxRegInsertable | afxRegApartmentThreading`。  如果现有参数是 false，将其更改为 `afxRegApartmentThreading`。  
  
 如果控件没有遵循单元线程处理模型的规则，不能将此参数的 `afxRegApartmentThreading`。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)