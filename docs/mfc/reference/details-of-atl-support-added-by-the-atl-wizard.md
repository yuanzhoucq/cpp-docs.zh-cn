---
title: "ATL 向导添加 ATL 支持的详细信息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.atl.support
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17d5063db9eb76e0fc6db9eecfe183b63276b874
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 向导添加的 ATL 支持的详细信息
当你[向现有 MFC 可执行文件或 DLL 中添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)，Visual c + + 进行以下修改现有的 MFC 项目 (在此示例中，项目称为`MFCEXE`):  
  
-   添加两个新文件 （.idl 文件和.rgs 文件中，以用于注册服务器）。  
  
-   在主应用程序标头和实现文件 （Mfcexe.h 和 Mfcexe.cpp），新类 (派生自**CAtlMFCModule**) 添加。 除了新的类中，代码添加到`InitInstance`进行注册。 此外将代码添加到`ExitInstance`吊销类对象的函数。 在标头文件中，最后，两个新标头文件 （Initguid.h 和 Mfcexe_i.c） 包含在实现文件中，声明并初始化新的 Guid **CAtlMFCModule**-派生类。  
  
-   若要正确注册服务器，将新的.rgs file 的条目添加到项目的资源文件。  
  
## <a name="notes-for-dll-projects"></a>DLL 项目的说明  
 ATL 支持添加到 MFC DLL 项目时，你将看到一些差异。 代码添加到**dllregisterserver 的调用**和**DLLUnregisterServer**用于注册和注销该 DLL 的函数。 此外将代码添加到[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)和[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 项目中的 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [添加类](../../ide/adding-a-class-visual-cpp.md)   
 [添加成员函数](../../ide/adding-a-member-function-visual-cpp.md)   
 [添加成员变量](../../ide/adding-a-member-variable-visual-cpp.md)   
 [重写虚函数](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 消息处理程序](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [导航类结构](../../ide/navigating-the-class-structure-visual-cpp.md)
