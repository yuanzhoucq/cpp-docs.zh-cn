---
title: 识别 DHTML 控制项目的元素
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 5fabdc815989c21bdf6b0932b9d6826e28d7012a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319503"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>识别 DHTML 控制项目的元素

大多数 DHTML 控制代码与为任何 ATL 控件创建的代码完全一样。 要基本了解通用代码，请通过[ATL 教程](../atl/active-template-library-atl-tutorial.md)，并阅读[创建 ATL 项目和 ATL](../atl/reference/creating-an-atl-project.md) [COM 对象基础](../atl/fundamentals-of-atl-com-objects.md)部分。

DHTML 控件类似于任何 ATL 控件，但：

- 除了控件实现的常规接口外，它还实现了一个用于在C++代码和 HTML 用户界面 （UI） 之间通信的附加接口。 使用此接口，HTML UI 调用C++代码。

- 它为控件 UI 创建 HTML 资源。

- 它允许通过成员变量`m_spBrowser`访问 DHTML 对象模型，这是[IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))类型的智能指针。 使用此指针可以访问 DHTML 对象模型的任何部分。

下图说明了 DLL、DHTML 控件、Web 浏览器和 HTML 资源之间的关系。

![DHTML 控件项目的元素](../atl/media/vc52en1.gif "DHTML 控件项目的元素")

> [!NOTE]
> 此图形上的名称是占位符。 HTML 资源的名称和控件上公开的接口基于您在 ATL 控制向导中分配它们的名称。

在此图形中，元素是：

- **我的 DLL**使用 ATL 项目向导创建的 DLL。

- **DHTML**控件`m_spBrowser`（ ） 使用 ATL 对象向导创建的 DHTML 控件。 此控件通过 Web 浏览器对象的接口访问 Web 浏览器对象及其方法`IWebBrowser2`。 除了控件所需的其他标准接口外，控件本身还公开以下两个接口。

  - `IDHCTL1`控件公开的接口，仅供容器使用。

  - `IDHCTLUI1`用于C++代码和 HTML 用户界面之间通信的调度界面。 Web 浏览器使用控件的调度界面来显示控件。 可以通过调用`window.external`（后）调用此调度接口上要调用的方法名称，从控件的用户界面调用此调度接口的各种方法。 您将从构成`window.external`此控件的 UI 的 HTML 中的 SCRIPT 标记进行访问。 有关在资源文件中调用外部方法的详细信息，请参阅[从 DHTML 调用C++代码](../atl/calling-cpp-code-from-dhtml.md)。

- **IDR_CTL1**HTML 资源的资源 ID。 在这种情况下，其文件名是 DHCTL1UI.htm。 DHTML 控件使用包含标准 HTML 标记和外部窗口调度命令的 HTML 资源，您可以使用文本编辑器进行编辑。

- **网络浏览器**Web 浏览器基于 HTML 资源中的 HTML 显示控件的 UI。 DHTML 控件中提供了指向`IWebBrowser2`Web 浏览器界面的指针，用于允许访问 DHTML 对象模型。

ATL 控制向导生成一个控件，其中包含 HTML 资源和 .cpp 文件中的默认代码。 您可以编译和运行向导生成的控件，然后在 Web 浏览器或 ActiveX 控件测试容器中查看控件。 下图显示了默认的 ATL DHTML 控件，测试容器中显示了三个按钮：

![ATL DHTML 控制](../atl/media/vc52en2.gif "ATL DHTML 控件")

请参阅[创建 ATL DHTML 控件](../atl/creating-an-atl-dhtml-control.md)以开始构建 DHTML 控件。 有关如何访问测试容器的信息，请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)。

## <a name="see-also"></a>另请参阅

[支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)
