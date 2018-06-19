---
title: 确定 DHTML 控件项目元素 |Microsoft 文档
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
ms.openlocfilehash: 525ad4e073607064234641f6544a11901ded0096
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357677"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>确定 DHTML 控件项目的元素
大多数 DHTML 控件代码完全这样会为任何 ATL 控件创建。 泛型代码的一个基本的了解，工作通过[ATL 教程](../atl/active-template-library-atl-tutorial.md)，并阅读部分[创建 ATL 项目](../atl/reference/creating-an-atl-project.md)和[ATL COM 对象的基础知识](../atl/fundamentals-of-atl-com-objects.md)。  
  
 DHTML 控件是类似于任何 ATL 控件，除外：  
  
-   除了控件实现的正则接口，它可实现其他接口用于 c + + 代码与 HTML 用户界面 (UI) 之间进行通信。 HTML UI 调用到 c + + 代码中使用此接口。  
  
-   它将创建 UI 控件的 HTML 资源。  
  
-   它允许通过成员变量的 DHTML 对象模型访问`m_spBrowser`，这是类型的智能指针[IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)。 使用此指针来访问 DHTML 对象模型的任何部分。  
  
 下图阐释了 DLL、 DHTML 控件，Web 浏览器中和 HTML 资源之间的关系。  
  
 ![DHTML 控件项目的元素](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  在此图的名称为占位符。 你的 HTML 资源以及对控件公开的接口的名称基于你将它们分配在 ATL 控件向导的名称。  
  
 在该图中的元素为：  
  
-   **我 DLL**使用 ATL 项目向导创建的 DLL。  
  
-   **DHTML 控件**(`m_spBrowser`) DHTML 控件，使用 ATL 对象向导创建。 此控件通过 Web 浏览器对象的接口访问的 Web 浏览器对象和其方法**IWebBrowser2**。 该控件本身公开以下两个接口，除了所需的控件的其他标准接口。  
  
    -   **IDHCTL1**由以仅供容器控件公开的接口。  
  
    -   **IDHCTLUI1** c + + 代码和 HTML 用户界面之间进行通信的调度接口。 Web 浏览器使用控件的调度接口来显示控件。 可从控件的用户界面中调用此调度接口的各种方法通过调用`window.external`后, 跟你想要调用此调度接口上的方法名称。 将访问`window.external`从脚本中构成此控件的 UI 的 HTML 标记。 有关调用外部方法中的资源文件的详细信息，请参阅[调用 DHTML 的 c + + 代码](../atl/calling-cpp-code-from-dhtml.md)。  
  
-   **IDR_CTL1** HTML 资源的资源 ID。 其文件名，在这种情况下，为 DHCTL1UI.htm。 DHTML 控件使用 HTML 资源，其中包含标准的 HTML 标记和外部窗口调度命令，可以使用文本编辑器进行编辑。  
  
-   **Web 浏览器**Web 浏览器将显示控件的 UI 中，基于 HTML 资源中的 HTML。 为 Web 浏览器的指针**IWebBrowser2**接口是 DHTML 控件以允许访问 DHTML 对象模型中提供。  
  
 ATL 控件向导生成的 HTML 资源和.cpp 文件中的默认代码具有的控件。 你可以编译和运行向导，生成的控件，然后查看 Web 浏览器或 ActiveX 控件测试容器中的控件。 下图显示默认 ATL DHTML 控件与显示在测试容器中的三个按钮：  
  
 ![ATL DHTML 控件](../atl/media/vc52en2.gif "vc52en2")  
  
 请参阅[创建 ATL DHTML 控件](../atl/creating-an-atl-dhtml-control.md)若要开始构建 DHTML 控件。 请参阅[使用测试容器测试属性和事件](../mfc/testing-properties-and-events-with-test-container.md)有关如何访问测试容器的信息。  
  
## <a name="see-also"></a>请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)

