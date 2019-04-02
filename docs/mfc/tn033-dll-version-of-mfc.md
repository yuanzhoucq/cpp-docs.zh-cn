---
title: TN033:MFC 的 DLL 版本
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.dll
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: 4bfc60e20a073dd34945b91dd48ba82cdf4ab9f3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767777"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033:MFC 的 DLL 版本

本说明介绍如何在将 mfcxx.dll 和 MFCxxD.DLL （其中 x 是 MFC 版本号） 共享动态链接库与 MFC 应用程序和 MFC 扩展 Dll。 有关规则 MFC Dll 的详细信息，请参阅[使用 MFC 作为 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

此技术说明介绍了 Dll 的三个方面。 最后两个是针对更高级的用户：

- [如何生成 MFC 扩展 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [如何构建使用 MFC 的 DLL 版本的 MFC 应用程序](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [MFC 如何共享动态链接库实现](#_mfcnotes_how_the_mfc30.dll_is_implemented)

如果您有兴趣构建使用可与非 MFC 应用程序 （这称为规则 MFC DLL） 的 MFC 的 DLL，请参阅[技术注意 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL 支持概述：术语和文件

**规则 MFC DLL**:使用规则 MFC DLL 生成独立的 DLL 使用的一些 MFC 类。 跨应用程序/DLL 边界的接口是"C"接口，并且客户端应用程序没有为 MFC 应用程序。

这是 DLL 支持 MFC 1.0 中支持的版本。 中所述[技术注意 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)和 MFC 高级概念示例[DLLScreenCap](../overview/visual-cpp-samples.md)。

> [!NOTE]
> 截至 Visual c + + 版本 4.0 中，术语**USRDLL**已过时，已由静态链接到 MFC 的规则 MFC DLL。 您也可以构建正则表达式动态链接到 MFC 的 MFC DLL。

MFC 3.0 （及更高版本） 支持使用所有新功能，包括 OLE 和数据库类的规则 MFC Dll。

**AFXDLL**:这也称为共享版本的 MFC 库。 这是在 MFC 2.0 中添加的新 DLL 支持。 MFC 库本身处于数 Dll （如下所述），客户端应用程序或 DLL 动态链接它需要的 Dll。 跨应用程序/DLL 边界的接口是 C + + MFC 类接口。 客户端应用程序必须是一个 MFC 应用程序。 这支持所有 MFC 3.0 功能 (异常：UNICODE 不是支持数据库类）。

> [!NOTE]
> 截至 Visual c + + 4.0 版，这种类型的 DLL 被称为"扩展 DLL。"

本说明将使用 MFCxx.DLL 来指代的整个 MFC DLL 集，其中包括：

- 调试：MFCxxD.DLL （组合） 和 MFCSxxD.LIB （静态）。

- 版本：MFCxx.DLL （组合） 和 MFCSxx.LIB （静态）。

- Unicode 调试：MFCxxUD.DLL （组合） 和 MFCSxxD.LIB （静态）。

- Unicode 版本：MFCxxU.DLL （组合） 和 MFCSxxU.LIB （静态）。

> [!NOTE]
> MFCSxx [U] [D]。在使用 LIB 库与 MFC 一起共享的 Dll。 这些库包含必须静态链接到应用程序或 DLL 的代码。

应用程序链接到相应的导入的库：

- 调试：MFCxxD.LIB

- 版本：MFCxx.LIB

- Unicode 调试：MFCxxUD.LIB

- Unicode 版本：MFCxxU.LIB

"MFC 扩展 DLL"是基于 MFCxx.DLL DLL （和/或其他 MFC 共享 Dll）。 此处的 MFC 组件体系结构会介入。 如果有用的类派生自 MFC 类，或构建另一个类似于 MFC 的工具包，您可以将其放置在 DLL 中。 DLL 作为使用 MFCxx.DLL，执行最终客户端应用程序。 这样可重用叶类、 可重用基类和可重复使用视图/文档类。

## <a name="pros-and-cons"></a>优点和缺点

为什么要使用共享的 MFC 版本

- 使用共享的库可能会导致较小的应用程序 （使用大部分的 MFC 库的最小应用程序为小于 10 K）。

- 共享的版本的 MFC 支持 MFC 扩展 Dll 和规则 MFC Dll。

- 构建使用共享的 MFC 库的应用程序的速度快于生成静态链接的 MFC 应用程序，因为不需链接 MFC 本身。 这是中尤其如此**调试**其中链接器必须压缩调试信息生成 — 通过链接已包含调试信息的 DLL，没有调试信息较少，压缩应用程序中。

为什么您不应使用共享的 MFC 版本：

- 传送使用共享的库的应用程序需要您在发运 MFCxx.DLL （和其他人） 使用你的程序的库。 MFCxx.DLL 可自由分发，如多个 Dll，但你仍必须安装此 DLL 在安装程序中。 此外，你必须发运 MSVCRTxx.DLL，其中包含您的程序和 MFC Dll 本身使用的 C 运行时库。

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> 如何编写 MFC 扩展 DLL

MFC 扩展 DLL 是一个包含类和编写修饰的 MFC 类功能的函数的 DLL。 MFC 扩展 DLL 以相同的方式有几个额外的注意事项的应用程序使用它，使用共享的 MFC Dll:

- 生成过程是类似于构建几个其他编译器和链接器选项中使用共享的 MFC 库的应用程序。

- MFC 扩展 DLL 不具有`CWinApp`-派生的类。

- MFC 扩展 DLL 必须提供一种特殊`DllMain`。 应用程序向导提供`DllMain`可以修改的函数。

- MFC 扩展 DLL 通常会提供初始化例程来创建`CDynLinkLibrary`如果 MFC 扩展 DLL 希望导出`CRuntimeClass`es 或对应用程序的资源。 派生的类`CDynLinkLibrary`如果由 MFC 扩展 DLL 必须保留每个应用程序数据可能会使用。

下面更详细地说明了这些注意事项。 您还应该参考 MFC 高级概念示例[DLLHUSK](../overview/visual-cpp-samples.md)由于它阐释了：

- 构建使用共享的库的应用程序。 (DLLHUSK。EXE 是动态链接到 MFC 库，以及其他 Dll 的 MFC 应用程序。）

- 构建的 MFC 扩展 DLL。 (请注意的特殊标志如`_AFXEXT`，将用于构建的 MFC 扩展 DLL)

- MFC 扩展 Dll 的两个示例。 一个显示了用有限的导出 (TESTDLL1) MFC 扩展 DLL 导出整个类接口 (TESTDLL2)，其他所示的基本结构。

客户端应用程序和任何 MFC 扩展 Dll 必须使用相同版本的 MFCxx.DLL。 应按照 MFC DLL 的约定并提供这两个调试和零售 (/release) 版本的 MFC 扩展 DLL。 这将允许客户端程序来生成其应用程序的调试和发布版本并将其链接与适当的调试或零售版本的所有 Dll。

> [!NOTE]
>  C + + 名称重整和导出问题，因为 MFC 扩展 DLL 中的导出列表可能不同的同一个 DLL 的调试和零售版本和 Dll 之间针对不同的平台。 零售 MFCxx.DLL 具有大约 2000年导出入口点;调试 MFCxxD.DLL 大约 3000 已导出入口点。

### <a name="quick-note-on-memory-management"></a>有关内存管理的快速说明

标题为"内存管理"的此技术说明结尾的部分描述了使用共享版本的 MFC MFCxx.DLL 的实现。 所需了解实现只是 MFC 扩展 DLL 此处所述的信息。

MFCxx.DLL 和所有 MFC 扩展 Dll 加载到客户端应用程序的地址空间将使用相同的内存分配器，资源加载和其他 MFC"全局"状态，它们在同一应用程序中一样。 这很重要，因为非 MFC DLL 库和静态链接到 MFC 的规则 MFC Dll 执行完全相反的操作，并且具有移出其自己的内存池分配每个 DLL。

如果对 MFC 扩展 DLL 分配内存，然后该内存可以自由地混合使用与任何其他应用程序分配的对象中。 此外，如果使用共享的 MFC 库的应用程序崩溃，操作系统的保护将保持共享 DLL 任何其他 MFC 的应用程序的完整性。

同样还为客户端应用程序和所有 MFC 扩展 Dll 以及 MFCxx.DLL 本身之间共享其他"全局"的 MFC 状态，类似于当前的可执行文件加载资源，从。

### <a name="building-an-mfc-extension-dll"></a>构建的 MFC 扩展 DLL

可以使用应用程序向导创建 MFC 扩展 DLL 项目，并将自动生成相应的编译器和链接器设置。 这是也生成`DllMain`可以修改的函数。

如果要将转换为的 MFC 扩展 DLL 的现有项目，开始构建使用共享的版本的 MFC 中，为应用程序的标准规则，然后执行以下操作：

- 添加 **/D_AFXEXT**到编译器标志。 在项目属性对话框中，选择 C/c + + 节点。 然后选择预处理器类别。 添加`_AFXEXT`到定义宏字段中，每个项用分号分隔。

- 删除 **/Gy**编译器开关。 在项目属性对话框中，选择 C/c + + 节点。 然后选择代码生成类别。 请确保未启用"启用函数级链接"选项。 这将使更轻松地导出的类，因为链接器将不会删除未引用的函数。 如果原始项目用于构建正则表达式 MFC DLL 以静态方式链接到 MFC，更改 **/MT [d]** 编译器选项 **/MD [d]**。

- 生成与导出库 **/DLL**到链接的选项。 这会设置时创建新的目标，指定为目标类型的 Win32 动态链接库。

### <a name="changing-your-header-files"></a>更改标头文件

MFC 扩展 DLL 的目标通常是将导出到一个或多个应用程序可以使用该功能的一些常用功能。 这归结为导出的类和全局函数，适用于客户端应用程序。

若要执行此操作必须确保每个成员函数被标记为导入或导出根据。 这需要特殊的声明：`__declspec(dllexport)`和`__declspec(dllimport)`。 当客户端应用程序使用您的类时，你希望它们声明为`__declspec(dllimport)`。 当生成 MFC 扩展 DLL 本身时，它们应声明为`__declspec(dllexport)`。 此外，必须实际导出函数，以便在加载时绑定到其上的客户端程序。

若要导出整个类，使用`AFX_EXT_CLASS`类定义中。 由框架作为定义此宏`__declspec(dllexport)`时`_AFXDLL`并`_AFXEXT`定义的但定义为`__declspec(dllimport)`时`_AFXEXT`未定义。 `_AFXEXT` 如上所述，仅定义生成 MFC 扩展 DLL 时。 例如：

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>不会导出整个类

有时你可能想要导出只是您的类中的单个必要成员。 例如，如果要导出`CDialog`的派生的类，您可能只需要导出该构造函数和`DoModal`调用。 您可以导出使用 DLL 的这些成员。DEF 文件，但你还可以使用`AFX_EXT_CLASS`中您需要将导出单个成员上大致相同的方式。

例如：

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

执行此操作，您可能会遇到其他问题，您无法再导出类的所有成员。 问题是 MFC 宏的工作方式。 MFC 的帮助器宏的几个实际声明或定义数据成员。 因此，这些成员将还需要从 DLL 导出。

例如，DECLARE_DYNAMIC 宏被定义，如下所示生成 MFC 扩展 DLL 时：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

开始在行"静态`AFX_DATA`"声明内您的类的静态对象。 若要正确进行导出此类并从客户端访问运行时信息。Exe 文件，您需要导出此静态对象。 因为使用修饰符声明的静态对象`AFX_DATA`，只需定义`AFX_DATA`要`__declspec(dllexport)`生成 DLL 时并将其作为定义`__declspec(dllimport)`生成客户端可执行文件时。

如上所述，`AFX_EXT_CLASS`已在这种方式中定义。 只需重新定义`AFX_DATA`是与相同`AFX_EXT_CLASS`围绕你的类定义。

例如：

```cpp
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

始终使用 MFC`AFX_DATA`符号在其定义中其宏，因此此方法将适用于这种情况下的数据项上。 例如，它将适用于 DECLARE_MESSAGE_MAP。

> [!NOTE]
> 如果要导出整个类而不是所选的成员的类，静态数据成员将自动导出。

您可以使用相同的技术自动导出`CArchive`提取运算符使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏的类。 括号类声明导出存档运算符 (位于中。H 文件中） 使用以下代码：

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>_AFXEXT 的限制

您可以使用 _**AFXEXT** MFC 扩展 Dll，只要不具有多个层的 MFC 扩展 Dll 的预处理器符号。 如果具有 MFC 扩展 Dll 的调用或派生类中自己的 MFC 扩展 Dll，后者又派生自 MFC 类，必须使用你自己的预处理器符号以避免多义性。

问题是，在 Win32，必须显式声明任何数据作为`__declspec(dllexport)`如果从 DLL 导出和`__declspec(dllimport)`如果要从 DLL 导入。 在定义`_AFXEXT`，MFC 标头确保`AFX_EXT_CLASS`已正确定义。

当你具有多个层、 一个符号如`AFX_EXT_CLASS`是不够的因为 MFC 扩展 DLL 可能要导出新类，以及从另一个 MFC 扩展 DLL 导入其他类。 为了解决此问题，请使用特殊的预处理器符号，指示要构建 DLL 本身还是使用 DLL。 例如，假设两个 MFC 扩展 Dll，A.DLL、 B.DLL。 它们分别导出 A.H 和 B.H 中的某些类。 B.DLL 使用 A.DLL 中的类。 标头文件将如下所示：

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

A.DLL 生成时，它用生成 **/DA_IMPL**和 B.DLL 生成时，它用生成 **/DB_IMPL**。 通过每个 DLL 使用单独的符号，CExampleB 导出和导入 CExampleA 生成 B.DLL 时。 CExampleA 是时构建 A.DLL 导出和导入使用 B.DLL （或其他某个客户端） 时。

使用内置时，无法完成这种类型的分层`AFX_EXT_CLASS`和`_AFXEXT`预处理器符号。 上面所述的技术解决了在构建其 OLE、 数据库和网络 MFC 扩展 Dll 时，MFC 本身的机制使用的方式与此问题。

### <a name="not-exporting-the-entire-class"></a>不会导出整个类

同样，需要时您不导出整个类时要特别小心。 您必须确保创建的 MFC 宏的必需数据项目正确导出。 这可以通过重新定义`AFX_DATA`特定类的宏。 每当不导出整个类，就应进行此操作。

例如：

```cpp
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
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

以下是应置于 MFC 扩展 DLL 的主源代码文件的确切代码。 应该会在后标准包括。 请注意，当你使用应用程序向导创建 MFC 扩展 DLL 的初学者文件，它会提供`DllMain`为您。

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

在调用`AfxInitExtensionModule`捕获模块运行时类 (`CRuntimeClass`结构) 以及其对象工厂 (`COleObjectFactory`对象) 用于更高版本时`CDynLinkLibrary`创建对象。 （可选） 调用`AfxTermExtensionModule`，MFC 清除 MFC 扩展 DLL 时每个进程分离 (时在进程退出，或为卸载 DLL 时，会发生该情况`FreeLibrary`调用) 从 MFC 扩展 DLL。 由于大多数 MFC 扩展 Dll 不会动态加载 （通常情况下，它们在连接通过其导入库），在调用`AfxTermExtensionModule`通常不是必需的。

如果你的应用程序将加载并动态释放 MFC 扩展 Dll，请务必调用`AfxTermExtensionModule`如上所示。 此外请务必使用`AfxLoadLibrary`并`AfxFreeLibrary`(而不是 Win32 函数`LoadLibrary`和`FreeLibrary`) 如果你的应用程序使用多个线程或动态加载的 MFC 扩展 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`也可确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

标头文件 AFXDLLX 中。H 包含特殊定义 MFC 扩展 Dll，如的定义中使用结构`AFX_EXTENSION_MODULE`和`CDynLinkLibrary`。

全局*extensionDLL*必须声明为所示。 与不同的 16 位版本的 MFC 中，可以分配内存并在此期间，调用 MFC 的函数，因为 MFCxx.DLL 完全初始化时你`DllMain`调用。

### <a name="sharing-resources-and-classes"></a>共享资源和类

简单 MFC 扩展 Dll 需要仅导出到客户端应用程序而不安装其他几个低带宽函数。 更多的用户界面密集型 Dll 可能想要将资源和 c + + 类导出到客户端应用程序。

导出资源是通过资源的列表。 在每个应用程序是单向链接的列表的`CDynLinkLibrary`对象。 大多数标准加载资源的 MFC 实现时查找的资源，请先查看当前的资源模块 (`AfxGetResourceHandle`)，如果找不到遍历列表`CDynLinkLibrary`尝试加载所请求的资源的对象。

动态创建 c + + 类名称的 c + + 对象是类似的。 MFC 对象反序列化机制需要具有的所有`CRuntimeClass`对象注册，以便它可以通过动态创建基于以前存储的内容所需类型的 c + + 对象重新构造。

如果希望客户端应用程序使用 MFC 扩展 DLL 中的类的`DECLARE_SERIAL`，则您将需要导出您的类对客户端应用程序可见。 这还可通过遍历`CDynLinkLibrary`列表。

在 MFC 高级概念示例的情况下[DLLHUSK](../overview/visual-cpp-samples.md)，列表看起来类似于：

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

MFCxx.DLL 是通常的最后一个的资源和类列表。 MFCxx.DLL 包括所有标准 MFC 资源，包括所有标准命令 Id 的提示字符串。 将它放在列表的尾允许 Dll 和客户端应用程序本身不具有其自己的标准 MFC 资源，但为依赖的共享资源中 MFCxx.DLL 改为副本。

合并到客户端应用程序的命名空间的资源和类名称的所有 Dll 都有缺点在于必须要小心操作什么 Id 或您选择的名称。 您可以当然禁用此功能不会导出任何一个资源或`CDynLinkLibrary`到客户端应用程序对象。 [DLLHUSK](../overview/visual-cpp-samples.md)示例通过使用多个标头文件来管理共享的资源命名空间。 请参阅[技术注意 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)有关使用共享的资源文件的更多技巧。

### <a name="initializing-the-dll"></a>初始化 DLL

如上所述，您通常需要创建`CDynLinkLibrary`才能导出到客户端应用程序的资源和类的对象。 需要提供初始化该 DLL 的已导出的入口点。 至少，这是一个 void 的例程，不采用任何参数并不返回任何内容，但它可以是您喜欢的任何。

每个想要使用您的 DLL 的客户端应用程序必须调用此初始化例程，如果使用此方法。 您还可能会分配这`CDynLinkLibrary`对象中你`DllMain`只需在调用`AfxInitExtensionModule`。

初始化例程必须创建`CDynLinkLibrary`对象在当前应用程序的堆中，绑定到您的 MFC 扩展 DLL 的信息。 这可以使用以下：

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

例程的名称， *InitXxxDLL*此示例中，可以为任何需要的内容。 它不需要要**extern"C"**，但这样也使导出列表更易于维护。

> [!NOTE]
> 如果您使用您从常规 MFC DLL 的 MFC 扩展 DLL，则必须导出此初始化函数。 使用 MFC 扩展 DLL 类或资源之前，必须从 MFC DLL 的常规调用此函数。

### <a name="exporting-entries"></a>导出条目

导出您的类的简单方法是使用`__declspec(dllimport)`和`__declspec(dllexport)`上每个类和你想要导出的全局函数。 这使得更容易，但效率低于命名每个入口点 （如下所述），因为有控制力导出哪些功能较小并且不能按序号导出的函数。 TESTDLL1 和 TESTDLL2 使用此方法导出它们的项。

更有效的方法 （和 MFCxx.DLL 所使用的方法） 是通过命名每个条目中的手动导出每个条目。DEF 文件。 由于我们要从我们 DLL （即，不是全部） 导出选择性导出，因此我们必须确定我们想要导出哪些特定接口。 这是很难，因为必须在窗体中的条目中指定链接器的重整的名称。DEF 文件。 不导出任何 c + + 类，除非您真正需要具有针对它的符号链接。

如果已尝试导出 c + + 类。DEF 文件之前，你可能想要开发一个工具，可自动生成此列表。 这可以使用两阶段链接过程。 链接您一次用于没有导出的 DLL，并允许链接器生成。映射文件。 。映射文件可用于生成在应导出的函数的列表，因此与某些重新排列，它可用于为你导出项生成应用。DEF 文件。 MFCxx.DLL 和 OLE 和数千在数量、 数据库 MFC 扩展 Dll 的导出列表是与此类的过程生成的 （尽管它不是完全自动的并且需要一些手动优化一段时间中的每一次）。

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs。CDynLinkLibrary

MFC 扩展 DLL 不具有`CWinApp`的派生自己的对象; 而是它必须使用`CWinApp`-派生的对象的客户端应用程序。 这意味着，客户端应用程序拥有主消息泵，空闲循环，等等。

如果您的 MFC 扩展 DLL 需要维护每个应用程序的额外数据，可以派生新类从`CDynLinkLibrary`和在上面描述的例程 InitXxxDLL 中创建它。 DLL 运行时，可以检查当前应用程序的列表的`CDynLinkLibrary`对象以查找该特定 MFC 扩展 DLL 的一个。

### <a name="using-resources-in-your-dll-implementation"></a>在您的 DLL 实现中使用的资源

如上所述，默认资源负载将引导的列表`CDynLinkLibrary`查找第一个 EXE 或 DLL 中具有请求的资源的对象。 所有 MFC Api 以及所有的内部代码使用`AfxFindResourceHandle`遍历要查找任何资源，无论其可能所在的资源列表。

如果你想要仅从特定位置加载资源，使用 Api`AfxGetResourceHandle`和`AfxSetResourceHandle`保存旧句柄并设置新的句柄。 请确保还原旧资源句柄，然后返回到客户端应用程序。 示例 TESTDLL2 用于显式加载菜单使用这种方法。

遍历列表也有缺点，它是速度稍慢，需要管理资源 ID 范围。 它具有链接到多个 MFC 扩展 Dll 的客户端应用程序可以使用任何 DLL 提供的资源，而无需指定 DLL 实例句柄的优势。 `AfxFindResourceHandle` 是一个 API 用于资源列表的每个步骤来查找给定的匹配项。 它采用名称和资源类型，并返回其中第一次发现的资源句柄 （或 NULL）。

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> 编写的应用程序使用的 DLL 版本

### <a name="application-requirements"></a>应用程序的要求

使用共享的 MFC 版本的应用程序必须遵循一些简单的规则：

- 它必须具有`CWinApp`对象，并按照消息泵的标准规则。

- 它必须使用一组所需的编译器标志 （见下文） 进行编译。

- 它必须使用 MFCxx 导入库链接。 通过设置所需的编译器标志，MFC 标头确定在链接时应用程序应与链接的库。

- 若要运行该可执行文件，MFCxx.DLL 必须在路径上或在 Windows 系统目录中。

### <a name="building-with-the-development-environment"></a>构建与开发环境

如果使用内部生成文件的大部分标准默认值，可以轻松更改要生成的 DLL 版本的项目。

以下步骤假定已与 NAFXCWD 链接的正常运行 MFC 应用程序。LIB （适用于调试） 和 NAFXCW。LIB （适用于零售） 以及你想要将其转换为使用共享的版本的 MFC 库。 正在运行的 Visual c + + 环境，并且有一个内部项目文件。

1. 上**项目**菜单上，单击**属性**。 在中**常规**页**项目默认值**，将 Microsoft 基础类设置为**在共享 DLL 中使用 MFC** (MFCxx(d).dll)。

### <a name="building-with-nmake"></a>使用 NMAKE 生成

如果你正在使用外部生成文件功能的 Visual c + +，或直接使用 NMAKE，必须编辑你的生成文件，以支持编译器和链接器选项

所需的编译器标志：

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

标准 MFC 标头需要定义此符号：

- **/MD**应用程序必须使用 C 运行时库的 DLL 版本

所有其他编译器标志遵循 MFC 的默认值 (例如，用于调试的 _DEBUG)。

编辑库的链接器的列表。 更改 NAFXCWD。到 MFCxxD.LIB LIB 和更改 NAFXCW。MFCxx.LIB 到 LIB。 将为 LIBC。LIB msvcrt 系统使用。LIB。 因为与任何其他 MFC 库很重要，放置 MFCxxD.LIB**之前**任何 C 运行时库。

可以选择添加 **/D_AFXDLL**零售和调试资源编译器选项 (实际编译的资源使用的那个 **/R**)。 这使得最终的可执行文件更小通过共享 MFC Dll 中存在的资源。

进行这些更改后需要完全重新生成。

### <a name="building-the-samples"></a>生成示例

从 Visual c + + 或从命令行生成 NMAKE 兼容共享的文件，可以生成的大多数 MFC 示例程序。

若要将这些示例以使用 MFCxx.DLL 的任何转换，可以加载。MAK 到 Visual c + + 文件，并设置项目选项，如上文所述。 如果您使用 NMAKE 生成，你可以指定"AFXDLL = 1"上 NMAKE 命令行，并且将生成该示例使用共享的 MFC 库。

MFC 高级概念示例[DLLHUSK](../overview/visual-cpp-samples.md)使用 MFC 的 DLL 版本生成的。 此示例不只演示了如何构建与 MFCxx.DLL，链接的应用程序，但它还阐释了 MFC DLL 打包选项，例如更高版本中此技术说明描述 MFC 扩展 Dll 的其他功能。

### <a name="packaging-notes"></a>打包说明

零售版本的 Dll (MFCxx [U]。DLL) 可随便重新发布。 不是可以免费再发行 Dll 的调试版本，因此应仅在你的应用程序的开发过程。

调试 Dll 提供调试信息。 通过使用 Visual c + + 调试器，您可以跟踪的应用程序和 DLL 的执行情况。 发布 Dll (MFCxx [U]。DLL) 不包含调试信息。

如果自定义或重新生成 Dll，则应调用它们的内容"MFCxx"MFC SRC 文件 MFCDLL 以外。MAK 介绍生成选项，并包含用于重命名 DLL 的逻辑。 重命名文件是必需的因为这些 Dll 可能共享许多 MFC 应用程序。 MFC Dll 替换为你自定义版本与安装在系统可能会破坏另一个使用共享的 MFC Dll 的 MFC 应用程序。

不建议重新生成 MFC Dll。

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> 如何实现 MFCxx.DLL

以下部分介绍如何实现 MFC DLL （MFCxx.DLL 和 MFCxxD.DLL）。 了解详细信息在此处更改也不重要如果所有你想要执行的是与你的应用程序中使用 MFC DLL。 此处的详细信息不重要，有助于了解如何编写 MFC 扩展 DLL，但了解此实现可能会帮助你编写自己的 DLL。

### <a name="implementation-overview"></a>实现概述

MFC DLL 实际上是 MFC 扩展 DLL 的一种特殊情况，如上文所述。 它具有大量的大量类导出。 有几个其他我们做的事 MFC DLL 中，使其更特殊比常规 MFC 扩展 DLL。

### <a name="win32-does-most-of-the-work"></a>Win32 完成大部分工作

16 位版本的 MFC 需要大量的特殊技术，包括堆栈段上每个应用程序数据由一些 80x86 程序集代码中，每个进程异常上下文和其他技术创建的特殊段。 Win32 直接支持每个进程的数据放到 DLL 的想大多数情况。 大多数情况下 MFCxx.DLL 是只需 NAFXCW。LIB 打包在一个 DLL。 如果您看一下 MFC 源代码，您会发现很少 #ifdef _AFXDLL，由于存在极少数特殊情况下，不需要进行。 特殊情况是不是专门处理 Win32 Windows 3.1 （也称为 Win32s） 上。 Win32s 执行不支持每个进程的 DLL 数据直接因此 MFC DLL 必须使用线程本地存储 (TLS) 来获取处理本地数据的 Win32 Api。

### <a name="impact-on-library-sources-additional-files"></a>对库源，其他文件的影响

产生的影响 **_AFXDLL**上的普通的 MFC 类库源和标头的版本是相对较小。 没有特殊版本的文件 (AFXV_DLL。H），以及将其他头文件 (AFXDLL_。H） 包括由主要 AFXWIN。H 标头。 AFXDLL_。H 标头包括`CDynLinkLibrary`类和其他实现详细信息，这两者的`_AFXDLL`应用程序和 MFC 扩展 Dll。 AFXDLLX。H 标头提供用于生成 MFC 扩展 Dll （请参阅上面有关详细信息）。

MFC SRC 中的 MFC 库的正则源具有一些额外的条件代码下`_AFXDLL`#ifdef。 其他源文件 (DLLINIT。CPP) 包含额外的 DLL 初始化代码和共享版本的 MFC 其他粘附。

若要生成共享的版本的 MFC，提供了其他文件。 （请参阅下面有关如何生成的 DLL 的详细信息。）

- 两个。DEF 文件用于导出调试 (MFCxxD.DEF) 的 MFC DLL 入口点和发布 (MFCxx.DEF) 版本的 DLL。

- 一个。RC 文件 (MFCDLL。RC) 包含所有标准 MFC 资源和 VERSIONINFO 资源 dll。

- 答:。CLW 文件 (MFCDLL。若要允许浏览 MFC 类使用类向导提供 CLW)。 注意： 此功能不是特定于 MFC 的 DLL 版本的。

### <a name="memory-management"></a>内存管理

使用 MFCxx.DLL 的应用程序使用由 MSVCRTxx.DLL，共享的 C 运行时 DLL 提供常见的内存分配。 应用程序、 任何 MFC 扩展 Dll 和 MFC Dll 本身以及使用此共享的内存分配器。 通过使用内存分配在共享的 DLL，MFC Dll 可以分配内存的更高版本将释放由应用程序，反之亦然。 由于应用程序和 DLL 必须使用相同的分配器，您不应覆盖全局 c + +**运算符 new**或**运算符 delete**。 同一规则适用于 C 运行时内存分配例程的其余部分 (如**malloc**， **realloc**，**免费**，等等)。

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>序号和类 __declspec （dllexport） 和 DLL 命名

我们不会使用`class` **__declspec （dllexport)** c + + 编译器的功能。 相反，一组导出是附带类库源 （MFCxx.DEF 和 MFCxxD.DEF）。 导出仅这些选定的一组的入口点 （函数和数据）。 其他符号，如 MFC 私有实现函数或类，不会导出所有导出都完成按序号而无需常驻或驻留的名称表中的字符串名称。

使用`class` **__declspec （dllexport)** 可能是一个可行的替代，用于构建较小的 Dll，但在 MFC 中，默认值导出机制等较大的 DLL 的情况下具有效率和容量限制。

这意味着是功能的什么，我们可以将打包大量的版本仅为大约 800 KB 而不会影响多执行或加载速度的 MFCxx.DLL 中。 MFCxx.DLL 可能会更大的 100 K 此方法尚未使用。 这还使可能的末尾添加的其他入口点。DEF 文件，以便简单版本控制而不会影响按序号导出的速度和大小的效率。 MFC 类库中的主版本修订将更改的库名称。 也就是说，MFC30。DLL 是包含版本 3.0 的 MFC 类库的可再发行 DLL。 此 DLL 的升级在假设的 MFC 3.1 中，假设该 DLL 将被命名为 MFC31。DLL 相反。 同样，如果您修改生成自定义版本的 MFC DLL 的 MFC 源代码，使用不同的名称 （，最好是一个而不使用名称中的"MFC"）。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)
