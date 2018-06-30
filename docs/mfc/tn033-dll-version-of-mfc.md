---
title: 'TN033: MFC 的 DLL 版本 |Microsoft 文档'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dll
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c47f7888c2801af4dae1a181e4eb836dde4feaaa
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123001"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033：MFC 的 DLL 版本

本说明介绍如何将 MFCxx.DLL 和 MFCxxD.DLL （其中 x 是 MFC 版本号） 共享动态链接库用于 MFC 应用程序和 MFC 扩展 Dll。 有关 MFC 的规则 Dll 的详细信息，请参阅[使用 MFC 作为 DLL 的一部分](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

此技术说明介绍 Dll 的三个的方面。 最后两个是针对更高级的用户：

- [如何生成 MFC 扩展 DLL](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [如何生成的 MFC 应用程序使用 MFC 的 DLL 版本](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [MFC 如何共享动态链接库实现](#_mfcnotes_how_the_mfc30.dll_is_implemented)

如果你有兴趣生成使用可与非 MFC 应用程序 （这称为正则 MFC DLL） 的 MFC 的 DLL，请参阅[技术注意 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)。

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>概述 MFCxx.DLL 支持： 术语和文件

**常规 MFC DLL**： 使用正则 MFC DLL 生成独立 DLL 使用某些 MFC 类。 跨应用程序/DLL 边界的接口为"C"接口，并且客户端应用程序没有为 MFC 应用程序。

这是 DLL 支持 MFC 1.0 中支持的版本。 中描述的那样[技术注意 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md)和 MFC 高级概念示例[DLLScreenCap](../visual-cpp-samples.md)。

> [!NOTE]
> 截至 Visual c + + 版本 4.0 中，术语**USRDLL**已过时，并已替换为静态链接到 MFC 的正则 MFC DLL。 你也可能生成正则表达式动态链接到 MFC 的 MFC DLL。

MFC 3.0 （和更高版本） 支持 MFC 的规则 Dll，并包括 OLE 和数据库类的所有新功能。

**AFXDLL**： 也称为共享版本的 MFC 库。 这是在 MFC 2.0 中添加的新 DLL 支持。 在 MFC 库自身处于大量的 Dll （如下所述），客户端应用程序或 DLL 动态链接它需要的 Dll。 跨应用程序/DLL 边界的接口是 C + + MFC 类接口。 客户端应用程序必须是 MFC 应用程序。 这样可支持所有 MFC 3.0 功能 (异常： 数据库类不支持 UNICODE)。

> [!NOTE]
> 截至 Visual c + + 4.0 版，此类型的 DLL 被称为"扩展 DLL。"

本说明将使用 MFCxx.DLL 来引用的整个 MFC DLL 设置，其中包括：

- 调试： MFCxxD.DLL （合并） 和 MFCSxxD.LIB （静态）。

- 版本： MFCxx.DLL （合并） 并且 MFCSxx.LIB （静态）。

- Unicode 调试： MFCxxUD.DLL （合并） 和 MFCSxxD.LIB （静态）。

- Unicode 版本： MFCxxU.DLL （合并） 并且 MFCSxxU.LIB （静态）。

> [!NOTE]
> MFCSxx [U] [D]。LIB 库用于在与 MFC 一起共享的 Dll。 这些库包含必须静态链接到应用程序或 DLL 的代码。

应用程序链接到相应的导入库：

- 调试： MFCxxD.LIB

- 版本： MFCxx.LIB

- Unicode 调试： MFCxxUD.LIB

- Unicode 版本： MFCxxU.LIB

"MFC 扩展 DLL"是基于 MFCxx.DLL DLL （和/或其他 MFC 共享 Dll）。 此处的 MFC 组件体系结构启动。 如果你从 MFC 类，派生的有用的类，或生成另一个类似于 MFC 的工具包，可以将它放在 DLL 中。 其中 DLL 将使用 MFCxx.DLL，最终客户端应用程序一样。 这允许可重用叶类、 可重复使用基类和可重用的视图/文档类。

## <a name="pros-and-cons"></a>优点和缺点

为何应使用共享的版本的 MFC

- 使用共享的库可以导致较小的应用程序 （最少使用的应用程序的 MFC 库的大多数是小于 10k）。

- 共享的版本的 MFC 支持 MFC 扩展 Dll 和 MFC 的规则 Dll。

- 生成使用共享的 MFC 库的应用程序是比构建静态链接的 MFC 应用程序，因为它不是必需将链接 MFC 本身更快。 这是中尤其如此**调试**生成链接器必须在其中压缩的调试信息 — 通过链接一个 DLL，它已包含的调试信息，没有调试信息变少，需要压缩你的应用程序。

为什么你不应使用共享的版本的 MFC:

- 传送使用共享的库的应用程序需要您在发运 MFCxx.DLL （及其他） 使用你的程序的库。 MFCxx.DLL 许多 Dll，如自由可再发行组件，但你仍必须 DLL 在安装你的安装程序。 此外，你必须将发运 MSVCRTxx.DLL，其中包含用于你的程序和 MFC Dll 本身的 C 运行时库。

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> 如何编写 MFC 扩展 DLL

MFC 扩展 DLL 是一个包含类和写入修饰 MFC 类的功能的函数的 DLL。 MFC 扩展 DLL 与应用程序使用它，有几个额外的注意事项相同的方式使用共享的 MFC Dll:

- 生成过程等同于生成几个其他编译器和链接器选项使用共享的 MFC 库的应用程序。

- MFC 扩展 DLL 不具有`CWinApp`-派生类。

- MFC 扩展 DLL 必须提供一个特殊`DllMain`。 AppWizard 提供`DllMain`可以修改的函数。

- MFC 扩展 DLL 通常会提供初始化例程，以创建`CDynLinkLibrary`如果 MFC 扩展 DLL 希望导出`CRuntimeClass`es 或对应用程序的资源。 派生的类`CDynLinkLibrary`如果必须由 MFC 扩展 DLL 维护每个应用程序数据可能会使用。

下面更详细地介绍这些注意事项。 你还应该参考 MFC 高级概念示例[DLLHUSK](../visual-cpp-samples.md)由于它阐释了：

- 生成使用共享的库的应用程序。 (DLLHUSK。EXE 是 MFC 应用程序以及其他 Dll 动态链接到 MFC 库。）

- 生成 MFC 扩展 DLL。 (请注意的特殊标志如`_AFXEXT`生成 MFC 扩展 DLL 中使用的)

- MFC 扩展 Dll 的两个示例。 一个显示 MFC 扩展 DLL 用有限的导出 (TESTDLL1) 和其他的导出整个类接口 (TESTDLL2) 所示的基本结构。

客户端应用程序和任何 MFC 扩展 Dll 必须使用相同版本的 MFCxx.DLL。 你应遵循的 MFC DLL 的约定，并提供这两个调试和零售 （/ 释放） 版本的 MFC 扩展 DLL。 这允许客户端程序来生成其应用程序的调试和发布版本并将这些链接与合适的调试或零售版本的所有 Dll。

> [!NOTE]
>  C + + 名称重整和导出问题，因为 MFC 扩展 DLL 中的导出列表可能会不同同一 DLL 的调试和发布版本和 Dll 之间不同的平台。 零售 MFCxx.DLL 已大约 2000年导出入口点;调试 MFCxxD.DLL 大约 3000 已导出入口点。

### <a name="quick-note-on-memory-management"></a>有关内存管理的快速说明

节"内存管理"结尾处此技术说明描述 MFCxx.DLL 使用共享版本的 MFC 的实现。 你需要知道要实现只需 MFC 扩展 DLL 此处所述的信息。

MFCxx.DLL 和所有 MFC 扩展 Dll 加载到客户端应用程序的地址空间将使用相同的内存分配器，资源加载和其他 MFC"全局"状态就像它们是在同一应用程序。 这很重要，因为非 MFC DLL 库和静态链接到 MFC 的规则 MFC Dll 精确求反并具有其自己的内存池之外分配每个 DLL。

如果 MFC 扩展 DLL 分配内存，然后该内存可以自由混合使用与任何其他应用程序分配的对象中。 此外，如果使用共享的 MFC 库的应用程序崩溃，操作系统的保护将保持共享 DLL 任何其他 MFC 的应用程序的完整性。

同样其他"全局"的 MFC 状态，类似于当前的可执行文件加载资源，还为客户端应用程序和所有 MFC 扩展 Dll，以及 MFCxx.DLL 本身之间共享。

### <a name="building-an-mfc-extension-dll"></a>生成 MFC 扩展 DLL

你可以使用应用程序向导创建 MFC 扩展 DLL 项目，并且将自动生成的相应编译器和链接器设置。 它是还生成`DllMain`可以修改的函数。

如果你要将现有项目转换为 MFC 扩展 DLL，开始构建使用共享的版本的 MFC 中，一个应用程序的标准规则，然后执行以下操作：

- 添加 **/D_AFXEXT**到编译器标志。 在项目属性对话框中，选择 C/c + + 节点。 然后选择预处理器类别。 添加`_AFXEXT`到定义宏字段中，每个项用分号分隔。

- 删除 **/Gy**编译器开关。 在项目属性对话框中，选择 C/c + + 节点。 然后选择代码生成类别。 确保未启用"启用函数级链接"选项。 这将使更轻松地导出类，因为链接器不会删除未引用的函数。 如果原始项目用于生成正则表达式 MFC DLL 静态链接到 MFC，更改 **/MT [d]** 编译器选项 **/MD [d]**。

- 生成与导出库 **/DLL**到链接的选项。 这将创建一个新的目标，指定为目标类型的 Win32 动态链接库时设置。

### <a name="changing-your-header-files"></a>更改标头文件

MFC 扩展 DLL 的目标通常是将导出到一个或多个应用程序可以使用该功能的一些常用的功能。 这可以归结为导出类和全局函数，可用于客户端应用程序。

为了执行此操作必须确保每个成员函数被标记为导入或导出根据。 这需要特殊的声明：`__declspec(dllexport)`和`__declspec(dllimport)`。 当客户端应用程序使用你的类时，你希望它们声明为`__declspec(dllimport)`。 当生成 MFC 扩展 DLL 本身时，它们应被声明为`__declspec(dllexport)`。 此外，函数必须实际导出，以便客户端程序在加载时将绑定到它们。

若要导出整个类，使用`AFX_EXT_CLASS`类定义中。 由框架作为定义此宏`__declspec(dllexport)`时`_AFXDLL`和`_AFXEXT`定义，但定义为`__declspec(dllimport)`时`_AFXEXT`未定义。 `_AFXEXT` 生成 MFC 扩展 DLL 时仅定义按上文所述，。 例如：

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>不会导出整个类

有时你可能想要导出只是你的类的个别必要成员。 例如，如果要导出`CDialog`-派生类中，你可能只需导出构造函数和`DoModal`调用。 你可以导出使用 DLL 的这些成员。DEF 文件，但你还可以使用`AFX_EXT_CLASS`得多您需要将导出单个成员上一样。

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

执行此操作时，你可能会遇到其他问题中，因为你无法再导出类的所有成员。 问题是 MFC 宏的工作方式。 MFC 的帮助器宏多种实际声明或定义数据成员。 因此，这些数据成员将还需要从 DLL 导出。

例如，DECLARE_DYNAMIC 宏定义，如下所示生成 MFC 扩展 DLL 时：

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \

```

开始的行"静态`AFX_DATA`"声明内您的类的静态对象。 若要正确进行导出此类，并从客户端访问运行时信息。EXE，你需要导出此静态对象。 因为使用修饰符声明的静态对象`AFX_DATA`，只需定义`AFX_DATA`要`__declspec(dllexport)`时生成您的 DLL 并将其作为定义`__declspec(dllimport)`生成你的客户端可执行文件时。

如上所述，`AFX_EXT_CLASS`已在这种方式中定义。 你只需重新定义`AFX_DATA`会作为相同`AFX_EXT_CLASS`解决你的类定义。

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

MFC 始终使用`AFX_DATA`符号在它定义在其中的宏，因此此方法将适用于这种情况下的数据项上。 例如，它将适用于 DECLARE_MESSAGE_MAP。

> [!NOTE]
> 如果你要导出整个类而不是所选的类的成员，将自动导出静态数据成员。

你可以使用相同的技术自动导出`CArchive`提取运算符使用 DECLARE_SERIAL 和 IMPLEMENT_SERIAL 宏的类。 导出存档运算符包括类声明 (位于中。H 文件中） 替换为以下代码：

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>_AFXEXT 的限制

您可以使用 _**AFXEXT** MFC 扩展 Dll，只要你没有 MFC 扩展 Dll 的多个层的预处理器符号。 如果你有 MFC 扩展 Dll 可调用或派生自中你自己的 MFC 扩展 Dll，后者又派生自 MFC 类，类必须使用你自己的预处理器符号以避免多义性。

问题在于该在 Win32，所以必须显式声明为任何数据`__declspec(dllexport)`如果它是从 DLL，导出和`__declspec(dllimport)`是否要从 DLL 导入它。 在定义`_AFXEXT`，MFC 标头确保`AFX_EXT_CLASS`正确定义。

如果你具有多个层、 一个符号如`AFX_EXT_CLASS`是不够的因为 MFC 扩展 DLL 可能会导出新类，以及从另一个 MFC 扩展 DLL 导入其他类。 若要处理此问题，使用特殊的预处理器符号，该值指示要生成 DLL 本身还是使用该 DLL。 例如，假设两个 MFC 扩展 Dll、 A.DLL 和 B.DLL。 每个分别导出 A.H 和 B.H 中的某些类。 B.DLL 使用 A.DLL 类。 标头文件将如下所示：

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

A.DLL 生成时，它用生成 **/DA_IMPL**和 B.DLL 生成时，它用生成 **/DB_IMPL**。 通过使用单独的符号，每个 DLL，导出 CExampleB 和 CExampleA 时生成 B.DLL 导入。 CExampleA 导出生成 A.DLL 时，导入由 B.DLL （或某些其他客户端）。

使用内置时，无法完成这种类型的分层`AFX_EXT_CLASS`和`_AFXEXT`预处理器符号。 上面所述的技术可解决此问题的方式与 MFC 本身的机制使用时生成其 OLE、 数据库和网络 MFC 扩展 Dll 中。

### <a name="not-exporting-the-entire-class"></a>不会导出整个类

同样，你将需要不导出整个类时要特别小心。 你必须确保正确导出由 MFC 宏创建的必需数据项目。 这可以通过重新定义`AFX_DATA`对特定类的宏。 每当不导出整个类的时候，你应进行此操作。

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

下面是应置于 MFC 扩展 DLL 的主源代码文件的精确代码。 它应来自后标准包括。 请注意，当你使用应用程序向导创建 MFC 扩展 DLL 的初学者文件，它会提供`DllMain`为你。

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

调用`AfxInitExtensionModule`捕获模块运行时类 (`CRuntimeClass`结构) 以及其对象工厂 (`COleObjectFactory`对象) 用于更高版本在`CDynLinkLibrary`创建对象。 （可选） 调用`AfxTermExtensionModule`，MFC 清除 MFC 扩展 DLL 时每个进程分离 (这发生在进程退出，或为卸载 DLL`FreeLibrary`调用) 从 MFC 扩展 DLL。 由于不会动态加载 Dll 的大多数 MFC 扩展 （通常情况下，它们在连接通过其导入库），调用`AfxTermExtensionModule`通常是不必要。

如果你的应用程序加载，并动态释放 MFC 扩展 Dll，一定要调用`AfxTermExtensionModule`如上所示。 此外请务必使用`AfxLoadLibrary`和`AfxFreeLibrary`(而不是 Win32 函数`LoadLibrary`和`FreeLibrary`) 如果你的应用程序使用多个线程，或如果它动态加载 MFC 扩展 DLL。 使用`AfxLoadLibrary`和`AfxFreeLibrary`将确保在加载和卸载 MFC 扩展 DLL 时执行的启动和关闭代码不会损坏全局 MFC 状态。

标头文件 AFXDLLX 中。H 包含特殊定义 MFC 扩展 Dll，如的定义中使用结构`AFX_EXTENSION_MODULE`和`CDynLinkLibrary`。

全局*extensionDLL*必须按所示声明。 与不同的是 16 位版本的 MFC 中，你可以分配内存，并且在此期间，调用 MFC 的函数，因为 MFCxx.DLL 完全初始化时你`DllMain`调用。

### <a name="sharing-resources-and-classes"></a>共享资源和类

简单 MFC 扩展 Dll 仅需要将少数几个低带宽函数导出到客户端应用程序而不安装其他。 多个用户界面密集型 Dll 可能想要将资源和 c + + 类导出到客户端应用程序。

导出资源均通过的资源列表。 在每个应用程序是单向链表的`CDynLinkLibrary`对象。 在查看资源时，大部分加载资源的标准 MFC 实现应当首先查看当前的资源模块 (`AfxGetResourceHandle`) 如果未找到审核的列表`CDynLinkLibrary`尝试加载请求的资源的对象。

在给定 c + + 类名称的 c + + 对象的动态创建是类似的。 MFC 对象反序列化机制需要具有的所有`CRuntimeClass`对象注册，以便它可以重新构造通过动态创建的基于以前存储的内容所需类型的 c + + 对象。

如果希望客户端应用程序使用 MFC 扩展 DLL 中的类`DECLARE_SERIAL`，则将需要导出您的类对客户端应用程序可见。 这还会通过遍历`CDynLinkLibrary`列表。

对于 MFC 高级概念示例[DLLHUSK](../visual-cpp-samples.md)，列表如下所示：

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

MFCxx.DLL 是通常的最后一个的资源和类列表。 MFCxx.DLL 包括所有标准 MFC 资源，包括提示字符串用于所有标准命令 Id。 将其放在列表的结尾允许 Dll 和客户端应用程序本身不具有其自己的标准 MFC 资源，但为依赖 MFCxx.DLL 中的共享资源上改为副本。

合并到客户端应用程序的命名空间的资源和类名称的所有 Dll 都有缺点，一定要注意哪些 Id 或你选择的名称。 你可以当然禁用此功能通过不导出你的资源或`CDynLinkLibrary`到客户端应用程序对象。 [DLLHUSK](../visual-cpp-samples.md)示例通过使用多个标头文件来管理共享的资源命名空间。 请参阅[技术注意 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)有关使用共享的资源文件的更多技巧。

### <a name="initializing-the-dll"></a>初始化 DLL

如上所述，你通常要创建`CDynLinkLibrary`才能导出到客户端应用程序的资源和类的对象。 你将需要提供初始化该 DLL 的导出的入口点。 按最小的方式，这是一个 void 例程不采用任何参数并返回任何内容，但它可以是您喜欢的任何。

每个想要使用您的 DLL 的客户端应用程序必须调用此初始化例程，如果你使用此方法。 你还可能会分配这`CDynLinkLibrary`对象中你`DllMain`之后调用`AfxInitExtensionModule`。

初始化例程必须创建`CDynLinkLibrary`在当前应用程序的堆中，最多 MFC 扩展 DLL 信息有线的对象。 这可实现替换为以下内容：

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

例程的名称， *InitXxxDLL*此示例中，可以为任何需要的内容。 它不需要为**extern"C"**，但这样易于维护的导出列表也使。

> [!NOTE]
> 如果你使用你从常规 MFC DLL 的 MFC 扩展 DLL，你必须导出此初始化函数。 使用任何 MFC 扩展 DLL 类或资源之前，必须从 MFC DLL 的常规调用此函数。

### <a name="exporting-entries"></a>导出条目

若要导出你的类的简单方法是使用`__declspec(dllimport)`和`__declspec(dllexport)`对每个类和全局您要导出的函数。 这将使其容易得多，但效率低于命名 （如下所述） 每个入口点，因为你可以更少控制导出哪些函数和不能按序号导出的函数。 TESTDLL1 和 TESTDLL2 使用此方法导出其条目。

更高效的方法 （和使用 MFCxx.DLL 的方法） 是通过命名每个条目中的手动导出每个条目。DEF 文件。 由于我们要从我们 DLL （即，不是全部） 导出选择性导出，我们必须确定我们想要导出的特定接口。 这是困难的因为你必须在窗体中的条目指定到链接器的重整的名称。DEF 文件。 不导出任何 c + + 类，除非你确实需要对符号链接。

如果你已尝试导出 c + + 类使用。DEF 文件之前，你可能想要开发的工具自动生成此列表。 这可以使用两阶段链接过程。 链接 DLL 没有导出中，使用一次并允许链接器生成。映射文件。 。映射文件可以用于生成应导出的函数的列表，因此与某些重新排列，它可以用于生成导出条目你。DEF 文件。 MFCxx.DLL 和 OLE 和数据库 MFC 扩展 Dll，几千在数量、 的导出列表是使用此类进程生成的 （尽管它不是完全自动的并且需要一些手动优化每一次在一段）。

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs。CDynLinkLibrary

MFC 扩展 DLL 不具有`CWinApp`-派生自己的对象; 而是必须过使用`CWinApp`-派生对象的客户端应用程序。 这意味着，客户端应用程序拥有的主消息泵，空闲循环，依此类推。

如果你 MFC 扩展 DLL 必须保持的每个应用程序的额外数据，你可以派生新类从`CDynLinkLibrary`和上面描述的例程 InitXxxDLL 中创建它。 DLL 运行时，可以检查当前应用程序的列表的`CDynLinkLibrary`要查找该特定的 MFC 扩展 DLL 的一个对象。

### <a name="using-resources-in-your-dll-implementation"></a>DLL 实现中使用的资源

如上所述，默认资源负载将引导的列表`CDynLinkLibrary`查找第一个 EXE 或 DLL 中具有请求的资源的对象。 所有 MFC Api 以及所有内部的代码使用`AfxFindResourceHandle`遍历资源列表以找到任何资源，无论它可能驻留在其中。

如果你想要仅从特定的位置加载资源，使用 Api`AfxGetResourceHandle`和`AfxSetResourceHandle`保存旧句柄并设置新的句柄。 请确保还原旧资源句柄，然后返回到客户端应用程序。 示例 TESTDLL2 用于显式加载菜单使用此方法。

遍历列表也有缺点，它会稍慢些，并需要管理资源 ID 范围。 它具有链接到多个 MFC 扩展 Dll 的客户端应用程序可以使用任何 DLL 提供的资源，而无需指定 DLL 实例句柄的优势。 `AfxFindResourceHandle` 是一个 API 用于遍历资源列表以查找给定的匹配项。 它采用的名称和类型的资源，并返回的第一次找的资源句柄 （或 NULL）。

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> 编写的应用程序使用的 DLL 版本

### <a name="application-requirements"></a>应用程序的要求

使用共享的版本的 MFC 的应用程序必须遵循一些简单的规则：

- 它必须具有`CWinApp`对象，并符合标准的规则的消息泵。

- 它必须使用一组所需的编译器标志 （见下文） 进行编译。

- 它必须与 MFCxx 导入库链接。 通过设置所需的编译器标志，MFC 标头确定在链接时应用程序应与链接的库。

- 若要运行可执行文件，MFCxx.DLL 必须路径上或在 Windows 系统目录中。

### <a name="building-with-the-development-environment"></a>生成与开发环境

如果你使用内部生成文件具有大多数标准默认值，你可以轻松更改要生成的 DLL 版本的项目。

以下步骤假定你有与 NAFXCWD 链接正常运行 MFC 应用程序。LIB （适用于调试） 和 NAFXCW。LIB （对于零售版） 和你想要将其转换为使用共享的版本的 MFC 库。 您正在运行的 Visual c + + 环境，并且具有内部项目文件。

1. 上**项目**菜单上，单击**属性**。 在**常规**下页上**项目默认值**，设置为 Microsoft 基础类**在共享的 DLL 中使用 MFC** (MFCxx(d).dll)。

### <a name="building-with-nmake"></a>使用 NMAKE 生成

如果你正在使用外部生成文件功能的 Visual c + +，或直接使用 NMAKE，你将必须编辑你的生成文件，以支持编译器和链接器选项

必需的编译器标志：

- **/ D_AFXDLL /MD**  
  **/ D_AFXDLL**

标准 MFC 标头需要定义该符号：

- **/MD**应用程序必须使用 C 运行时库的 DLL 版本

所有其他编译器标志遵循 MFC 的默认值 (例如，用于调试的 _DEBUG)。

编辑库的链接器的列表。 更改 NAFXCWD。LIB 到 MFCxxD.LIB 和更改 NAFXCW。到 MFCxx.LIB LIB。 替换 LIBC。LIB 与 MSVCRT。LIB。 因为与任何其他 MFC 库它是重要 MFCxxD.LIB 位于**之前**任何 C 运行库。

根据需要添加 **/D_AFXDLL**到你的零售和调试资源编译器选项 (实际编译的资源的一个 **/R**)。 这样就可以共享 MFC Dll 中存在的资源较小进行最终可执行文件。

进行这些更改之后，完全重新生成是必需的。

### <a name="building-the-samples"></a>生成示例

从 Visual c + + 或从命令行生成 NMAKE 兼容共享的文件，可以生成大部分 MFC 示例程序。

若要转换的这些示例使用 MFCxx.DLL 任何，你可以加载。MAK 到 Visual c + + 文件，并设置项目选项，按上文所述。 如果你使用 NMAKE 生成，你可以指定"AFXDLL = 1"上 NMAKE 命令行，将生成该示例使用共享的 MFC 库。

MFC 高级概念示例[DLLHUSK](../visual-cpp-samples.md)使用 MFC 的 DLL 版本生成的。 此示例不只演示如何构建与 MFCxx.DLL，链接的应用程序，但它还阐释如更高版本中此技术说明描述 MFC 扩展 Dll 的 MFC DLL 打包选项的其他功能。

### <a name="packaging-notes"></a>打包说明

零售版本的 Dll (MFCxx [U]。DLL) 是自由地重新发布。 Dll 的调试版本是不可自由地重新发布，应仅在你的应用程序开发期间使用。

使用调试信息提供了调试 Dll。 通过使用 Visual c + + 调试器，你可以跟踪你的应用程序，以及该 DLL 的执行情况。 版本 Dll (MFCxx [U]。DLL) 不包含调试信息。

如果自定义或重新生成 Dll，则你应调用它们的内容"MFCxx"MFC SRC 文件 MFCDLL 之外。MAK 描述生成选项，并包含用于重命名该 DLL 的逻辑。 重命名文件是必需的因为这些 Dll 可能由很多 MFC 应用程序共享。 MFC Dll 替换你自定义版本安装在系统上可能会中断另一个使用共享的 MFC Dll 的 MFC 应用程序。

不建议重新生成 MFC Dll。

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> 如何实现 MFCxx.DLL

以下部分介绍如何实现 MFC DLL （MFCxx.DLL 和 MFCxxD.DLL）。 了解的详细信息并不重要信息： 如果所有你想要执行是你的应用程序中使用 MFC DLL。 此处的详细信息不重要对于了解如何编写 MFC 扩展 DLL，但了解此实现可能帮助你编写自己的 DLL。

### <a name="implementation-overview"></a>实现概述

MFC DLL 实际上是一种特殊情况的 MFC 扩展 DLL，按上文所述。 它具有大量的导出的大量的类。 有几个使其更特殊比常规 MFC 扩展 DLL 的其他事项我们在 MFC DLL 中执行操作。

### <a name="win32-does-most-of-the-work"></a>Win32 完成大部分工作

16 位版本的 MFC 需要大量的特殊技术包括每个应用程序数据上的堆栈段，特殊的段由某些 80x86 程序集代码、 每个进程异常上下文和其他技术。 Win32 直接支持每个进程的数据中一个 DLL，即你想大部分时间。 在大多数情况下 MFCxx.DLL 是只需 NAFXCW。在 DLL 中打包的 LIB。 如果你查看 MFC 源代码，你将找到很少 #ifdef _AFXDLL，因为有极少数需要进行的特殊情况。 是不是专门在 Windows 3.1 （也称为 Win32s） 的 Win32 处理特殊情况。 Win32s 执行不支持每个进程 DLL 数据直接因此 MFC DLL 必须使用线程本地存储 (TLS) 来获取进程的本地数据的 Win32 Api。

### <a name="impact-on-library-sources-additional-files"></a>对库源，其他文件的影响

影响 **_AFXDLL**上的正常的 MFC 类库源和标头的版本是相对较小。 没有特殊版本文件 (AFXV_DLL。H），以及其他标头文件 (AFXDLL_。H） 包括主 AFXWIN。H 标头。 AFXDLL_。H 标头包括`CDynLinkLibrary`类和其他实现详细信息的同时`_AFXDLL`应用程序和 MFC 扩展 Dll。 AFXDLLX。H 标头提供用于生成 MFC 扩展 Dll （请参阅上面有关详细信息）。

到 MFC SRC 中的 MFC 库的正则源具有一些附加条件代码下的`_AFXDLL`#ifdef。 其他的源文件 (DLLINIT。CPP) 包含额外的 DLL 初始化代码和其他粘附共享版本的 MFC。

若要生成共享的版本的 MFC，提供了其他文件。 （请参阅下面有关如何生成 DLL 的详细信息。）

- 两个。DEF 文件用于导出调试 (MFCxxD.DEF) 的 MFC DLL 入口点，且发行版本的 DLL (MFCxx.DEF) 版本。

- 一个。RC 文件 (MFCDLL。RC) 包含所有标准 MFC 资源和 VERSIONINFO 资源中的 dll。

- 答:。CLW 文件 (MFCDLL。以允许浏览 MFC 类使用 ClassWizard 提供 CLW)。 注意： 此功能不是特定于 MFC 的 DLL 版本的。

### <a name="memory-management"></a>内存管理

使用 MFCxx.DLL 的应用程序使用提供 MSVCRTxx.DLL，共享的 C 运行时 DLL 的一个常见内存分配器。 应用程序、 任何 MFC 扩展 Dll 和以及 MFC Dll 本身使用此共享的内存分配器。 通过使用内存分配共享的 DLL，MFC Dll 可以分配由应用程序，反之亦然更高版本将被释放的内存。 由于应用程序和 DLL 必须使用相同的分配器，因此不应覆盖全局 c + +**运算符 new**或**运算符 delete**。 相同的规则适用于 C 运行时内存分配例程的其余部分 (如**malloc**， **realloc**，**免费**，等)。

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>序号和类 __declspec （dllexport） 和 DLL 命名

我们不会使用`class` **__declspec （dllexport)** c + + 编译器的功能。 相反，一组导出是附带类库源 （MFCxx.DEF 和 MFCxxD.DEF）。 导出仅这些选定的一组入口点 （函数和数据）。 其他符号，如 MFC 私有实现函数或类，不会导出所有导出都完成而无需在常驻或非居民名称表中的字符串名称的序号。

使用`class` **__declspec （dllexport)** 可能是可行的替代方案，用于构建较小的 Dll，但在 MFC 中，默认值导出机制类似较大的 DLL 的情况下具有效率和容量限制。

此的所有方法都是功能的什么我们可以打包大量的版本都才大约 800 KB，而无需破坏多执行或加载速度的 MFCxx.DLL 中。 MFCxx.DLL 已经是更大的 100k 此方法尚未使用。 这也使得可以在末尾添加其他入口点。DEF 文件以允许简单版本控制而不会影响按序号导出的速度和大小的效率。 MFC 类库中的主要版本修订将更改库名称。 也就是说，MFC30。DLL 是包含 3.0 版的 MFC 类库的可再发行组件 DLL。 此 DLL，升级在假设的 MFC 3.1 中，假设 DLL 将被命名为 MFC31。DLL 相反。 同样，如果你修改以生成 MFC DLL 的自定义版本的 MFC 源代码，使用不同的名称 （，最好是一个无需在名称中的"MFC"）。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)  
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)  
