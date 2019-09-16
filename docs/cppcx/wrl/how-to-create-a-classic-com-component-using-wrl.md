---
title: 如何：使用 WRL 创建经典 COM 组件
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: ec762b07caa30ce9aa6f4c67f84bb66ae884a7cf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498386"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>如何：使用 WRL 创建经典 COM 组件

除了将其用于通用 Windows 平台C++ （UWP）应用之外，还可以使用 Windows 运行时模板库（WRL）来创建基本经典 COM 组件，以便在桌面应用中使用。 对于 COM 组件的创建，Windows 运行时C++模板库可能需要比 ATL 更少的代码。 有关 Windows 运行时C++模板库支持的 COM 子集的信息，请参阅[Windows 运行时C++模板库（WRL）](windows-runtime-cpp-template-library-wrl.md)。

本文档演示如何使用 Windows 运行时C++模板库来创建基本的 COM 组件。 尽管可以使用最适合你需求的部署机制，本文档还会展示一种从桌面应用程序注册及使用 COM 组件的基本方法。

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>使用 Windows 运行时C++模板库创建基本的经典 COM 组件

1. 在 Visual Studio 中，创建一个**空白解决方案**项目。 为项目命名，例如， `WRLClassicCOM`。

2. 将**Win32 项目**添加到解决方案。 为项目命名，例如， `CalculatorComponent`。 在 "**应用程序设置**" 选项卡上，选择 " **DLL**"。

3. 将**Midl 文件（.idl）** 文件添加到项目。 为文件命名，例如`CalculatorComponent.idl`。

4. 将此代码添加到 CalculatorComponent.idl：

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. 在 CalculatorComponent.cpp 中，定义 `CalculatorComponent` 类。 该类继承自[Microsoft：： WRL：： RuntimeClass。](runtimeclass-class.md) `CalculatorComponent` [Microsoft：： WRL：： RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md)指定类派生自[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) ，而不是[IInspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable)。 （`IInspectable`仅适用于 Windows 运行时应用组件。）`CoCreatableClass`为类创建一个工厂，该工厂可与 [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) 等函数一起使用。

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. 使用以下代码替换中`dllmain.cpp`的代码。 此文件定义 DLL 导出函数。 这些函数使用[Microsoft：： WRL：： module](module-class.md)类来管理模块的类工厂。

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. 将**模块定义文件（.def）** 文件添加到项目。 为文件命名，例如`CalculatorComponent.def`。 此文件为链接器提供了要导出的函数的名称。

8. 将此代码添加到 CalculatorComponent.def：

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. 将 runtimeobject.lib 添加到链接器行。 若要了解如何操作，请参阅[。用作链接器输入的 .lib 文件](../../build/reference/dot-lib-files-as-linker-input.md)。

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>从桌面应用程序使用 COM 组件

1. 向 Windows 注册表注册 COM 组件。 为此，请创建一个注册项文件，将其`RegScript.reg`命名为，然后添加以下文本。 将 *\<dll 路径 >* 替换为您的 dll 的路径，例如，。 `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`

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

2. 运行 RegScript，或将其添加到项目的**生成后事件**。 有关详细信息，请参阅[预生成事件/生成后事件命令行对话框](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)。

3. 将**Win32 控制台应用程序**项目添加到解决方案。 为项目命名，例如， `Calculator`。

4. 使用以下代码替换的`Calculator.cpp`内容：

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>可靠编程

本文档使用标准 COM 函数说明你可以使用 Windows 运行时C++模板库创作 com 组件，并将其提供给启用了 com 的任何技术。 你还可以在桌面C++应用中使用 Windows 运行时模板库类型（如[MICROSOFT：： WRL：： ComPtr](comptr-class.md) ）来管理 COM 和其他对象的生存期。 下面的代码使用 Windows 运行时C++模板库来管理`ICalculatorComponent`指针的生存期。 `CoInitializeWrapper` 类是一种 RAII 包装，可保证 COM 库已释放，并保证 COM 库的生存期长于 `ComPtr` 智能指针对象。

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>请参阅

[Windows 运行时 C++ 模板库 (WRL)](windows-runtime-cpp-template-library-wrl.md)