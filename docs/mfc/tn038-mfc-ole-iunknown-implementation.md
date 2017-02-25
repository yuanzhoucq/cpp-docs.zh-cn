---
title: "TN038：MFC/OLE IUnknown 实现 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "聚合宏 [C++]"
  - "BEGIN_INTERFACE_MAP 宏"
  - "BEGIN_INTERFACE_PART 宏"
  - "COM 接口, 基接口"
  - "DECLARE_INTERFACE_MAP 宏"
  - "END_INTERFACE_MAP 宏"
  - "END_INTERFACE_PART 宏"
  - "INTERFACE_PART 宏"
  - "IUnknown 接口"
  - "METHOD_PROLOGUE 宏"
  - "OLE [C++], 实现 IUnknown 接口"
  - "STDMETHOD 宏"
  - "TN038"
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# TN038：MFC/OLE IUnknown 实现
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  以下技术说明在首次包括在联机文档中后未更新。  因此，某些过程和主题可能已过时或不正确。  要获得最新信息，建议你在联机文档索引中搜索热点话题。  
  
 OLE 2 的核心是“OLE 组件对象模型”，又称为 COM。  COM 定义协同对象如何互相通信的标准。  这包括“对象”外观的详细信息，其中包括方法如何在对象上分派。  COM 还定义了一个基类，所有兼容 COM 的类都由此派生。  此基类即是 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  尽管 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 接口被称为 C\+\+ 类，但是 COM 并不特定于任何一种语言，它可以在 C、PASCAL 或任何其他支持 COM 对象二进制布局的语言中实现。  
  
 OLE 将所有从 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 派生的类称为“接口”。 因为“接口”（例如 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)）不携带实现，所以这是一个重要区别。  它只定义对象借由通信的协议，而不定义这些实现可以完成的具体事项。  这对于允许最大灵活性的系统而言是合理的。  MFC 的作用是实现 MFC\/C\+\+ 程序的默认行为。  
  
 要了解 MFC 的 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 实现，必须先了解此接口是什么。  [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 的简化版本定义如下：  
  
```  
class IUnknown  
{  
public:  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;  
    virtual ULONG AddRef() = 0;  
    virtual ULONG Release() = 0;  
};  
```  
  
> [!NOTE]
>  此例中省略了某些必要的调用约定详细信息，例如 `__stdcall`。  
  
 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 成员函数控制对象的内存管理。  COM 使用引用计数方案跟踪对象。  从来不会像在 C\+\+ 中一样直接引用对象。  相反，始终通过指针引用 COM 对象。  要在所有者用完对象后释放该对象，可调用该对象的 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 成员（不同于使用 delete 运算符释放传统 C\+\+ 对象的做法）。  引用计数机制允许管理单个对象的多个引用。  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 的实现维护对象引用计数 － 在对象的引用计数达到零时才会删除该对象。  
  
 从实现的角度来看，[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 是非常直接的。  此处为普通实现：  
  
```  
ULONG CMyObj::AddRef()   
{   
    return ++m_dwRef;   
}  
  
ULONG CMyObj::Release()   
{   
    if (--m_dwRef == 0)   
    {  
        delete this;   
        return 0;  
    }  
    return m_dwRef;  
}  
```  
  
 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 成员函数更有意思。  拥有成员函数仅为 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 的对象没什么意思，除 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 提供的功能外，让对象完成更多事项会是很好的体验。  这是 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 的用处所在。  它允许你在同一对象上获取不同的“接口”。  这些接口通常从 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 派生，并通过添加新成员函数来添加附加功能。  COM 接口从不在接口中声明成员变量，并且所有成员函数都声明为纯虚。  例如，  
  
```  
class IPrintInterface : public IUnknown  
{  
public:  
    virtual void PrintObject() = 0;  
};  
```  
  
 如果你只有 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 并且要获取 IPrintInterface，那么可以使用 **IPrintInterface** 的 `IID` 调用 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)。  `IID` 是唯一标识接口的 128 位数字。  你或 OLE 定义的每个接口都具有 `IID`。  如果 `pUnk` 是指向 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 对象的指针，则用于从中检索 IPrintInterface 的代码可能为：  
  
```  
IPrintInterface* pPrint = NULL;  
if (pUnk->QueryInterface(IID_IPrintInterface,   
    (void**)&pPrint) == NOERROR)  
{  
    pPrint->PrintObject();  
    pPrint->Release();     
        // release pointer obtained via QueryInterface  
}  
```  
  
 这看起来非常简单，但你要如何实现同时支持 IPrintInterface 和 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 接口的对象？  在本例中，这很简单，因为 IPrintInterface 通过实现 IPrintInterface 直接从 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 派生，所以自动支持 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  例如:  
  
```  
class CPrintObj : public CPrintInterface  
{  
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);  
    virtual ULONG AddRef();  
    virtual ULONG Release();  
    virtual void PrintObject();  
};  
```  
  
 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 的实现将会与上述实现完全相同。  **CPrintObj::QueryInterface** 会查找类似如下所示的内容：  
  
```  
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)  
{  
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)  
    {  
        *ppvObj = this;  
        AddRef();  
        return NOERROR;  
    }  
    return E_NOINTERFACE;  
}  
```  
  
 可以看到，如果接口标识符 \(IID\) 得到识别，指针会返回到对象；否则会出现错误。  另请注意，成功的 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 会导致默式 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)。  当然，你还必须实现 CEditObj::Print。  这很简单，因为 IPrintInterface 直接派生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 接口。  但是，如果要支持从 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 派生的两个不同接口，请考虑以下内容：  
  
