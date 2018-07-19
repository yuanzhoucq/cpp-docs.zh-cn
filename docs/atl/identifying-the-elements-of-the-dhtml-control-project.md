---
title: 标识 DHTML 控件项目的元素 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f415d9b52179d83617cefe94d4f4525d3cf9808e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852427"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>标识 DHTML 控件项目的元素
大多数 DHTML 控件代码完全类似的创建的任何 ATL 控件。 基本了解泛型代码，通过工作[ATL 教程](../atl/active-template-library-atl-tutorial.md)，并阅读部分[创建 ATL 项目](../atl/reference/creating-an-atl-project.md)并[ATL COM 对象的基础知识](../atl/fundamentals-of-atl-com-objects.md)。  
  
 DHTML 控件是类似于任何 ATL 控件除外：  
  
-   除了常见的接口，控件实现，它实现了使用 c + + 代码和 HTML 用户界面 (UI) 之间进行通信的其他接口。 HTML UI 会调入 c + + 代码使用此接口。  
  
-   它创建 UI 控件的 HTML 资源。  
  
-   它允许访问 DHTML 对象模型通过成员变量`m_spBrowser`，这是类型的智能指针[IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)。 使用此指针访问 DHTML 对象模型的任何部分。  
  
 下图说明了您的 DLL、 DHTML 控件、 Web 浏览器和 HTML 资源之间的关系。  
  
 ![DHTML 控件项目的元素](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  上图的名称是占位符。 HTML 资源和您的控件上公开的接口的名称基于 ATL 控件向导中将其分配的名称。  
  
 在此图中，这些元素为：  
  
-   **我的 DLL**使用 ATL 项目向导创建的 DLL。  
  
-   **DHTML 控件**(`m_spBrowser`) DHTML 控件，使用 ATL 对象向导创建。 此控件通过 Web 浏览器对象的接口访问的 Web 浏览器对象和其方法`IWebBrowser2`。 在控件自身公开以下两个接口，除了控制所需的其他标准接口。  
  
    -   `IDHCTL1` 仅供容器使用的控件所公开的接口。  
  
    -   `IDHCTLUI1` 用于 c + + 代码和 HTML 用户界面之间进行通信的调度接口。 Web 浏览器使用控件的调度接口来显示该控件。 可以从控件的用户界面中调用此调度接口的各种方法通过调用`window.external`后, 跟上你想要调用此调度接口的方法名称。 将访问`window.external`从构成此控件的 UI 的 HTML 内的脚本标记。 有关调用外部方法中的资源文件的详细信息，请参阅[从 DHTML 调用 c + + 代码](../atl/calling-cpp-code-from-dhtml.md)。  
  
-   **IDR_CTL1** HTML 资源的资源 ID。 其文件名，在这种情况下，为 DHCTL1UI.htm。 DHTML 控件使用 HTML 资源，其中包含标准的 HTML 标记和外部窗口调度命令，可以使用文本编辑器进行编辑。  
  
-   **Web 浏览器**Web 浏览器将显示控件的 UI 中，基于 HTML 资源中的 HTML。 一个指向 Web 浏览器的`IWebBrowser2`接口是 DHTML 控件能够访问 DHTML 对象模型中提供。  
  
 ATL 控件向导生成的 HTML 资源和.cpp 文件中，默认代码的控件。 可以编译和运行向导，生成的控件，然后在 Web 浏览器或 ActiveX 控件测试容器中查看该控件。 下图显示了三个按钮显示在测试容器的默认 ATL DHTML 控件：  
  
 ![ATL DHTML 控件](../atl/media/vc52en2.gif "vc52en2")  
  
 请参阅[创建 ATL DHTML 控件](../atl/creating-an-atl-dhtml-control.md)若要开始构建 DHTML 控件。 请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)有关如何访问测试容器的信息。  
  
## <a name="see-also"></a>请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)

