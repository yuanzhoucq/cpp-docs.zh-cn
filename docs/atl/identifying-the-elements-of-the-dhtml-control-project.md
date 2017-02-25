---
title: "Identifying the Elements of the DHTML Control Project | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DHTML controls, ATL 支持"
  - "HTML 控件, ATL 支持"
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Identifying the Elements of the DHTML Control Project
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大多数DHTML控件代码是方式与为所有ATL控件创建的实例。  对泛型代码，工作的基本了解通过 [ATL教程](../atl/active-template-library-atl-tutorial.md)和读取部分 [创建ATL项目](../atl/reference/creating-an-atl-project.md) 和 [ATL COM对象的基本知识](../atl/fundamentals-of-atl-com-objects.md)。  
  
 DHTML控件类似于所有ATL控件，但:  
  
-   除了常规接口外控件实现，该实现用于通信在C\+\+代码和HTML用户界面\(UI\)之间的其他接口。  使用此接口，HTML用户界面对C\+\+代码。  
  
-   它创建控件用户界面的一个HTML资源。  
  
-   将成员变量的 `m_spBrowser`允许访问DHTML对象模型的访问，是类型 [IWebBrowser2](https://msdn.microsoft.com/en-us/library/aa752127.aspx)智能指针。  使用此指针访问DHTML对象模型中的任何部分。  
  
 下图说明您的DLL、DHTML控件、浏览器和HTML资源之间的关系。  
  
 ![DHTML 控件项目的元素](../atl/media/vc52en1.png "vc52EN1")  
  
> [!NOTE]
>  此图像的名称为占位符。  在控件中显示的HTML资源和接口的名称基于您在ATL控件向导分配其名称。  
  
 此图像，元素是:  
  
-   **My DLL** 使用ATL项目向导创建的DLL。  
  
-   **DHTML Control** \(`m_spBrowser`\) DHTML控件，创建使用ATL对象向导。  此控件访问浏览器对象及其方法通过浏览器对象的接口，**IWebBrowser2**。  控件显示下面的两个接口，以及对于控件所需的任何其他标准接口之外。  
  
    -   **IDHCTL1** 控件公开的接口仅使用由容器。  
  
    -   **IDHCTLUI1** 通信的调度接口在C\+\+代码和HTML用户界面之间。  浏览器使用控件的调度接口显示控件。  可以通过调用 `window.external`调用此调度接口各种方法从控件的用户界面的，后跟此计划接口的方法名称要调用。  您将从构造该控件的用户界面的一个脚本标记来访问 `window.external` 在HTML中。  有关调用在资源文件中的外部方法的更多信息，请参见 [调用从DHTML的C\+\+代码](../atl/calling-cpp-code-from-dhtml.md)。  
  
-   **IDR\_CTL1** HTML资源的ID。  其文件名，在这种情况下，为DHCTL1UI.htm。  DHTML控件使用文本编辑器，其中包含标准HTML标记，并外部窗口计划命令的一种HTML资源可以编辑。  
  
-   **Web Browser** 浏览器基于HTML资源的HTML中显示控件的用户界面。  给浏览器的 **IWebBrowser2** 接口的指针可在DHTML控件允许访问DHTML对象模型的访问。  
  
 ATL控件向导生成的默认代码的控件在HTML资源和.cpp文件。  可编译和运行该控件在生成的由向导，然后查看在或浏览器的控件或ActiveX控件测试容器。  下面的表中的图片并突出显示的三个按钮的默认ATL DHTML控件测试容器:  
  
 ![ATL DHTML 控件](../atl/media/vc52en2.png "vc52EN2")  
  
 请参见 [创建ATL DHTML控件](../atl/creating-an-atl-dhtml-control.md) 开始生成DHTML控件。  有关如何访问测试容器的信息，请参见 [测试属性和事件与测试容器](../mfc/testing-properties-and-events-with-test-container.md)。  
  
## 请参阅  
 [支持 DHTML 控件](../atl/atl-support-for-dhtml-controls.md)