```  
class IEditInterface : public IUnkown  
{  
public:  
    virtual void EditObject() = 0;  
};  
```  
  
 尽管有许多不同的方法用于实现同时支持 IEditInterface 和 IPrintInterface 的类，包括使用 C\+\+ 多重继承，但本说明将集中讨论如何使用嵌套类实现此功能。  
  
```  
class CEditPrintObj  
{  
public:  
    CEditPrintObj();  
  
    HRESULT QueryInterface(REFIID iid, void**);  
    ULONG AddRef();  
    ULONG Release();  
    DWORD m_dwRef;  
  
    class CPrintObj : public IPrintInterface  
    {  
    public:  
        CEditPrintObj* m_pParent;  
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);  
        virtual ULONG AddRef();  
        virtual ULONG Release();  
    } m_printObj;  
  
    class CEditObj : public IEditInterface  
    {  
    public:  
        CEditPrintObj* m_pParent;  
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);  
        virtual ULONG AddRef();  
        virtual ULONG Release();  
    } m_editObj;  
};  
```  
  
 以下内容包括整个实现：  
  
```  
CEditPrintObj::CEditPrintObj()  
{  
    m_editObj.m_pParent = this;  
    m_printObj.m_pParent = this;  
}  
  
ULONG CEditPrintObj::AddRef()   
{   
    return ++m_dwRef;  
}  
  
CEditPrintObj::Release()  
{  
    if (--m_dwRef == 0)  
    {  
        delete this;  
        return 0;  
    }  
    return m_dwRef;  
}  
  
HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)  
{  
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)  
    {  
        *ppvObj = &m_printObj;  
        AddRef();  
        return NOERROR;  
    }  
    else if (iid == IID_IEditInterface)  
    {  
        *ppvObj = &m_editObj;  
        AddRef();  
        return NOERROR;  
    }  
    return E_NOINTERFACE;  
}  
  
ULONG CEditPrintObj::CEditObj::AddRef()   
{   
    return m_pParent->AddRef();   
}  
  
ULONG CEditPrintObj::CEditObj::Release()   
{   
    return m_pParent->Release();   
}  
  
HRESULT CEditPrintObj::CEditObj::QueryInterface(  
    REFIID iid, void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid, ppvObj);   
}  
  
ULONG CEditPrintObj::CPrintObj::AddRef()   
{   
    return m_pParent->AddRef();   
}  
  
ULONG CEditPrintObj::CPrintObj::Release()   
{   
    return m_pParent->Release();   
}  
  
HRESULT CEditPrintObj::CPrintObj::QueryInterface(  
    REFIID iid, void** ppvObj)   
{   
    return m_pParent->QueryInterface(iid, ppvObj);   
}  
```  
  
 请注意，大多数 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 实现放置在 CEditPrintObj 类中，而不会复制 CEditPrintObj::CEditObj 和 CEditPrintObj::CPrintObj 中的代码。  这样可以减少代码量并避免 Bug。  此处的要点是，可以从 IUnknown 接口调用 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 检索对象可能支持的任何接口，也可以从其中每个接口执行相同操作。  这意味着每个接口可用的所有 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 函数都必须具有完全相同的行为。  为了让这些嵌入对象调用“外部对象”中的实现，使用了后向指针 \(m\_pParent\)。  m\_pParent 指针在 CEditPrintObj 构造函数计算期间初始化。  然后还会实现 CEditPrintObj::CPrintObj::PrintObject 和 CEditPrintObj::CEditObj::EditObject。  添加了相当多的代码来添加编辑对象的能力这一功能。  幸运的是，接口只有一个成员函数的情况相当罕见（尽管确实存在），并且在这种情况下，通常会将 EditObject 和 PrintObject 合并到单个接口中。  
  
 对于如此简单的方案而言，解释和代码都相当多。  MFC\/OLE 类提供更简单的替代方案。  MFC 实现使用的技术与使用消息映射包装 Windows 消息的方法类似。  此功能称为*接口映射*，会在下一节进行讨论。  
  
