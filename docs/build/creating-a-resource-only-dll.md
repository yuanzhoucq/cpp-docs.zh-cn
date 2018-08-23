---
title: 创建纯资源 DLL |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5249f4528038771162bb96b714524ed751ff39a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367542"
---
# <a name="creating-a-resource-only-dll"></a>创建纯资源 DLL  
  
纯资源 DLL 是一个 DLL，它包含任何内容但资源，如图标、 位图、 字符串和对话框。 使用纯资源 DLL 是共享相同一组在多个程序中的资源的一种好方法。 还有一种好方法，以提供针对多个语言进行本地化的资源的应用程序 (请参阅[MFC 应用程序中的本地化资源： 附属 Dll](../build/localized-resources-in-mfc-applications-satellite-dlls.md))。  
  
若要创建纯资源 DLL，你创建新的 Win32 DLL (非 MFC) 项目，并将你的资源添加到项目。  
  
-   选择在 Win32 项目**新项目**对话框框中，并在 Win32 项目向导中指定的 DLL 项目类型。  
  
-   为 DLL 创建一个包含的资源 （例如字符串或菜单） 的新资源脚本并保存.rc 文件。  
  
-   上**项目**菜单上，单击**添加现有项**，然后在项目中插入新的.rc 文件。  
  
-   指定[/NOENTRY](../build/reference/noentry-no-entry-point.md)链接器选项。 /NOENTRY 防止链接器链接到的引用`_main`到 DLL; 需要此选项来创建纯资源 DLL。  
  
-   生成 DLL。  
  
使用纯资源 DLL 的应用程序应调用[LoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)显式链接到 DLL。 若要访问的资源，调用泛型函数`FindResource`和`LoadResource`，这适用于任何类型的资源，或调用以下特定于资源的函数之一：  
  
-   `FormatMessage`  
  
-   `LoadAccelerators`  
  
-   `LoadBitmap`  
  
-   `LoadCursor`  
  
-   `LoadIcon`  
  
-   `LoadMenu`  
  
-   `LoadString`  
  
应用程序应调用`FreeLibrary`完成时使用的资源。  
  
## <a name="see-also"></a>请参阅  
  
[使用资源文件](../windows/working-with-resource-files.md)  
[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)