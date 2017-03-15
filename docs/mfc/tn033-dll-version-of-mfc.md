---
title: "TN033：MFC 的 DLL 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AFXDLL 库"
  - "MFC 的 DLL 版本 [C++]"
  - "DLL [C++], MFC"
  - "MFC DLL [C++], 编写扩展方法 DLLS"
  - "TN033"
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# TN033：MFC 的 DLL 版本
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明如何将用于 MFC 应用程序和扩展 DLL 的 MFCxx.DLL 和 MFCxxD.DLL \(其中 x 是 MFC 版本号\) 共享动态链接库。  有关规则 DLL 的更多信息，请参见 [使用将 MFC 作为 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。  
  
 此技术声明 DLL 包含三个特性。  最后两种是为高级用户：  
  
-   [您如何生成 MFC 扩展 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)  
  
-   [您如何使用 MFC 生成 DLL 版本的 MFC 应用程序](#_mfcnotes_writing_an_application_that_uses_the_dll_version)  
  
-   [MFC 共享动态链接库的实现方式](#_mfcnotes_how_the_mfc30.dll_is_implemented)  
  
 如果您对使用 MFC 的 DLL。用于非 MFC 应用程序的生成感兴趣 \(称为常规 DLL\) 的此，请参见 [技术说明 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。  
  
## MFCxx.DLL 支持大纲显示：术语和文件  
 **Regular DLL**:某些使用 MFC 类，则使用常规 DLL 生成独立 DLL。  在 App\/DLL 边界的接口是“C”接口，并且，客户端应用程序不必是 MFC 应用程序。  
  
 这是" MFC DLL 支持的支持版本 1.0。  在 [技术说明 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) 中，将介绍和 MFC 示例 [DLLScreenCap](../top/visual-cpp-samples.md)高级概念。  
  
> [!NOTE]
>  自 Visual C\+\+ 4.0 版起，静态链接到 MFC 的 **USRDLL** 这个术语是过时并由常规 DLL 替换。  动态链接到 MFC 的还可以生成规则 DLL。  
  
 MFC 3.0 \(如\) 支持。所有新增功能的常规 DLL \(OLE 和数据库类。  
  
 **AFXDLL**:这也称作 MFC 库的共享版本。  这是由添加的新 MFC DLL 支持 2.0。  MFC 库中若干 DLL \(参阅下面的描述\)，并且客户端应用程序或 DLL 动态链接所需的 DLL。  在 application\/DLL 边界的接口是 C\+\+\/MFC 类接口。  客户端应用程序必须是 MFC 应用程序。  这支持所有 MFC 3.0 功能 \(异常：UNICODE 对于数据库类支持。\)  
  
> [!NOTE]
>  自 Visual C\+\+ 4.0 版起，这类 DLL 称作“扩展 DLL”。  
  
 此注释将使用 MFCxx.DLL 引用设置整个的 MFC DLL，包括：  
  
-   调试：MFCxxD.DLL \(合并\) 和 MFCSxxD.LIB \(静态\)。  
  
-   版本：MFCxx.DLL \(合并\) 和 MFCSxx.LIB \(静态\)。  
  
-   Unicode 调试：\(MFCxxUD.DLL 合并\) 和 MFCSxxD.LIB \(静态\)。  
  
-   Unicode 版本：\(MFCxxU.DLL 合并\) 和 MFCSxxU.LIB \(静态\)。  
  
> [!NOTE]
>  MFCSxx\[U\]\[D\].LIB 库与 MFC 的共享 DLL 一起使用。  这些库包含必须静态链接到应用程序或 DLL 关联的代码。  
  
 至对应的导入库的应用程序链接：  
  
-   调试：MFCxxD.LIB  
  
-   版本：MFCxx.LIB  
  
-   Unicode 调试：MFCxxUD.LIB  
  
-   Unicode 版本：MFCxxU.LIB  
  
 “MFC 扩展 DLL 是 DLL”构建 MFCxx.DLL \(和\/或其他 MFC 的共享 DLL\)。  此处 MFC 组件体系结构起动。  如果从 MFC 类派生了有用的类或生成其他类似于 MFC 的工具包，可以在 DLL 中。  DLL 使用 MFCxx.DLL，以最终客户端应用程序。  这样可重用的叶类、可重用的基类且可重用的视图\/类文档。  
  
## 的优缺点  
 您为什么使用 MFC 的共享版本？  
  
-   使用共享库可以将更小的应用程序 \(使用最使用 MFC 库的 10K 小于\) 的最小的应用程序。  
  
-   MFC 共享版本支持 MFC 的规则 DLL 和扩展 DLL。  
  
-   生成使用共享 MFC 库的应用程序要比生成静态链接的 MFC 应用程序快，因为前者不需链接 MFC 本身。  尤其如此。在链接器必须压缩调试信息的生成 \- **DEBUG** 通过已经包含调试信息的 DLL 链接时，只有很少的调试信息需要压缩应用程序中。  
  
 为什么不使用 MFC 的共享版本：  
  
-   发布使用共享库的应用程序要求您提供与程序的 MFCxx.DLL \(及其他\) 库。  MFCxx.DLL 自由是可像许多 DLL，但仍必须在安装程序中安装 DLL。  此外，必须提供包含 MSVCRTxx.DLL，C 运行库程序和 MFC DLL 使用。  
  
##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> 如何编写 MFC 扩展 DLL  
 MFC 扩展 DLL 是包含类和 DLL 函数的修饰 MFC 编写类的功能。  MFC 扩展 DLL 使用共享 MFC DLL 的方式与应用程序使用它，但有另外几点需要注意的事项：  
  
-   生成过程类似于生成用于数组的共享 MFC 库的其他编译器和链接器选项的应用程序。  
  
-   MFC 扩展 DLL 没有 `CWinApp`派生类。  
  
-   MFC 扩展 DLL 必须提供特定 `DllMain`。  AppWizard 提供可以修改的 `DllMain` 函数。  
  
-   如果扩展 DLL 希望导出 `CRuntimeClass`。或资源添加到应用程序中，提供扩展 MFC DLL 通常一个初始化程序创建一个 **CDynLinkLibrary**。  **CDynLinkLibrary** 派生类，则必须使用扩展 DLL，可以使用维护每应用程序数据。  
  
 这些注意事项如下更详细地介绍。  因为它说明，您也应该是称为 MFC 高级概念的示例：[DLLHUSK](../top/visual-cpp-samples.md)  
  
-   生成使用共享库的应用程序。\(DLLHUSK.EXE 是动态链接到 MFC 库和其他 DLL。\) 的 MFC 应用程序  
  
-   生成 MFC 扩展 DLL。\(请注意用于生成扩展 DLL\) 的特殊标志 \( `_AFXEXT`  
  
-   MFC 扩展 DLL 组成的两个示例。  说明如何一个 MFC 扩展 DLL \(TESTDLL1\) 使用受限的基本结构导出和其他的导出整个类接口 \(TESTDLL2\) 的显示。  
  
 客户端应用程序和任何扩展 DLL 必须使用相同版本 MFCxx.DLL。  应遵循的约定和 MFC DLL 的调试和扩展 DLL 的零售 \(\/release\)。  这使客户端程序生成两种调试及其应用程序发布版本和链接自身与适当或调试任何 DLL 发布版本。  
  
> [!NOTE]
>  由于存在 C\+\+ 名称重整和导出问题，从扩展 DLL 中的导出列表可能不同的目录在不同平台的同一 DLL 的调试版本和零售版本和 DLL 之间。  零售 MFCxx.DLL 有大约 2000 个导出入口点；调试 MFCxxD.DLL 有大约 3000 个导出入口点。  
  
### 有关内存管理的快速注释  
 在接近技术声明末尾附近 \(标题“内存，管理”一节，描述 MFCxx.DLL 实现用共享 MFC 版本生成的。  您需要知道实现扩展 DLL 的信息介绍此处。  
  
 MFCxx.DLL 和任何扩展 DLL 加载到客户端应用程序的地址空间将使用相同的内存分配器、资源加载和其他 MFC“全局”状态，就好像它们在同一个应用程序。  这非常重要，因为静态链接到 MFC 的非 MFC DLL 库和规则 DLL 正好相反并具有分配从各自的内存池之外的每个 DLL。  
  
 如果扩展 DLL 分配内存，则该内存能够随意组合与任何其他应用程序分配的对象。  此外，如果，使用共享 MFC 库的应用程序失败，操作系统的保护将维护共享 DLL 的任何其他 MFC 应用程序的完整性。  
  
 同样，其他“全局”MFC 状态 \(如从中加载资源的当前可执行文件\) 也共享，在客户端应用程序和之间 MFCxx.DLL 以及所有 MFC 扩展 DLL。  
  
### 生成扩展 DLL  
 可以使用 AppWizard 创建 MFC DLL，扩展项目，并将其自动生成相应的编译器和链接器设置。  它也是您可以修改生成的 `DllMain` 函数。  
  
 如果将现有项目转换至，MFC 扩展 DLL 使用 MFC，共享版本中以生成的应用程序标准规则开始，则执行以下操作：  
  
-   为编译器标志的添加 **\/D\_AFXEXT**。  在项目的属性对话框中，选择的节点。  然后选择类别预处理器。  宏的定义中添加 `_AFXEXT` 字段，分隔每个用分号的项。  
  
-   移除 **\/Gy** 编译器开关。  在项目的属性对话框中，选择的节点。  然后选择类别生成代码。  确保“启用函数级链接”选项未启用。  因为链接器不会移除未引用的函数，这将非常容易导出类。  如果原始项目用于生成静态链接到 MFC 的规则 DLL，将 **\/MT\[d\]** 编译器选项设置为 **\/MD\[d\]**。  
  
-   导出构造库使用 **\/DLL** 选项链接。  这将设置，也可以创建一个新目标，指定 Win32 动态链接库为目标类型。  
  
### 将头文件  
 扩展 DLL 的目标通常是导出某些通用功能。使用该功能的一个或多个应用程序。  这是因为为导出为客户端应用程序可用的全局类和函数。  
  
 为此必须确保每个成员函数标记为根据需要导入或导出。  这需要特殊的声明：**\_\_declspec\(dllexport\)** 和 **\_\_declspec\(dllimport\)**。  在客户端应用程序中使用类，您希望它们声明为 **\_\_declspec\(dllimport\)**。  当生成扩展 DLL 时，应声明为 **\_\_declspec\(dllexport\)**。  此外，必须导出函数，因此实际上，客户端程序将绑定到其在加载时间。  
  
 若要导出整个类，使用 **AFX\_EXT\_CLASS** 类中定义。  此宏由框架定义为 **\_\_declspec\(dllexport\)**，在 **\_AFXDLL** 和 `_AFXEXT` 都定义了时，但定义为 **\_\_declspec\(dllimport\)**，在未定义 `_AFXEXT` 时。  当生成扩展 DLL 时，`_AFXEXT` \(如上所述，只定义。  例如：  
  
```  
class AFX_EXT_CLASS CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
### 不导出整个类  
 有时您可能希望导出类中的个别成员必需的。  例如，如果导出 `CDialog` 派生类，可能只需要导出构造函数和 `DoModal` 调用。  可以使用 DLL 的导出 .DEF 文件的这些成员，但是，可以采用与还使用 **AFX\_EXT\_CLASS**。需要导出的个别成员。  
  
 例如：  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
   AFX_EXT_CLASS CExampleDialog();  
   AFX_EXT_CLASS int DoModal();  
   // rest of class definition  
   .  
   .  
   .  
};  
```  
  
 当您这样做时，您可能会遇到其他问题，因为您不再导出类的所有成员。  问题的方式 MFC 宏的工作方式。  几个 MFC 的 Helper 宏实际声明或定义数据成员。  因此，这些数据成员还需要从 DLL 中导出了。  
  
 例如，当生成扩展 DLL 时，`DECLARE_DYNAMIC` 宏的定义如下：  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
   static CRuntimeClass* PASCAL _GetBaseClass(); \  
   public: \  
   static AFX_DATA CRuntimeClass class##class_name; \  
   virtual CRuntimeClass* GetRuntimeClass() const; \  
```  
  
 开始“静态 `AFX_DATA`”的行声明类的内部静态对象。  若要正确导出该类并从客户的 .EXE 访问运行时信息，必须导出此静态对象。  由于静态对象是用 `AFX_DATA` 修饰符声明的，因此只需在生成 DLL 时将 `AFX_DATA` 定义为 **\_\_declspec\(dllexport\)**，在生成客户端可执行文件时将其定义为 **\_\_declspec\(dllimport\)**。  
  
 如上所述，已经以此方式定义了 **AFX\_EXT\_CLASS**。  需要 `AFX_DATA` 重定义为与 **AFX\_EXT\_CLASS** 相同。参考类定义。  
  
 例如：  
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
class CExampleView : public CView  
{  
  DECLARE_DYNAMIC()  
  // ... class definition ...  
};  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 MFC 总是在其宏的内部定义的数据项上使用 `AFX_DATA` 符号，因此，此方法对于所有此类方案能够工作。  例如，它适用于 `DECLARE_MESSAGE_MAP`仍有效。  
  
> [!NOTE]
>  如果导出整个类而非选定的类成员，静态数据成员将自动导出。  
  
 可以使用相同技术将自动导出使用 `DECLARE_SERIAL` 和 `IMPLEMENT_SERIAL` 宏的类 `CArchive` 提取运算符。  托通过导出存档运算符 \(位于类声明。H 文件\) 包含下面的代码：  
  
```  
#undef AFX_API  
#define AFX_API AFX_EXT_CLASS  
  
<your class declarations here>  
  
#undef AFX_API  
#define AFX_API  
```  
  
### \_AFXEXT 的限制  
 只要不具有多层扩展 DLL，就可以对扩展 DLL 使用\_**AFXEXT** 预处理器符号。  如果所具有的扩展 DLL 调用或派生自您自己的扩展 DLL 中的类，而您自己的扩展 DLL 又派生自 MFC 类，则必须使用您自己的预处理器符号以避免多义性。  
  
 问题是，在 Win32 中，必须将任何要从 DLL 导出的数据显式声明为 **\_\_declspec\(dllexport\)**，将任何要从 DLL 导入的数据显式声明为 **\_\_declspec\(dllimport\)**。  当您定义 `_AFXEXT` 时，MFC 头文件确定 **AFX\_EXT\_CLASS** 的定义是正确的。  
  
 当具有多层时，一个符号 \(如 **AFX\_EXT\_CLASS** \) 是不够的，因为扩展 DLL，可能导出新类和从另一个扩展 DLL 导入的其他类。  若要处理此问题，请使用一个特殊的预处理器符号。生成 DLL 和使用 DLL。  例如，假设有两个扩展 DLL，DLL 和 B.DLL。  它们分别在 A.H 导出和 B.H 的那些类，分别。  B.DLL 使用从 DLL 的类。  头文件看上去像下面这样：  
  
```  
/* A.H */  
#ifdef A_IMPL  
   #define CLASS_DECL_A   __declspec(dllexport)  
#else  
   #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
  
/* B.H */  
#ifdef B_IMPL  
   #define CLASS_DECL_B   __declspec(dllexport)  
#else  
   #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
  
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition .. };  
```  
  
 当生成 DLL 时，它会生成用 **\/D A\_IMPL**，并且，当 B.DLL 生成 B.dll 时，则是用生成 **\/D B\_IMPL**。  通过对每个 DLL 使用不同的符号，CExampleB 导出，并且 CExampleA 导入，则生成 B.DLL 时。  CExampleA 导出，在生成 DLL 时将导入，则使用。B.DLL \(或某些其他客户端\)。  
  
 当使用内置 **AFX\_EXT\_CLASS** 和 `_AFXEXT` 预处理器符号时，是无法完成这种分层的。  当生成的 OLE、数据库和网络扩展 DLL 时，在上面描述的技术解决此问题没有某些不同机制使用 MFC。  
  
### 不导出整个类  
 再次，那么，当不导出整个类，则必须特别留意。  必须确保正确导出由 MFC 宏创建的必要数据项。  这可以通过将重定义为特定类的宏 **AFX\_DATA** 完成。  每当不导出整个类的时候，就应进行此操作。  
  
 例如：  
  
```  
// A.H  
#ifdef A_IMPL  
   #define CLASS_DECL_A  _declspec(dllexport)  
#else  
   #define CLASS_DECL_A  _declspec(dllimport)  
   #endif  
  
#undef  AFX_DATA  
#define AFX_DATA CLASS_DECL_A  
  
class CExampleA : public CObject  
{  
   DECLARE_DYNAMIC()  
   CLASS_DECL_A int SomeFunction();  
   //class definition   
   .  
   .  
   .  
};  
  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### DllMain  
 下面是在扩展 DLL 的主源文件应放置的确切代码。  在标准包括后，它应是。  请注意，在使用 AppWizard 创建扩展 DLL 的起始文件，它提供您的 `DllMain`。  
  
```  
#include "afxdllx.h"  
  
static AFX_EXTENSION_MODULE extensionDLL;  
  
extern "C" int APIENTRY   
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)  
{  
   if (dwReason == DLL_PROCESS_ATTACH)  
   {  
      // Extension DLL one-time initialization   
      if (!AfxInitExtensionModule(  
             extensionDLL, hInstance))  
         return 0;  
  
      // TODO: perform other initialization tasks here  
   }  
   else if (dwReason == DLL_PROCESS_DETACH)  
   {  
      // Extension DLL per-process termination  
      AfxTermExtensionModule(extensionDLL);  
  
          // TODO: perform other cleanup tasks here  
   }  
   return 1;   // ok  
}  
```  
  
 对 `AfxInitExtensionModule` 的调用捕获模块的运行时类 \(`CRuntimeClass` 结构\) 以及它的对象工厂 \(`COleObjectFactory` 对象\)。之后，将使用创建 **CDynLinkLibrary** 对象时。  对 `AfxTermExtensionModule` \(可选\) 调用提供 MFC 为清除扩展 DLL，当每个进程与扩展 DLL 分离时 \(发生在进程退出时，时，或者，当卸载 DLL 作为调用 **FreeLibrary** \)。  因为大多数扩展 DLL 没有动态加载 \(通常，它们通过其导入库链接\)，对 `AfxTermExtensionModule` 的调用通常不是必需的。  
  
 如果应用程序动态加载和释放扩展 DLL，请确保调用 `AfxTermExtensionModule` 如上所述。  还要确保使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` \(而不是 Win32 函数 **LoadLibrary** 和 **FreeLibrary**\)，如果应用程序使用多个线程或，则动态加载扩展 DLL。  使用 `AfxLoadLibrary` 和 `AfxFreeLibrary` 将确保执行的启动代码和关闭代码，当在加载和卸载扩展 DLL 时不会损坏全局 MFC 状态。  
  
 头文件 AFXDLLX.H 包含在扩展 DLL 中使用的结构的特殊定义，例如 `AFX_EXTENSION_MODULE` 和 **CDynLinkLibrary**的定义。  
  
 必须声明全局 *extensionDLL* 所示。  此超时时间，与 16 位版本的 MFC 不同，您可以分配内存和调用 MFC 函数，因为 MFCxx.DLL 完全初始化，同时调用 `DllMain` 时。  
  
### 共享资源和类  
 只简单的 MFC 扩展 DLL 需要导出到客户端应用程序和 Nothing 某些低带宽函数更多。  更多的用户接口 DLL 可能希望将资源导出和 C\+\+ 类添加到客户端应用程序。  
  
 导出资源的操作是通过资源列表完成的。  在每个应用程序都是 **CDynLinkLibrary** 对象的单向链接表。  当查找资源时，大部分加载资源的标准 MFC 实现首先查看当前资源模块 \(`AfxGetResourceHandle`和\)，如果找不到结构 **CDynLinkLibrary** 列表对象尝试加载请求的资源。  
  
 C\+\+ 对象的动态创建给定了 C.C\+\+ 类名类似。  MFC 对象反序列化机制需要注册所有的 `CRuntimeClass` 对象，以便可以通过基于动态创建所需类型的 C\+\+ 对象来重新构造以前存储。  
  
 如果在扩展 DLL 希望客户端应用程序使用 `DECLARE_SERIAL`类，则需要导出类可见到客户端应用程序。  这通过浏览 **CDynLinkLibrary** 也完成列表。  
  
 对于 MFC 高级概念的示例 [DLLHUSK](../top/visual-cpp-samples.md)列表，类似于：  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
               |                      |  
            MFC90D.DLL            MFC90.DLL  
```  
  
 MFCxx.DLL 通常最后在资源和类列表的表。  MFCxx.DLL 包含所有的标准 MFC 资源，其中包括所有标准命令 ID 的提示字符串。  将其置于列表的尾使得 DLL 和客户端应用程序本身不必有自己的标准 MFC 资源的副本，但是，依赖于 MFCxx.DLL 的共享资源。  
  
 合并所有 DLL 资源和类名称到客户端应用程序的命名空间中有缺陷您必须注意的 ID 或名称。选取。  当然可以通过不将资源导出或一 **CDynLinkLibrary** 对象来禁用此功能。客户端应用程序。  [DLLHUSK](../top/visual-cpp-samples.md) 示例通过使用多个头文件来管理共享资源命名空间。  对使用共享资源文件的更多提示参见 [技术说明 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)。  
  
### 初始化 DLL  
 如上所述，通常需要创建 **CDynLinkLibrary** 对象即可导出资源和类向客户端应用程序。  您将需要提供一个导出入口点 DLL 初始化。  最低限度上，这是什么都不接受参数并返回的无效例程，但也可以是您喜欢的任何名称。  
  
 要使用 DLL 的每台客户端应用程序不必调用此初始化例程，因此，如果使用此方法。  还可以分配 `DllMain` 中此 **CDynLinkLibrary** 对象在调用 `AfxInitExtensionModule`。  
  
 初始化程序必须创建在当前应用程序内存段的 **CDynLinkLibrary** 对象，有线到扩展 DLL 的信息。  这可以通过以下操作：  
  
```  
extern "C" extern void WINAPI InitXxxDLL()  
{  
   new CDynLinkLibrary(extensionDLL);  
}  
```  
  
 定期名称，在本例中 *InitXxxDLL*，可以为所需的任何内容。  它不必是 `extern "C"`，但是，这样做使导出列表目录更易于维护。  
  
> [!NOTE]
>  如果使用从规则 DLL 中使用扩展 DLL，必须导出此初始化函数。  从必须在使用扩展 DLL 的任何类或资源之前的规则 DLL 调用此函数。  
  
### 导出项  
 The 类导出是使用 **\_\_declspec\(dllimport\)** 和 **\_\_declspec\(dllexport\)**。要导出的每个类和全局函数。  这比命名每个入口点即可很容易，但是，效率低 \(参阅下面的描述\)，在较少控制哪些函数导出，无法按序号导出函数。  TESTDLL1 导出其输入和 TESTDLL2 使用此方法。  
  
 一种高效率的方法 \(和 MFCxx.DLL 的方法会手动导出每个条目通过命名每项在 .DEF 文件。  由于我们从导出的 DLL \(即不是内容\) 的选择性导出，必须决定哪些特定接口我们希望导出。  因为您必须指定已损坏的名称传递给链接器输入以的形式在 .DEF 文件，这会很困难。  true，除非您需要它的，一个符号链接不导出任何 C\+\+ 类。  
  
 如果您已尝试导出 C\+\+ 使用 .DEF 文件的类之前，您可能希望开发工具自动生成此列表。  使用两阶段链接处理，可以执行。  一次没有链接 DLL 导出，并允许生成 .MAP 链接器文件。  .MAP 文件来生成应导出函数的列表，因此，使用某些重新排列，因此可以用于生成 .DEF 文件的 EXPORTS 输入。  MFCxx.DLL 和 OLE 和数据库扩展 DLL 导出列表，许多目录数千上，发生与此类过程 \(尽管它不全自动不需要过程调整数组来处理。\)  
  
### CWinApp 与 CDynLinkLibrary  
 MFC 扩展 DLL 没有 `CWinApp`\- 自己的派生的对象；的 `CWinApp`\- 必须与客户端应用程序的派生对象一起使用。  这意味着客户端应用程序拥有主消息泵，、等。  
  
 如果 MFC 扩展 DLL 需要为每个应用程序维护额外的数据，可从 **CDynLinkLibrary** 派生一个新类，并创建该 InitXxxDLL 例程中描述的顶部。  运行时，DLL 会检查当前应用程序的 **CDynLinkLibrary** 对象列表，以查找用于特定扩展 DLL 的对象。  
  
### 使用 DLL 中实现的资源  
 如上所述，默认资源负载将检查具有所请求资源 **CDynLinkLibrary** 对象的列表以查找第一 EXE 或 DLL。  所有 MFC API 以及所有内部代码使用 `AfxFindResourceHandle` 遍历查找任何资源的资源列表，无论它可能驻留。  
  
 如果希望仅从特定的位置加载资源，请使用 API `AfxGetResourceHandle` 和 `AfxSetResourceHandle` 保存旧句柄和设置新句柄。  返回到客户端应用程序之前，请务必还原旧资源句柄。  示例 TESTDLL2 为显式加载菜单使用此方法。  
  
 浏览列表的做法有一些缺点，即速度稍慢且需要管理资源 ID 范围。  它的优点在于，链接到几个扩展 DLL 的客户端应用程序可以使用 DLL 提供的任何资源，而无需指定 DLL 实例句柄。  `AfxFindResourceHandle` 是用于浏览资源列表以查找给定匹配的 API。  它采用资源的名称和类型，并从最先找到匹配项的位置返回资源句柄（或 NULL）。  
  
##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> 编写使用 DLL 生成的应用程序  
  
### 应用程序要求  
 使用共享 MFC 版本的应用程序必须服从几个简单规则：  
  
-   它必须具有 `CWinApp` 对象，并遵循标准消息发送的规则。  
  
-   必须编译它与一组所需的编译器标志 \(如下所示\)。  
  
-   它必须与 MFCxx 导入库链接。  通过将所需的编译器标志，MFC 头确定应用程序应在库链接的链接。  
  
-   若要运行可执行文件，MFCxx.DLL 必须位于 PATH 或在 Windows 系统目录。  
  
### 生成与开发环境  
 如果您使用生成生成的大多数标准默认文件，您可以方便地更改项目生成 DLL 版本。  
  
 下面的步骤假定您有一个正常的 MFC 应用程序。NAFXCWD.LIB \(对于调试\)，并 NAFXCW.LIB \(对于零售\) 和要转换它使用 MFC 库的共享版本。  在运行 Visual C\+\+ 环境并具有内部项目文件。  
  
1.  在 **项目** 菜单上，单击 **属性**。  在 **项目默认值**中的 **常规** 页，将 Microsoft 基础类 \(MFC\) 为 **在共享 DLL 中使用 MFC** \(MFCxx d \(.dll\)。\)  
  
### 生成使用 NMAKE  
 如果您使用 Visual C\+\+ 生成的外部文件功能可以直接使用 NMAKE，则必须编辑生成文件支持编译器和链接器选项  
  
 所需的编译器标志：  
  
 **\/D\_AFXDLL \/MD**  
 **\/D\_AFXDLL**  
  
 标准 MFC 头需要此符号定义：  
  
 **\/MD**  
 应用程序必须使用 C 运行库的 DLL 版本  
  
 其他编译器标志遵循默认、MFC \(例如，为调试\)。  
  
 编辑库的列表。  更改 MFCxxD.LIB NAFXCWD.LIB 为并更改 NAFXCW.LIB 到 MFCxx.LIB。  用 MSVCRT.LIB 替换 LIBC.LIB。  与其他 MFC 库是重要的 MFCxxD.LIB 是将 **before** 的任何 C 运行库。  
  
 可以选择将 **\/D\_AFXDLL** 添加到发布和调试资源编译器选项 \(实际上用 **\/R**编译的资源\) 的文件。  这通过共享存在于 MFC DLL 的资源发出最终执行小。  
  
 完全重新生成，则这些更改后，需要。  
  
### 生成示例  
 大多数 MFC 示例程序中可以从命 Visual C\+\+ 或从命令行的共享 NMAKE 兼容生成文件。  
  
 若要转换这些示例的任何可 MFCxx.DLL，可以加载文件 .MAK 到 Visual C\+\+ 和上述设置项目选项。  如果使用 NMAKE 版本，则 NMAKE 命令行可指定“AFXDLL\=1”使用共享 MFC 库，并且，这将生成此示例。  
  
 MFC 高级概念示例 [DLLHUSK](../top/visual-cpp-samples.md) 生成的 MFC DLL 版本。  此示例阐释如何具体化不仅应用程序链接。MFCxx.DLL，但也演示选项包装 \(MFC 扩展 DLL 的 MFC DLL 的任何其他功能后介绍本技术声明。  
  
### 打包注释  
 DLL 的零售版本 \(MFCxx\[U\].DLL\) 可随便重新发布。  在应用程序开发中，DLL 的调试版本是不可随便重新发布，应仅使用。  
  
 调试 DLL 提供的调试信息。  通过使用 Visual C\+\+ 调试器，可以跟踪应用程序和 DLL 的执行。  释放 DLL \(MFCxx\[U\].DLL\) 不包含调试信息。  
  
 如果自定义或重新生成 DLL，则应调用它们内容为“MFCxx 的”MFC MFCDLL.MAK SRC 文件描述生成选项并包含对重命名 DLL 的逻辑。  因为这些 DLL 由许多 MFC 应用程序，这可能被共享重命名文件是必需的。  使用共享 MFC DLL，则 MFC DLL 的自定义版本中取代系统上安装的一些可能中断其他 MFC 应用程序。  
  
 MFC DLL 不建议重新生成。  
  
##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> MFCxx.DLL 实现方式。  
 下面的章节介绍 MFC DLL \(MFCxx.DLL 和 MFCxxD.DLL\) 如何实现。  了解此处不详细信息也是重要，如果您想做的所有工作是用于应用程序的 MFC DLL。  此处对详细了解如何不重要时写入扩展 MFC DLL，但是了解，此实现可帮助您编写自己的 DLL。  
  
### 概述实现  
 MFC DLL，Unicode 如上所述实际上是 MFC 扩展 DLL 中的一种特殊情况。  它有大量的类的一个非常大数量的导出。  我们在生成规则 DLL 有 MFC 扩展 DLL 比更加特定的某些部分的其他操作。  
  
### Win32 执行大多数工作  
 MFC 16 位版本需要许多特殊技术包括在某个 80x86 程序集代码的堆栈段创建无效、特定段，per\-process 异常上下文和其他技术中每 App 数据。  Win32 直接支持 DLL 中的每个进程的数据，这是您的大多数时间需要。  在很大程度上 MFCxx.DLL 是一个打包在 DLL 中的 NAFXCW.LIB。  如果查看 MFC 源代码时，您会发现\_AFXDLL 极少数 \#ifdef，因为只有非常少需要进行的特定条件。  在序列的特殊情况是专用于涉及在 Windows 3.1 中也 Win32 \(称为 Win32s\)。  Win32s 不直接支持每进程 DLL 数据，所以 MFC DLL 必须使用线程本地存储 \(TLS\) Win32 API 得到处理本地数据。  
  
### 对库源，附加文件的影响  
 **\_AFXDLL** 版本的影响。标准 MFC 类库源和头为最小。  具有特殊的文件版本 \(AFXV\_DLL.H\) 和其他的头文件 \(AFXDLL\_.H\) 由主 AFXWIN.H 标题。  AFXDLL\_.H 头包括 **CDynLinkLibrary** 类和 **\_AFXDLL** 应用程序和扩展其他 MFC DLL 实现详细信息。  AFXDLLX.H 标题。生成 MFC 扩展提供 DLL \(参见上面获取详细信息\)。  
  
 到 MFC 库的常规 SRC MFC 源中具有某其他条件的代码置于 **\_AFXDLL** \#ifdef 下。  其他的源文件 \(DLLINIT.CPP\) 包含额外的 DLL 初始化代码和其他胶浆 MFC 共享版本。  
  
 若要生成 MFC 共享版本，提供附加的文件。\(请参见下文了解有关如何生成 DLL。\) 的详细信息  
  
-   两个文件用于导出 .DEF MFC DLL 入口点用于调试 \(MFCxxD.DEF\) 并释放 MFCxx.DEF \(\) DLL 版本。  
  
-   .rc 文件 \(MFCDLL.RC\) 包含所有的标准 MFC 资源和一 VERSIONINFO 资源 DLL。  
  
-   使用提供 .CLW 文件 \(MFCDLL.CLW ClassWizard，\) 允许浏览 MFC 类。  注意：此功能为 MFC DLL 版本不是特定的。  
  
### 内存管理  
 使用 MFCxx.DLL 的应用程序使用 MSVCRTxx.DLL 提供的常见内存分配程序共享，C 运行时的 DLL。  应用程序，任何扩展 DLL 和良好用作 MFC DLL 使用此共享内存分配器。  使用内存分配的共享 DLL，MFC DLL 可由分配应用程序之后释放反之亦然的内存。  由于应用程序和 DLL 必须使用相同程序分配，您不应当重写 C\+\+ 全局 `operator new` 或 `operator delete`。  相同规则适用于 C 运行时内存分配例程的其余部分 \(例如 `malloc`、`realloc`，**free**和其他一些函数\)。  
  
### Ordinal 类 declspec\(dllexport\) 和 DLL 命名  
 我们不使用 C\+\+ `class` **\_\_declspec\(dllexport\)** 编译器的功能。  相反，将列表导出包含类库源 \(MFCxx.DEF 和 MFCxxD.DEF\)。  这些选择的一组函数和入口点 \(数据\) 只导出。  其他符号，如 MFC 私有实现函数或类中，居民或非居民表中名称导出所有按顺序导出没有完成字符串名称。  
  
 使用 `class` **\_\_declspec\(dllexport\)** 可能是内部版本的更小的 DLL 一个可行的替代，但是 \+ 一旦，像 MFC 的一大，DLL 导出机制效率具有的默认和容量限制。  
  
 这意味着我们是所有可以包装在只约为 800 KB，而无损执行速度或加载的版本 MFCxx.DLL 的许多功能。  MFCxx.DLL 将较大 100K 此方法未使用。  这还可以添加其他的入口点在 .DEF 关闭简单文件时使用的版本控制，而无损速度和效率大小按顺序导出。  主版本生成该类库中更改库名称。  也就是说 MF C30 .DLL MFC 是包含类库的 DLL 版本 3.0 的可再发行组件。  升级此 DLL 位于一个 MFC 3.1，DLL 将命名 MF C31 .DLL。  再次，如果修改 MFC 源代码生成 MFC DLL 的自定义版本，请使用其他名称和 \(最好一个无“MFC”名称中\)。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)