## MFC 接口映射  
 MFC\/OLE 包括一个与 MFC 的“消息映射”和“分派映射”在概念和执行上类似的“接口映射”实现。  MFC 的接口映射的核心功能如下所示：  
  
-   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 的标准实现，内置于 `CCmdTarget` 类中。  
  
-   引用计数的维护，通过 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 修改  
  
-   [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 的数据驱动实现  
  
 此外，接口映射支持以下高级功能：  
  
-   支持创建可聚合 COM 对象  
  
-   支持在 COM 对象实现期间使用聚合对象  
  
-   实现可钩进且可扩展  
  
 有关聚合的详细信息，请参阅[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx)主题。  
  
 MFC 的接口映射支持来源于 `CCmdTarget` 类。  `CCmdTarget`“*拥有*”引用计数以及所有与 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 实现关联的成员函数（例如，引用计数位于 `CCmdTarget` 中）。  要创建支持 OLE COM 的类，请从 `CCmdTarget` 派生类并使用各种宏以及 `CCmdTarget` 的成员函数实现所需接口。  MFC 的实现使用嵌套类定义每个接口实现，与上面的示例非常类似。  借助 IUnknown 标准实现和数个可以消除一些重复代码的宏，此操作变得更轻松。  
  
## 接口映射基本知识  
  
#### 使用 MFC 的接口映射实现类  
  
1.  从 `CCmdTarget` 直接或间接派生类。  
  
2.  使用派生类定义中的 `DECLARE_INTERFACE_MAP` 函数。  
  
3.  对于希望支持的每个接口，在类定义中使用 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 宏。  
  
4.  在实现文件中，使用 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 宏定义类的接口映射。  
  
5.  对于支持的每个 IID，使用 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 宏之间的 `INTERFACE_PART` 宏将该 IID 映射到类的特定“部分”。  
  
6.  实现表示所支持接口的每个嵌套类。  
  
7.  使用 `METHOD_PROLOGUE` 宏访问 `CCmdTarget` 派生的父对象。  
  
8.  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 可以委托到这些函数（`ExternalAddRef`、`ExternalRelease` 和 `ExternalQueryInterface`）的 `CCmdTarget` 实现。  
  
 以上 CPrintEditObj 示例可按下列方式实现：  
  
```  
class CPrintEditObj : public CCmdTarget  
{  
public:  
    // member data and member functions for CPrintEditObj go here  
  
// Interface Maps  
protected:  
    DECLARE_INTERFACE_MAP()  
  
    BEGIN_INTERFACE_PART(EditObj, IEditInterface)  
        STDMETHOD_(void, EditObject)();  
    END_INTERFACE_PART(EditObj)  
  
    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)  
        STDMETHOD_(void, PrintObject)();  
    END_INTERFACE_PART(PrintObj)  
};  
```  
  
 以上声明创建派生自 `CCmdTarget` 的类。  `DECLARE_INTERFACE_MAP` 宏告知框架，此类将具有自定义接口映射。  此外，`BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 宏定义嵌套类，在此例中，名称为 CEditObj 和 CPrintObj（X 仅用于将嵌套类与以“C”开头的全局类和以“I”开头的接口类区分开来）。  创建了这些类的两个嵌套成员，分别为 m\_CEditObj 和 m\_CPrintObj。  宏自动声明 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 函数；因此仅声明特定于此接口的函数：EditObject 和 PrintObject（使用 OLE 宏 `STDMETHOD`，以便为目标平台提供合适的 `_stdcall` 和虚拟关键字）。  
  
 实现此类的接口映射：  
  
```  
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)  
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)  
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)  
END_INTERFACE_MAP()  
```  
  
 这将分别连接 IID\_IPrintInterface IID 和 m\_CPrintObj 以及 IID\_IEditInterface 和 m\_CEditObj。  [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 的 `CCmdTarget` 实现 \(`CCmdTarget::ExternalQueryInterface`\) 在收到请求时会使用此映射返回指向 m\_CPrintObj 和 m\_CEditObj 的指针。  无需包括 `IID_IUnknown` 的条目；请求 `IID_IUnknown` 时，框架将使用映射中的第一个接口（在此例中为 m\_CPrintObj）。  
  
 尽管 `BEGIN_INTERFACE_PART` 宏会为你自动声明 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 函数，你仍需要实现它们：  
  
```  
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    return pThis->ExternalAddRef();  
}  
  
ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    return pThis->ExternalRelease();  
}  
  
HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(  
    REFIID iid, void FAR* FAR* ppvObj)  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);  
}  
  
void FAR EXPORT CEditPrintObj::XEditObj::EditObject()  
{  
    METHOD_PROLOGUE(CEditPrintObj, EditObj)  
    // code to "Edit" the object, whatever that means...  
}  
```  
  
 CEditPrintObj::CPrintObj 的实现将与上面对 CEditPrintObj::CEditObj 的定义类似。  尽管可以创建能够用于自动生成这些函数的宏（在 MFC\/OLE 开发的早期阶段是这种情况），但在宏生成多行代码时，设置断点会变得困难。  因此，会手动展开此代码。  
  
 通过使用消息映射的框架实现，有许多事项不再需要完成：  
  
-   实现 QueryInterface  
  
-   实现 AddRef 和 Release  
  
-   在两个接口上声明其中一个内置方法  
  
 此外，框架在内部使用消息映射。  这让你可以从框架类进行派生，例如 `COleServerDoc`，它已支持某些接口并向框架提供的接口提供替换项或添加项。  框架完全支持从基类继承接口映射，因此你可进行此操作。  这是 `BEGIN_INTERFACE_MAP` 采用其第二个参数作为基类名称的原因。  
  
> [!NOTE]
>  通常不可能仅通过从 MFC 版本继承 OLE 接口的嵌入专用化来重用 MFC 的 OLE 接口内置实现的实现。  这不可能实现的原因在于，使用 `METHOD_PROLOGUE` 宏获取所含 `CCmdTarget` 派生对象的访问权限表示嵌入对象对 `CCmdTarget` 派生对象的*固定偏移*。  举例来说，这意味着你无法在 `COleClientItem::XAdviseSink` 中从 MFC 的实现派生嵌入 XMyAdviseSink，因为 XAdviseSink 依赖于对 `COleClientItem` 对象顶部进行特定偏移。  
  
> [!NOTE]
>  但是，你可以为所有你想要其具有 MFC 默认行为的函数委托到 MFC 实现。  这在 `COleFrameHook` 类（它为许多函数委托到 m\_xOleInPlaceUIWindow）中的 `IOleInPlaceFrame` \(XOleInPlaceFrame\) 的 MFC 实现中完成。  选择这种设计是为了减少实现多个接口的对象的运行时大小；它可以避免使用后向指针（例如上一节中使用 m\_pParent 的方式）。  
  
### 聚合和接口映射  
 除支持独立 COM 对象外，MFC 还支持聚合。  聚合本身是一个过于复杂的主题，无法在这里讨论；有关聚合的详细信息，请参阅[聚合](http://msdn.microsoft.com/library/windows/desktop/ms686558\(v=vs.85\).aspx)主题。  本说明将简单介绍对内置到框架和接口映射中的聚合的支持。  
  
 有两种方法可以使用聚合：\(1\) 使用支持聚合的 COM 对象，和 \(2\) 实现可由另一个对象聚合的对象。  这些功能可称为“使用聚合对象”和“使对象可聚合”。  MFC 两者都支持。  
  
### 使用聚合对象  
 要使用聚合对象，需要有某种方法能将聚合连接到 QueryInterface 机制中。  换言之，聚合对象必须表现得像是你的对象的本机部分一样。  那么这如何连接到 MFC 的接口映射机制中呢？  除嵌套对象在其中映射到 IID 的 `INTERFACE_PART` 宏外，你还可以将聚合对象声明为 `CCmdTarget` 派生类的一部分。  为此，将使用 `INTERFACE_AGGREGATE` 宏。  这让你可以指定成员变量（必须是指向 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 或派生类的指针），该变量将集成到接口映射机制中。  如果调用 `CCmdTarget::ExternalQueryInterface` 时指针不为 NULL，且如果请求的 `IID` 不是 `CCmdTarget` 对象本身支持的本机 `IID` 之一，则该框架将自动调用聚合对象的 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 成员函数。  
  
##### 使用 INTERFACE\_AGGREGATE 宏  
  
1.  声明将包含指向聚合对象的指针的成员变量 \(`IUnknown*`\)。  
  
2.  在接口映射中包括 `INTERFACE_AGGREGATE` 宏，它根据名称引用成员变量。  
  
3.  在某些情况下（通常在 `CCmdTarget::OnCreateAggregates` 期间），请将成员变量初始化为除 NULL 之外的值。  
  
 例如:  
  
```  
class CAggrExample : public CCmdTarget  
{  
public:  
    CAggrExample();  
  
protected:  
    LPUNKNOWN m_lpAggrInner;  
    virtual BOOL OnCreateAggregates();  
  
