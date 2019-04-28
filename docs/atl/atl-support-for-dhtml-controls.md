---
title: ATL 支持 DHTML 控件
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: dd8ac616d127c3307c1c432c0b3c9bc2ef1d6181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223285"
---
# <a name="atl-support-for-dhtml-controls"></a>ATL 支持 DHTML 控件

使用 ATL，你可以使用动态 HTML (DHTML) 功能创建一个控件。 ATL DHTML 控件：

- 承载 WebBrowser 控件。

- 指定使用 HTML、 DHTML 控件的用户界面 (UI)。

- 通过其界面，可访问的 web 浏览器对象和其方法[IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\))。

- 管理之间的通信C++代码和 HTML。

DHTML 控件非常到任何其他 ATL 控件相似，但 DHTML 控件包含其他调度接口。 请参阅中的图形[标识 DHTML 控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)有关默认 DHTML 项目中提供的接口的说明。

在 Web 浏览器或其他容器，如 ActiveX 控件测试容器，可以查看 ATL DHTML 控件。

## <a name="in-this-section"></a>本节内容

[标识 DHTML 控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
介绍 DHTML 控件项目的元素。

[从 DHTML 调用 C++ 代码](../atl/calling-cpp-code-from-dhtml.md)<br/>
提供了一个示例调用C++DHTML 控件中的代码。

[创建 ATL DHTML 控件](../atl/creating-an-atl-dhtml-control.md)<br/>
列出了用于创建 DHTML 控件的步骤。

[测试 ATL DHTML 控件](../atl/testing-the-atl-dhtml-control.md)<br/>
演示如何生成和测试初始 DHTML 控件项目。

[ ATL DHTML 控件](../atl/modifying-the-atl-dhtml-control.md)<br/>
演示如何向控件添加某种功能。

[测试更改后的 ATL DHTML 控件](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
演示如何生成和测试控件的附加的功能。

## <a name="related-sections"></a>相关章节

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。
