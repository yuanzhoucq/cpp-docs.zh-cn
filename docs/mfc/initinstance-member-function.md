---
title: InitInstance 成员函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bda38c7173feeccf878ee7befc3d27c0061ddb1e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="initinstance-member-function"></a>InitInstance 成员函数
Windows 操作系统允许您运行同一应用程序的多个副本（也称为“实例”）。 `WinMain` 调用[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)每次启动应用程序的新实例。  
  
 MFC 应用程序向导创建的标准 `InitInstance` 实现将执行以下任务：  
  
-   作为其中心操作，将创建文档模板，该模板又会创建文档、视图和框架窗口。 有关此过程的说明，请参阅[文档模板创建](../mfc/document-template-creation.md)。  
  
-   从 .ini 文件或 Windows 注册表加载标准文件选项，包括最近使用的文件的名称。  
  
-   注册一个或多个文档模板。  
  
-   对于 MDI 应用程序，创建主框架窗口。  
  
-   处理命令行以打开命令行上指定的文档或打开新的空文档。  
  
 您可以添加自己的初始化代码或修改向导编写的代码。  
  
> [!NOTE]
>  MFC 应用程序必须初始化为单线程单元 (STA)。 如果调用[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)中你`InitInstance`重写时，请指定`COINIT_APARTMENTTHREADED`(而非`COINIT_MULTITHREADED`)。 有关详细信息，请参阅 PRB: MFC 应用程序停止响应时初始化为多线程单元 （828643） 在应用程序[ http://support.microsoft.com/default.aspxscid=kb; en-我们; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