    DECLARE_INTERFACE_MAP()  
    // "native" interface part macros may be used here  
};  
  
CAggrExample::CAggrExample()  
{  
    m_lpAggrInner = NULL;  
}  
  
BOOL CAggrExample::OnCreateAggregates()  
{  
    // wire up aggregate with correct controlling unknown  
    m_lpAggrInner = CoCreateInstance(CLSID_Example,  
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,  
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);  
    if (m_lpAggrInner == NULL)  
        return FALSE;  
    // optionally, create other aggregate objects here  
    return TRUE;  
}  
  
BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)  
    // native "INTERFACE_PART" entries go here  
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)  
END_INTERFACE_MAP()  
```  
  
 m\_lpAggrInner 变量在构造函数中初始化为 NULL。  框架在 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 的默认实现中忽略 NULL 成员变量。  `OnCreateAggregates` 是实际创建聚合对象的适合位置。  如果要在 `COleObjectFactory` 的 MFC 实现外部创建对象，那么必须显式调用它。  讨论聚合对象的创建时，在 `CCmdTarget::OnCreateAggregates` 中创建聚合以及使用 `CCmdTarget::GetControllingUnknown` 的原因就会变得很明显。  
  
 此技术可为你的对象提供聚合对象支持的所有接口及其本机接口。  如果只需要聚合支持的一部分接口，可以替代 `CCmdTarget::GetInterfaceHook`。  这让你可以拥有极低可钩进性，与 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 类似。  你通常会想要拥有聚合支持的所有接口。  
  
### 使对象实现可聚合  
 要让对象可聚合，[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 的实现必须委托到“控制未知”\(controlling unknown\)。 换言之，要成为对象的一部分，它必须把 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 委托到也从 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 派生的其他对象。  此“控制未知”在创建对象时就会提供给对象，即提供给 `COleObjectFactory` 的实现。  将其实现需要花费一小笔开销，并且在某些情况下并不必要，因此 MFC 使其成为可选项。  要使对象可聚合，请从该对象的构造函数调用 `CCmdTarget::EnableAggregation`。  
  
 如果对象还使用聚合，则必须确保将正确的“控制未知”传递给聚合对象。  创建聚合后，此 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 指针通常会传递给对象。  例如，pUnkOuter 参数对于使用 `CoCreateInstance` 创建的对象而言是“控制未知”。  正确的“控制未知”指针可通过调用 `CCmdTarget::GetControllingUnknown` 进行检索。  但是，从该函数返回的值在构造函数计算期间无效。  因此，建议只在 `CCmdTarget::OnCreateAggregates` 替代中创建自己的聚合，该替代中 `GetControllingUnknown` 的返回值是可靠的，即使聚合是从 `COleObjectFactory` 实现创建的。  
  
 添加或释放人工引用计数时，对象操作正确的引用计数十分重要。  为确保这一点，请始终调用 `ExternalAddRef` 和 `ExternalRelease`，而不要调用 `InternalRelease` 和 `InternalAddRef`。  很少在支持聚合的类上调用 `InternalRelease` 或 `InternalAddRef`。  
  
### 参考资料  
 OLE 的高级用法（例如定义自己的接口或替代框架对 OLE 接口的实现）需要使用基础接口映射机制。  
  
 本节讨论用于实现这些高级功能的每个宏和 API。  
  
### CCmdTarget::EnableAggregation － 函数说明  
  
```  
  
