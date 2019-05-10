---
title: 如何：创建传统型 COM 组件使用 WRL
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: bb38f36cdd481e61d049f82159fdc24c3726f646
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398324"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>如何：创建传统型 COM 组件使用 WRL

可以使用 Windows 运行时C++模板库 (WRL) 来创建基本经典 COM 组件，以便在桌面应用程序，此外到通用 Windows 平台 (UWP) 应用的使用。 COM 组件、 Windows 运行时创建C++模板库可能需要更少的代码比 ATL 有关 COM 的信息子集的 Windows 运行时C++模板库支持，请参阅[Windows 运行时C++模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)。

本文档演示如何使用 Windows 运行时C++模板库来创建基本的 COM 组件。 尽管可以使用最适合你需求的部署机制，本文档还会展示一种从桌面应用程序注册及使用 COM 组件的基本方法。

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>若要使用 Windows 运行时C++模板库创建基本经典 COM 组件

1. 在 Visual Studio 中创建**空白解决方案**项目。 该项目命名，例如， `WRLClassicCOM`。

2. 添加**Win32 项目**到解决方案。 该项目命名，例如， `CalculatorComponent`。 上**应用程序设置**选项卡上，选择**DLL**。

3. 添加**Midl 文件 (.idl)** 到项目文件。 例如，命名该文件， `CalculatorComponent.idl`。

4. 将此代码添加到 CalculatorComponent.idl：

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. 在 CalculatorComponent.cpp 中，定义 `CalculatorComponent` 类。 `CalculatorComponent`类继承自[Microsoft::WRL::RuntimeClass](runtimeclass-class.md)。 [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md)指定的类派生[IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)而不[IInspectable](/windows/desktop/api/inspectable/nn-inspectable-iinspectable)。 (`IInspectable`仅适用于 Windows 运行时应用程序组件。)`CoCreatableClass`创建一个工厂可以如与函数一起使用的类[CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)。

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. 使用下面的代码中的代码替换为`dllmain.cpp`。 此文件定义 DLL 导出函数。 这些函数将使用[Microsoft::WRL::Module](module-class.md)类来管理模块的类工厂。

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. 添加**模块定义文件 (.def)** 到项目文件。 例如，命名该文件， `CalculatorComponent.def`。 此文件为链接器提供了要导出的函数的名称。

8. 将此代码添加到 CalculatorComponent.def：

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. 将 runtimeobject.lib 添加到链接器行。 若要了解如何操作，请参阅[。用作链接器输入 lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>从桌面应用程序使用 COM 组件

1. 向 Windows 注册表注册 COM 组件。 为此，请创建注册表项文件，将其命名`RegScript.reg`，并添加以下文本。 替换 *\<dll 的路径 >* DLL 的路径 — 例如， `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`。

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. 运行 RegScript.reg 或将其添加到你的项目**后期生成事件**。 有关详细信息，请参阅[预生成事件/生成后事件命令行对话框](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)。

3. 添加**Win32 控制台应用程序**到解决方案。 该项目命名，例如， `Calculator`。

4. 使用此代码的内容替换为`Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>可靠编程

本文档使用标准 COM 函数来演示您可以使用 Windows 运行时C++模板库创建 COM 组件，并使其可供任何支持 COM 的技术。 你还可以使用 Windows 运行时C++模板库类型，如[Microsoft::WRL::ComPtr](comptr-class.md)在桌面应用程序来管理 COM 及其他对象的生存期。 下面的代码使用 Windows 运行时C++模板库来管理生存期`ICalculatorComponent`指针。 `CoInitializeWrapper` 类是一种 RAII 包装，可保证 COM 库已释放，并保证 COM 库的生存期长于 `ComPtr` 智能指针对象。

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>请参阅

[Windows 运行时 C++ 模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)