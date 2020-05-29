---
title: TN033：MFC 的 DLL 版本
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: ad4cb883cfe7e397cf599d659afb02b23501dc5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370315"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033：MFC 的 DLL 版本

本说明介绍如何使用 MFCxx.DLL 和 MFCxxD.DLL（其中 x 是 MFC 版本号）与 MFC 应用程序和 MFC 扩展 DLL 共享动态链接库。 有关常规 MFC DLL 的详细信息，请参阅[使用 MFC 作为 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

本技术说明涵盖 DLL 的三个方面。 后两个适用于更高级的用户：

- [如何构建 MFC 扩展 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [如何使用 MFC 的 DLL 版本的 MFC 应用程序](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [如何实现 MFC 共享动态链接库](#_mfcnotes_how_the_mfc30.dll_is_implemented)

如果您有兴趣使用可用于非 MFC 应用程序的 MFC 构建 DLL（这称为常规 MFC DLL），请参阅[技术说明 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>MFCxx.DLL 支持的概述：术语和文件

**常规 MFC DLL**：使用常规 MFC DLL 使用某些 MFC 类构建独立 DLL。 跨 App/DLL 边界的接口是"C"接口，客户端应用程序不必是 MFC 应用程序。

这是 MFC 1.0 中支持的 DLL 支持版本。 它描述了[技术说明11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)和MFC高级概念示例[DLLScreenCap。](../overview/visual-cpp-samples.md)

> [!NOTE]
> 从 Visual C++ 版本 4.0 起，**术语 USRDLL**已过时，并已由静态链接到 MFC 的常规 MFC DLL 替换。 您还可以构建一个定期 MFC DLL，动态链接到 MFC。

MFC 3.0（及以上）支持常规 MFC DLL，具有所有新功能，包括 OLE 和数据库类。

**AFXDLL**：这也称为 MFC 库的共享版本。 这是 MFC 2.0 中添加的新 DLL 支持。 MFC 库本身位于多个 DLL 中（如下所述），客户端应用程序或 DLL 动态链接所需的 DLL。 跨应用程序/DLL 边界的接口是C++/MFC 类接口。 客户端应用程序必须是 MFC 应用程序。 这支持所有 MFC 3.0 功能（例外情况：数据库类不支持 UNICODE）。

> [!NOTE]
> 从 Visual C++ 版本 4.0 起，这种类型的 DLL 称为"扩展 DLL"。

本说明将使用 MFCxx.DLL 来引用整个 MFC DLL 集，其中包括：

- 调试：MFCxxD.DLL（组合）和MFCSxxD.LIB（静态）。

- 发布：MFCxx.DLL（组合）和MFCSxx.LIB（静态）。

- Unicode 调试：MFCxxUD.DLL（组合）和 MFCSxxD.LIB（静态）。

- Unicode 版本：MFCxxU.DLL（组合）和 MFCSxxU.LIB（静态）。

> [!NOTE]
> MFCSxx[U]D]。LIB 库与 MFC 共享 DLL 结合使用。 这些库包含必须静态链接到应用程序或 DLL 的代码。

指向相应导入库的应用程序链接：

- 调试： MFCxxD.LIB

- 发布： MFCxx.LIB

- Unicode 调试：MFCxxUD.LIB

- Unicode 版本：MFCxxU.LIB

"MFC 扩展 DLL"是基于 MFCxx.DLL（和/或其他 MFC 共享 DLL）构建的 DLL。 在这里，MFC 组件体系结构开始生效。 如果从 MFC 类派生有用类，或者构建另一个类似 MFC 的工具包，则可以将其放置在 DLL 中。 DLL 使用 MFCxx.DLL，最终客户端应用程序也是如此。 这允许可重用的叶类、可重用的基类和可重用的视图/文档类。

## <a name="pros-and-cons"></a>优点和缺点

为什么要使用 MFC 的共享版本

- 使用共享库可能会导致应用程序更小（使用大多数 MFC 库的最小应用程序小于 10K）。

- MFC 的共享版本支持 MFC 扩展 DLL 和常规 MFC DLL。

- 构建使用共享 MFC 库的应用程序比构建静态链接的 MFC 应用程序要快，因为没有必要链接 MFC 本身。 在**DEBUG**生成中尤其如此，其中链接器必须压缩调试信息 — 通过链接到已包含调试信息的 DLL，应用程序内要压缩的调试信息更少。

为什么不使用 MFC 的共享版本：

- 传送使用共享库的应用程序需要您将 MFCxx.DLL（和其他）库与程序一起传送。 MFCxx.DLL 与许多 DLL 一样可自由再分发，但您仍必须在设置程序中安装 DLL。 此外，您必须提供 MSVCRTxx.DLL，其中包含由您的程序和 MFC DLL 本身使用的 C 运行时库。

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>如何编写 MFC 扩展 DLL

MFC 扩展 DLL 是一种 DLL，其中包含为修饰 MFC 类的功能而编写的类和函数。 MFC 扩展 DLL 使用共享 MFC DLL 的方式与应用程序使用它的方式相同，还有其他一些注意事项：

- 生成过程类似于构建一个应用程序，该应用程序使用具有一些附加编译器和链接器选项的共享 MFC 库。

- MFC 扩展 DLL 没有派生`CWinApp`类。

- MFC 扩展 DLL 必须提供`DllMain`特殊的 。 AppWizard 提供了一`DllMain`个可以修改的函数。

- `CDynLinkLibrary` MFC 扩展 DLL 通常会提供初始化例程，以创建 MFC 扩展 DLL 希望将`CRuntimeClass`es 或资源导出到应用程序时创建 。 如果每个应用程序的数据`CDynLinkLibrary`必须由 MFC 扩展 DLL 维护，则可以使用 派生类。

下面将更详细地介绍这些注意事项。 您还应参考 MFC 高级概念示例[DLLHUSK，](../overview/visual-cpp-samples.md)因为它说明了：

- 使用共享库构建应用程序。 （德胡斯克。EXE 是一个 MFC 应用程序，可动态链接到 MFC 库以及其他 DLL。

- 构建 MFC 扩展 DLL。 （请注意用于构建 MFC`_AFXEXT`扩展 DLL 的特殊标志）

- MFC 扩展 DLL 的两个示例。 一个显示导出受限的 MFC 扩展 DLL 的基本结构 （TESTDLL1），另一个显示导出整个类接口 （TESTDLL2）。

客户端应用程序和任何 MFC 扩展 DLL 都必须使用相同的 MFCxx.DLL 版本。 您应该遵循 MFC DLL 的约定，并提供 MFC 扩展 DLL 的调试和零售（/发布）版本。 这允许客户端程序构建其应用程序的调试和零售版本，并将它们与所有 DLL 的相应调试或零售版本链接。

> [!NOTE]
> 由于C++名称管理和导出问题，因此来自 MFC 扩展 DLL 的导出列表可能因不同平台的相同 DLL 和 DLL 的调试和零售版本而异。 零售 MFCxx.DLL 拥有约 2000 个出口入口点;调试 MFCxxD.DLL 拥有约 3000 个导出的入口点。

### <a name="quick-note-on-memory-management"></a>关于内存管理的快速说明

本技术说明末尾的标题为"内存管理"的部分介绍了 MFCxx.DLL 与 MFC 共享版本的实现。 此处介绍了实现 MFC 扩展 DLL 所需的信息。

MFCxx.DLL 和加载到客户端应用程序地址空间中的所有 MFC 扩展 DLL 将使用相同的内存分配器、资源加载和其他 MFC"全局"状态，就像它们在同一应用程序中一样。 这一点非常重要，因为静态链接到 MFC 的非 MFC DLL 库和常规 MFC DLL 完全相反，并且每个 DLL 都从自己的内存池中分配出来。

如果 MFC 扩展 DLL 分配内存，则该内存可以自由地与任何其他应用程序分配的对象混合。 此外，如果使用共享 MFC 库的应用程序崩溃，操作系统的保护将保持共享 DLL 的任何其他 MFC 应用程序的完整性。

同样，其他"全局"MFC 状态（如当前可执行文件以加载资源）也在客户端应用程序和所有 MFC 扩展 DLL 以及 MFCxx.DLL 本身之间共享。

### <a name="building-an-mfc-extension-dll"></a>构建 MFC 扩展 DLL

您可以使用 AppWizard 创建 MFC 扩展 DLL 项目，它将自动生成相应的编译器和链接器设置。 它还生成了一个`DllMain`函数，您可以修改。

如果要将现有项目转换为 MFC 扩展 DLL，请从使用 MFC 的共享版本构建应用程序的标准规则开始，然后执行以下操作：

- 将 **/D_AFXEXT**添加到编译器标志。 在"项目属性"对话框中，选择 C/C++节点。 然后选择预处理器类别。 添加到`_AFXEXT`"定义宏"字段，将每个具有分号的项分隔开来。

- 删除 **/Gy**编译器开关。 在"项目属性"对话框中，选择 C/C++节点。 然后选择"代码生成"类别。 确保未启用"启用功能级别链接"选项。 这将更容易导出类，因为链接器不会删除未引用的函数。 如果原始项目用于构建与 MFC 静态链接的常规 MFC DLL，则将 **/MT_d_** 编译器选项更改为 **/MD_d}**。

- 使用 **/DLL**选项构建导出库以链接。 这将在创建新目标时设置，指定 Win32 动态链接库为目标类型。

### <a name="changing-your-header-files"></a>更改标题文件

MFC 扩展 DLL 的目标通常是将一些通用功能导出到一个或多个可以使用该功能的应用程序。 这归结为导出可用于客户端应用程序的类和全局函数。

为此，必须确保每个成员函数都标记为适当的导入或导出。 这需要特殊的声明：`__declspec(dllexport)`和`__declspec(dllimport)`。 当客户端应用程序使用类时，您希望将它们声明为`__declspec(dllimport)`。 在构建 MFC 扩展 DLL 本身时，应声明它们`__declspec(dllexport)`为 。 此外，必须实际导出函数，以便客户端程序在加载时绑定到它们。

要导出整个类，请使用`AFX_EXT_CLASS`类定义。 此宏由框架`__declspec(dllexport)`定义为何时`_AFXDLL`定义和`_AFXEXT`定义，但定义为`__declspec(dllimport)`未定义时。 `_AFXEXT` `_AFXEXT`如上所述，仅在构建 MFC 扩展 DLL 时定义。 例如：

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>未导出整个类

有时，您可能希望只导出类的单个必要成员。 例如，如果要导出`CDialog`派生类，可能只需要导出构造函数和`DoModal`调用。 您可以使用 DLL 导出这些成员。DEF 文件，但您也可以以大致相同`AFX_EXT_CLASS`的方式对需要导出的各个成员使用。

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

执行此操作时，可能会遇到其他问题，因为您不再导出类的所有成员。 问题在于 MFC 宏的工作方式。 MFC 的几个帮助宏实际上声明或定义了数据成员。 因此，这些数据成员也需要从 DLL 导出。

例如，DECLARE_DYNAMIC宏的定义如下：生成 MFC 扩展 DLL 时：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

开始"静态`AFX_DATA`"的行是在类内声明静态对象。 要正确导出此类并从客户端访问运行时信息。EXE，您需要导出此静态对象。 由于静态对象是使用修饰`AFX_DATA`符声明的，因此在构建 DLL`AFX_DATA`时`__declspec(dllexport)`只需定义为 ，并将其定义为构建客户端`__declspec(dllimport)`可执行文件时。

如上所述，`AFX_EXT_CLASS`已经以这种方式定义。 您只需重新定义`AFX_DATA`，与类定义`AFX_EXT_CLASS`相同。

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

MFC 始终在其`AFX_DATA`宏中定义的数据项上使用符号，因此此技术适用于所有此类方案。 例如，它将适用于DECLARE_MESSAGE_MAP。

> [!NOTE]
> 如果要导出整个类而不是类的选定成员，则会自动导出静态数据成员。

可以使用相同的技术自动导出使用DECLARE_SERIAL和IMPLEMENT_SERIAL宏`CArchive`的类的提取运算符。 通过包围类声明（位于 中）导出存档运算符。H 文件）与以下代码：

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>_AFXEXT的限制

只要没有多层 MFC 扩展 DLL，就可以为 MFC 扩展 DLL 使用 #**AFXEXT**预处理器符号。 如果 MFC 扩展 DLL 调用或派生自您自己的 MFC 扩展 DLL 中的类，然后从 MFC 类派生，则必须使用您自己的预处理器符号以避免歧义。

问题是，在 Win32 中，必须显式声明任何数据，就像`__declspec(dllexport)`从 DLL 导出数据一样，`__declspec(dllimport)`以及如果要从 DLL 导入数据。 定义`_AFXEXT`时，MFC 标头确保`AFX_EXT_CLASS`正确定义。

当您有多个图层时，一个符号（如`AFX_EXT_CLASS`是不够的），因为 MFC 扩展 DLL 可能正在导出新类，以及从其他 MFC 扩展 DLL 导入其他类。 为了解决此问题，请使用一个特殊的前处理器符号，指示您正在构建 DLL 本身，而不是使用 DLL。 例如，假设两个 MFC 扩展 DLL A.DLL 和 B.DLL。 它们各自分别导出 A.H 和 B.H 中的一些类。 B.DLL 使用 A.DLL 中的类。 头文件如下所示：

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

当 A.DLL 生成时，它使用 **/DA_IMPL**构建，当 B.DLL 生成时，它使用 **/DB_IMPL**生成。 通过为每个 DLL 使用单独的符号，将导出 CExampleB 并在构建 B.DLL 时导入 CExampleA。 CExampleA 在生成 A.DLL 时导出，并在 B.DLL（或其他客户端）使用时导入。

使用内置`AFX_EXT_CLASS`和`_AFXEXT`预处理器符号时，无法进行这种类型的分层。 上述技术以 MFC 本身在构建其 OLE、数据库和网络 MFC 扩展 DLL 时使用的机制的方式解决了此问题。

### <a name="not-exporting-the-entire-class"></a>未导出整个类

同样，当您不导出整个类时，您必须特别注意。 您必须确保正确导出 MFC 宏创建的必要数据项。 这可以通过重新定义`AFX_DATA`到特定类的宏来实现。 这应在您不导出整个类时执行。

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

以下是您应该在 MFC 扩展名 DLL 的主源文件中放置的确切代码。 它应该在标准包含之后。 请注意，当您使用 AppWizard 为 MFC 扩展名 DLL 创建启动文件时`DllMain`，它会为您提供 .

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

捕获`AfxInitExtensionModule`模块运行时类（`CRuntimeClass`结构）及其对象工厂（`COleObjectFactory`对象）的调用，供以后创建`CDynLinkLibrary`对象时使用。 （可选）调用允许`AfxTermExtensionModule`MFC 在每个进程从 MFC 分机 DLL 分离时清理 MFC 分机 DLL（当进程退出时发生，或者由于`FreeLibrary`调用而卸载 DLL 时）。 由于大多数 MFC 扩展 DLL 不是动态加载的（通常，它们通过其导入库链接），因此通常`AfxTermExtensionModule`不需要调用 。

如果应用程序动态加载并释放 MFC 扩展 DLL，请确保调用`AfxTermExtensionModule`，如上所示。 如果应用程序使用多个线程`AfxLoadLibrary`或`AfxFreeLibrary`动态加载 MFC 扩展`LoadLibrary` `FreeLibrary`DLL，请确保使用 和 （而不是 Win32 函数和 ）。 使用`AfxLoadLibrary`并确保`AfxFreeLibrary`在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

头文件 AFXDLLX。H 包含 MFC 扩展 DLL 中使用的结构的特殊定义，例如 和`AFX_EXTENSION_MODULE``CDynLinkLibrary`的定义。

全局*扩展 DLL*必须声明为如图所示。 与 16 位版本的 MFC 不同，您可以在这段时间内分配内存并调用 MFC 函数，因为 MFCxx.DLL 在调用时`DllMain`已完全初始化。

### <a name="sharing-resources-and-classes"></a>共享资源和类

简单的 MFC 扩展 DLL 只需要将几个低带宽函数导出到客户端应用程序，而仅需向客户端应用程序导出。 更多用户界面密集型 DLL 可能需要将资源和C++类导出到客户端应用程序。

导出资源是通过资源列表完成的。 在每个应用程序中，都是`CDynLinkLibrary`一个单独链接的对象列表。 查找资源时，加载资源的大多数标准 MFC 实现首先查看当前资源模块 （），`AfxGetResourceHandle`如果未找到，则遍历尝试加载请求的资源`CDynLinkLibrary`的对象列表。

给定C++类名称C++对象的动态创建是相似的。 MFC 对象反序列化机制需要注册所有`CRuntimeClass`对象，以便可以通过根据之前存储的内容动态创建所需类型的C++对象来重建。

如果希望客户端应用程序在 MFC 扩展 DLL 中使用 类`DECLARE_SERIAL`，则需要导出类才能对客户端应用程序可见。 这也是通过遍走列表来完成的`CDynLinkLibrary`。

在 MFC 高级概念示例[DLLHUSK](../overview/visual-cpp-samples.md)中，列表如下所示：

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

MFCxx.DLL 通常在资源和类列表中排在最后。 MFCxx.DLL 包括所有标准 MFC 资源，包括所有标准命令指示的提示字符串。 将其放在列表的尾部允许 DLL 和客户端应用程序本身没有自己的标准 MFC 资源副本，而是依赖于 MFCxx.DLL 中的共享资源。

将所有 DLL 的资源和类名称合并到客户端应用程序的名称空间中，缺点是必须小心您选择什么的代表或名称。 当然，您可以通过不将资源或`CDynLinkLibrary`对象导出到客户端应用程序来禁用此功能。 [DLLHUSK](../overview/visual-cpp-samples.md)示例使用多个标头文件管理共享资源名称空间。 有关使用共享资源文件的更多提示[，请参阅技术说明 35。](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

### <a name="initializing-the-dll"></a>初始化 DLL

如上所述，您通常需要创建一个`CDynLinkLibrary`对象，以便将资源和类导出到客户端应用程序。 您需要提供导出的入口点才能初始化 DLL。 最小，这是一个无效例程，不需要任何参数，也不返回任何内容，但它可以是任何你喜欢的。

如果要使用 DLL 的每个客户端应用程序都必须调用此初始化例程（如果使用此方法）。 您也可以在调用`CDynLinkLibrary``AfxInitExtensionModule`后在 您的`DllMain`中分配此对象。

初始化例程必须在当前应用程序的堆`CDynLinkLibrary`中创建一个对象，并连接到 MFC 扩展 DLL 信息。 这可以通过以下操作完成：

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

本示例中的例程名称*InitXxxDLL*可以是所需的任何内容。 它不需要**外部"C"，** 但这样做会使导出列表更易于维护。

> [!NOTE]
> 如果使用常规 MFC DLL 的 MFC 扩展 DLL，则必须导出此初始化函数。 在使用任何 MFC 扩展 DLL 类或资源之前，必须从常规 MFC DLL 调用此功能。

### <a name="exporting-entries"></a>导出条目

导出类的简单方法是在要导出的每个类和`__declspec(dllimport)`全局`__declspec(dllexport)`函数上使用和。 这使得它更容易，但比命名每个入口点（如下所述）的效率要低，因为您不太了解导出哪些函数，并且不能按 ddinal 导出函数。 TESTDLL1 和 TESTDLL2 使用此方法导出其条目。

更有效的方法（以及 MFCxx.DLL 使用的方法）是通过命名 中的每个条目来手动导出每个条目。DEF 文件。 由于我们从 DLL 导出选择性导出（即不是所有接口），因此我们必须决定要导出的特定接口。 这很困难，因为您必须以 中的条目的形式将混乱的名称指定给链接器。DEF 文件。 不要导出任何C++类，除非您确实需要为其提供符号链接。

如果尝试使用 导出C++类。DEF 文件之前，您可能需要开发一个工具来自动生成此列表。 这可以使用两阶段链接过程来完成。 链接一次 DLL，无需导出，并允许链接器生成 。MAP 文件。 .MAP 文件可用于生成应导出的函数列表，因此，对于某些重新排列，它可用于为 生成 的 EXPORT 条目。DEF 文件。 MFCxx.DLL 和 OLE 和数据库 MFC 扩展 DLL 的导出列表（数为数千）是使用此过程生成的（尽管它不是完全自动的，需要偶尔进行一次手动调整）。

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLink图书馆

MFC 扩展 DLL 没有其`CWinApp`自己的派生对象;相反，`CWinApp`它必须与客户端应用程序的派生对象一起工作。 这意味着客户端应用程序拥有主消息泵、空闲环路等。

如果您的 MFC 扩展 DLL 需要为每个应用程序维护额外的数据，则可以从`CDynLinkLibrary`派生新类并在上面描述的 InitXxxDLL 例程中创建它。 运行时，DLL 可以检查当前应用程序`CDynLinkLibrary`的对象列表，以查找该特定 MFC 扩展 DLL 的对象。

### <a name="using-resources-in-your-dll-implementation"></a>在 DLL 实现中使用资源

如上所述，默认资源负载将遍历查找具有请求资源的第`CDynLinkLibrary`一个 EXE 或 DLL 的对象列表。 所有 MFC API 以及所有内部代码都用于`AfxFindResourceHandle`遍历资源列表以查找任何资源，无论资源可能驻留在何处。

如果只想从特定位置加载资源，请使用 API`AfxGetResourceHandle`并`AfxSetResourceHandle`保存旧句柄并设置新句柄。 在返回到客户端应用程序之前，请确保还原旧资源句柄。 示例 TESTDLL2 使用此方法显式加载菜单。

遍行列表有缺点是速度稍慢，需要管理资源 ID 范围。 它的优点是，链接到多个 MFC 扩展 DLL 的客户端应用程序可以使用任何 DLL 提供的资源，而无需指定 DLL 实例句柄。 `AfxFindResourceHandle`是用于遍走资源列表以查找给定匹配项的 API。 它获取资源的名称和类型，并返回首次找到的资源句柄（或 NULL）。

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>编写使用 DLL 版本的应用程序

### <a name="application-requirements"></a>应用要求

使用 MFC 共享版本的应用程序必须遵循几个简单的规则：

- 它必须具有对象`CWinApp`，并遵循消息泵的标准规则。

- 它必须使用一组必需的编译器标志进行编译（见下文）。

- 它必须与 MFCxx 导入库链接。 通过设置所需的编译器标志，MFC 标头确定应用程序应在链接时链接到哪个库。

- 要运行可执行文件，MFCxx.DLL 必须位于路径或 Windows 系统目录中。

### <a name="building-with-the-development-environment"></a>与开发环境一起构建

如果将内部 makefile 与大多数标准默认值一起使用，则可以轻松地更改项目以生成 DLL 版本。

以下步骤假定您具有与 NAFXCWD 链接的正常运行的 MFC 应用程序。LIB（用于调试）和 NAFXCW。LIB（用于零售），您希望将其转换为使用 MFC 库的共享版本。 您正在运行 Visual C++ 环境，并且具有内部项目文件。

1. 在"**项目"** 菜单上，单击"**属性**"。 在 **"项目默认值****"下的"常规**"页中，将 Microsoft 基础类设置为在共享 DLL （MFCxx.dll）**中使用 MFC。**

### <a name="building-with-nmake"></a>使用 NMAKE 建造

如果您使用的是 Visual C++的外部 makefile 功能，或者直接使用 NMAKE，则必须编辑 makefile 以支持编译器和链接器选项

必需的编译器标志：

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

标准 MFC 标头需要定义此符号：

- **/MD**应用程序必须使用 C 运行时库的 DLL 版本

所有其他编译器标志都遵循 MFC 默认值（例如，_DEBUG用于调试）。

编辑库的链接器列表。 更改 NAFXCWD。LIB 到 MFCxxD.LIB 并更改 NAFXCW。LIB 到 MFCxx.LIB。 替换 LIBC。与 MSVCRT 的 LIB。自由。 与任何其他 MFC 库一样，将 MFCxxD.LIB 放在任何 C 运行时库**之前**非常重要。

可以选择将 **/D_AFXDLL**添加到零售和调试资源编译器选项（实际使用 **/R**编译资源的选项）。 这样，通过共享 MFC DLL 中存在的资源，最终可执行文件变小。

进行这些更改后，需要进行完全重建。

### <a name="building-the-samples"></a>生成示例

大多数 MFC 示例程序都可以从 Visual C++ 或从命令行的共享 NMAKE 兼容 MAKEFILE 构建。

要将这些示例中的任何一个转换为使用 MFCxx.DLL，可以加载 。MAK 文件进入可视化C++并设置上述项目选项。 如果使用 NMAKE 生成，则可以在 NMAKE 命令行上指定"AFXDLL_1"，并使用共享 MFC 库生成示例。

MFC 高级概念示例[DLLHUSK](../overview/visual-cpp-samples.md)采用 MFC 的 DLL 版本构建。 此示例不仅说明了如何构建与 MFCxx.DLL 链接的应用程序，还说明了 MFC DLL 打包选项的其他功能，如本文说明的稍后描述的 MFC 扩展 DLL。

### <a name="packaging-notes"></a>包装说明

DLL 的零售版本 （MFCxx[U]）。DLL） 可自由再分发。 DLL 的调试版本不可自由再分发，应仅在应用程序开发期间使用。

调试 DLL 提供调试信息。 通过使用 VisualC++调试器，可以跟踪应用程序以及 DLL 的执行。 版本 DLL （MFCxx_U]）。DLL） 不包含调试信息。

如果自定义或重建 DLL，则应将其称为 MFC SRC 文件 MFCDLL 以外的内容。MAK 描述了生成选项，并包含重命名 DLL 的逻辑。 重命名文件是必要的，因为这些 DLL 可能由许多 MFC 应用程序共享。 让自定义版本的 MFC DLL 替换安装在系统上的 MFC DLL 可能会使用共享 MFC DLL 中断另一个 MFC 应用程序。

不建议重建 MFC DLL。

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>如何实施 MFCxx.DLL

以下部分介绍如何实现 MFC DLL （MFCxx.DLL 和 MFCxxD.DLL）。 如果只想将 MFC DLL 与应用程序一起使用 MFC DLL，则了解此处的详细信息也并不重要。 此处的详细信息对于了解如何编写 MFC 扩展 DLL 并非至关重要，但了解此实现可以帮助您编写自己的 DLL。

### <a name="implementation-overview"></a>实现概述

如上所述，MFC DLL 实际上是 MFC 扩展 DLL 的特殊情况。 它具有大量导出大量类。 我们在 MFC DLL 中还执行一些其他操作，使其比常规 MFC 扩展 DLL 更特别。

### <a name="win32-does-most-of-the-work"></a>Win32 做大部分工作

16 位版本的 MFC 需要许多特殊技术，包括堆栈段上的每个应用数据、由大约 80x86 程序集代码创建的特殊段、每个进程异常上下文和其他技术。 Win32 直接支持 DLL 中的每个进程数据，这是您大多数时候想要的。 在大多数情况下，MFCxx.DLL 只是 NAFXCW。以 DLL 打包的 LIB。 如果查看 MFC 源代码，你会发现很少#ifdef_AFXDLL，因为需要进行的特殊情况很少。 特殊案例专门处理 Windows 3.1 上的 Win32（也称为 Win32）。 Win32s 不支持每进程 DLL 数据，因此 MFC DLL 必须使用线程本地存储 （TLS） Win32 API 来获取进程本地数据。

### <a name="impact-on-library-sources-additional-files"></a>对库源、其他文件的影响

**_AFXDLL**版本对普通 MFC 类库源和标头的影响相对较小。 有一个特殊的版本文件（AFXV_DLL。H）以及额外的头文件（AFXDLL_。H） 包括主 AFXWIN。H 标头。 AFXDLL_H 标头包括`CDynLinkLibrary``_AFXDLL`应用程序和 MFC 扩展 DLL 的类和其他实现详细信息。 AFXDLLX。H 标头用于构建 MFC 扩展 DLL（有关详细信息，请参阅上文）。

MFC SRC 中 MFC 库的常规源在`_AFXDLL`#ifdef下具有一些附加条件代码。 其他源文件（DLLINIT）。CPP） 包含 MFC 共享版本的额外 DLL 初始化代码和其他胶水。

为了构建 MFC 的共享版本，提供了其他文件。 （有关如何构建 DLL 的详细信息，请参阅下文。

- 两。DEF 文件用于导出用于调试 （MFCxxD.DEF） 和 DLL 版本 （MFCxx.DEF） 的 MFC DLL 入口点。

- A .RC 文件 （MFCDLL.RC） 包含所有标准 MFC 资源和 DLL 的 VERSIONINFO 资源。

- A .CLW 文件 （MFCDLL.CLW） 用于允许使用 ClassWizard 浏览 MFC 类。 注意：此功能对于 MFC 的 DLL 版本并不特别。

### <a name="memory-management"></a>内存管理

使用 MFCxx.DLL 的应用程序使用 MSVCRTxx.DLL（共享 C 运行时 DLL）提供的常见内存分配器。 应用程序、任何 MFC 扩展 DLL 以及 MFC DLL 本身使用此共享内存分配器。 通过使用共享 DLL 进行内存分配，MFC DLL 可以分配稍后由应用程序释放的内存，反之亦然。 由于应用程序和 DLL 都必须使用相同的分配器，因此不应重写C++全局**运算符 new****或删除**。 相同的规则适用于 C 运行时内存分配例程的其余部分（如**malloc、realloc、free**等**realloc**）。 **free**

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>__declspec（dllexport）和 DLL 命名

我们不使用C++编译器`class`**的__declspec（dllexport）** 功能。 相反，类库源（MFCxx.DEF 和 MFCxxD.DEF）中包含导出列表。 仅导出这些选定的入口点集（函数和数据）。 其他符号（如 MFC 私有实现函数或类）不导出 所有导出都由单位完成，没有驻留名称或非居民名称表中的字符串名称。

使用`class`**__declspec（dllexport）** 可能是构建较小 DLL 的可行替代方法，但在 MFC 等大型 DLL 的情况下，默认导出机制具有效率和容量限制。

这一切意味着我们可以在版本 MFCxx.DLL 中打包大量功能，这些功能只有大约 800 KB，同时不会影响很多执行或加载速度。 如果不使用这种技术，MFCxx.DLL 会大 10 万。 这也使得可以在 的末尾添加其他入口点。DEF 文件允许简单的版本控制，同时不影响通过单位导出的速度和大小效率。 MFC 类库中的主要版本版本版本将更改库名称。 即 MFC30。DLL 是包含 MFC 类库版本 3.0 的可再分发 DLL。 例如，在假设的 MFC 3.1 中升级此 DLL，DLL 将命名为 MFC31。而是 DLL。 同样，如果修改 MFC 源代码以生成 MFC DLL 的自定义版本，请使用其他名称（最好是名称中没有"MFC"的名称）。

## <a name="see-also"></a>另请参阅

[技术说明（按编号）](../mfc/technical-notes-by-number.md)<br/>
[按类别分类的技术说明](../mfc/technical-notes-by-category.md)