void EnableAggregation();  
```  
  
## 备注  
 如果希望对该类型的对象支持 OLE 聚合，请在派生类的构造函数中调用此函数。  这将准备可聚合对象需要的特殊 IUnknown 实现。  
  
### CCmdTarget::ExternalQueryInterface － 函数说明  
  
```  
  
              DWORD ExternalQueryInterface(    const void FAR* lpIID,    LPVOID FAR* ppvObj   
);  
```  
  
## 备注  
  
#### 参数  
 `lpIID`  
 指向 IID 的较远指针（QueryInterface 的第一个参数）  
  
 `ppvObj`  
 指向 IUnknown\* 的指针（QueryInterface 的第二个参数）  
  
## 备注  
 在 IUnknown 实现中为你的类实现的每个接口调用此函数。  此函数基于对象的接口映射提供 QueryInterface 的标准数据驱动实现。  需要将返回值转换为 HRESULT。  如果对象进行了聚合，则此函数将调用“控制 IUnknown”，而不会使用本地接口映射。  
  
### CCmdTarget::ExternalAddRef － 函数说明  
  
```  
  
DWORD ExternalAddRef();  
```  
  
## 备注  
 在 IUnknown::AddRef 实现中为你的类实现的每个接口调用此函数。  返回值是 CCmdTarget 对象的新引用计数。  如果对象进行了聚合，则此函数将调用“控制 IUnknown”，而不会操作本地引用计数。  
  
### CCmdTarget::ExternalRelease － 函数说明  
  
```  
  
DWORD ExternalRelease();  
  
```  
  
## 备注  
 在 IUnknown::Release 实现中为你的类实现的每个接口调用此函数。  返回值指示对象的新引用计数。  如果对象进行了聚合，则此函数将调用“控制 IUnknown”，而不会操作本地引用计数。  
  
### DECLARE\_INTERFACE\_MAP － 宏说明  
  
```  
  
DECLARE_INTERFACE_MAP  
  
```  
  
## 备注  
 在从 `CCmdTarget` 派生并且将拥有接口映射的任何类中使用此宏。  和使用 `DECLARE_MESSAGE_MAP` 的方式非常相似。  此宏调用应放置在类定义中（通常在标头 \(.H\) 文件中）。  具有 `DECLARE_INTERFACE_MAP` 的类必须使用 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 宏对实现文件 \(.CPP\) 中的接口映射进行定义。  
  
### BEGIN\_INTERFACE\_PART 和 END\_INTERFACE\_PART － 宏说明  
  
```  
  
              BEGIN_INTERFACE_PART(   
   localClass,  
   iface   
);  
END_INTERFACE_PART(   
   localClass   
)  
```  
  
## 备注  
  
#### 参数  
 l`ocalClass`  
 实现接口的类的名称  
  
 `iface`  
 此类实现的接口的名称  
  
## 备注  
 对于类将实现的每个接口，需要拥有一个 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 对。  这些宏定义从你定义的 OLE 接口派生的本地类以及该类的嵌入成员变量。  自动声明 [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)、[Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 和 [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 成员。  你必须包括属于要实现的接口的其他成员函数的声明（这些声明放在 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART`宏之间）。  
  
 `iface` 参数是你希望实现的 OLE 接口，例如 `IAdviseSink` 或 `IPersistStorage`（或你自己的自定义接口）。  
  
 `localClass` 参数是将被定义的本地类的名称。  名称前面会自动追加一个“X”。  此命名约定用于避免与同名的全局类发生冲突。  此外，嵌入成员的名称和 `localClass` 的名称相同，但其前缀为“m\_x”。  
  
 例如:  
  
