---
title: ATL 支持 DHTML 控件 |Microsoft 文档
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
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f57fc841ba2eb3473ccb866df7333ebd24583d40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="atl-support-for-dhtml-controls"></a>ATL 支持 DHTML 控件
使用 ATL，可以在动态 HTML (DHTML) 功能中创建的控件。 ATL DHTML 控件：  
  
-   WebBrowser 控件托管。  
  
-   指定，使用 HTML，DHTML 控件的用户界面 (UI)。  
  
-   通过其接口访问的 web 浏览器对象和其方法[IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx)。  
  
-   管理 c + + 代码与 HTML 之间的通信。  
  
 DHTML 控件非常相似到任何其他 ATL 控件，但 DHTML 控件包括其他的调度接口。 请参阅中的图形[确定 DHTML 控件项目元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)有关在默认 DHTML 项目中提供的接口的图例。  
  
 你可以在 Web 浏览器或其他容器，例如 ActiveX 控件测试容器中查看 ATL DHTML 控件。  
  
## <a name="in-this-section"></a>本节内容  
 [标识 DHTML 控件项目的元素](../atl/identifying-the-elements-of-the-dhtml-control-project.md)  
 描述 DHTML 控件项目的元素。  
  
 [从 DHTML 调用 C++ 代码](../atl/calling-cpp-code-from-dhtml.md)  
 提供从 DHTML 控件调用 c + + 代码的示例。  
  
 [创建 ATL DHTML 控件](../atl/creating-an-atl-dhtml-control.md)  
 列出创建 DHTML 控件的步骤。  
  
 [测试 ATL DHTML 控件](../atl/testing-the-atl-dhtml-control.md)  
 演示如何生成和测试初始 DHTML 控件项目。  
  
 [ ATL DHTML 控件](../atl/modifying-the-atl-dhtml-control.md)  
 演示如何将某些功能添加到控件。  
  
 [测试更改的 ATL DHTML 控件](../atl/testing-the-modified-atl-dhtml-control.md)  
 演示如何生成并测试控件的新增的功能。  
  
## <a name="related-sections"></a>相关章节  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 提供了关于如何使用 Active Template Library 进行编程的概念性主题的链接。