```  
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)  
   STDMETHOD_(void,OnDataChange)(LPFORMATETC, LPSTGMEDIUM);  
   STDMETHOD_(void,OnViewChange)(DWORD, LONG);  
   STDMETHOD_(void,OnRename)(LPMONIKER);  
   STDMETHOD_(void,OnSave)();  
   STDMETHOD_(void,OnClose)();  
END_INTERFACE_PART(MyAdviseSink)  
```  
  
 将定义从 IAdviseSink 派生的名为 XMyAdviseSink 的本地类和在该类中声明的名为 m\_xMyAdviseSink 的成员。注意：  
  
> [!NOTE]
>  以 `STDMETHOD_` 开头的行基本上复制自 OLE2.H 并略微进行了修改。  从 OLE2.H 复制它们能减少难以解决的错误。  
  
### BEGIN\_INTERFACE\_MAP 和 END\_INTERFACE\_MAP － 宏说明  
  
```  
  
              BEGIN_INTERFACE_MAP(   
   theClass,  
   baseClass   
) END_INTERFACE_MAP  
```  
  
## 备注  
  
#### 参数  
 `theClass`  
 要在其中定义接口映射的类  
  
 `baseClass`  
 `theClass` 派生自的类。  
  
## 备注  
 `BEGIN_INTERFACE_MAP` 和 `END_INTERFACE_MAP` 宏在实现文件中用于实际定义接口映射。  对于实现的每个接口，有一个或多个 `INTERFACE_PART` 宏调用。  对于类使用的每个聚合，有一个 `INTERFACE_AGGREGATE` 宏调用。  
  
### INTERFACE\_PART － 宏说明  
  
```  
  
              INTERFACE_PART(   
   theClass,  
   iid,   
   localClass   
)  
```  
  
## 备注  
  
#### 参数  
 `theClass`  
 包含接口映射的类的名称。  
  
 `iid`  
 要映射到嵌入类的 `IID`。  
  
 `localClass`  
 本地类的名称（去掉“X”）。  
  
## 备注  
 在 `BEGIN_INTERFACE_MAP` 宏和 `END_INTERFACE_MAP` 宏之间为你的对象将支持的每个接口使用此宏。  它让你能够将 IID 映射到 `theClass` 和 `localClass` 指示的类成员。  “m\_x”将向 `localClass` 自动添加。  请注意，多个 `IID` 可以与单个成员关联。  当你仅实现一个“派生程度最高”的接口并希望同时提供所有中间接口时，这非常有用。  `IOleInPlaceFrameWindow` 接口就是一个很好的示例。  其层次结构如下所示：  
  
```  
IUnknown  
    IOleWindow  
        IOleUIWindow  
            IOleInPlaceFrameWindow  
```  
  
 如果对象实现 `IOleInPlaceFrameWindow`，那么除“派生程度最高”的接口 `IOleInPlaceFrameWindow`（实际实现的接口）外，客户端还可能在以下任何接口上 `QueryInterface`：`IOleUIWindow`、`IOleWindow` 或 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)。  要处理此情况，可以使用多个 `INTERFACE_PART` 宏将每一个基接口映射到 `IOleInPlaceFrameWindow` 接口：  
  
 在类定义文件中：  
  
```  
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)  
```  
  
 在类实现文件中：  
  
```  
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)  
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)  
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)  
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)  
END_INTERFACE_MAP  
```  
  
 该框架负责 IUnknown，因为它始终是必需的。  
  
### INTERFACE\_PART － 宏说明  
  
```  
  
              INTERFACE_AGGREGATE(   
   theClass,  
   theAggr   
)  
```  
  
## 备注  
  
#### 参数  
 `theClass`  
 包含接口映射的类的名称，  
  
 `theAggr`  
 要聚合的成员变量的名称。  
  
## 备注  
 此宏用于告知框架，类正在使用聚合对象。  它必须在 `BEGIN_INTERFACE_PART` 和 `END_INTERFACE_PART` 宏之间出现。  聚合对象是单独的对象，从 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 派生。  通过使用聚合和 `INTERFACE_AGGREGATE` 宏，你可以让聚合支持的所有接口看起来像是受到对象直接支持。  `theAggr` 参数只是你的类的成员变量的名称，派生自 [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509)（直接或间接）。  在放置到接口映射中时，所有 `INTERFACE_AGGREGATE` 宏都必须遵循 `INTERFACE_PART` 宏。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)