---
title: "字符串编辑器 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.string.F1
dev_langs:
- C++
helpviewer_keywords:
- String editor
- string tables
- string tables, String editor
- string editing
- string editing, string tables
- resource editors, String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f0d0f368ec82e46a72977b574b1632bf1d9d6d84
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="string-editor"></a>字符串编辑器
字符串表是 Windows 资源，其中包含应用程序的所有字符串的 ID、值和标题的列表。 例如，状态栏提示位于字符串表中。  
  
 开发应用程序时，可以具有多个字符串表 — 每种语言或条件使用一个。 但是，可执行模块只有一个字符串表。 如果将表放入不同 DLL 中，则正在运行的应用程序可以引用多个字符串表。  
  
 通过字符串表可以更加轻松地将应用程序本地化为不同语言。 如果所有字符串都处于字符串表中，则可以通过翻译字符串（和其他资源）来本地化应用程序，而无需更改源代码。 这通常比在源文件中手动查找和替换各种字符串更加理想。  
  
 使用字符串编辑器可以：  
  
-   [搜索一个或多个字符串](../windows/finding-a-string.md)。  
  
-   快速向字符串表中 [插入新条目](../windows/adding-or-deleting-a-string.md) 。  
  
-   [在资源文件之间移动字符串](../windows/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [对 ID、值和标题属性使用就地编辑](../windows/changing-the-properties-of-a-string.md) 并立即查看更改。  
  
-   [更改多个字符串的标题属性](../windows/changing-the-caption-property-of-multiple-strings.md)  
  
-   [为字符串添加格式设置或特殊字符](../windows/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows 不允许创建空字符串表。 如果创建的字符串表中没有任何条目，则它在保存资源文件时会自动删除。  
  
 有关将资源添加到托管项目 （那些针对公共语言运行时） 的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅 [演练：本地化 Windows 窗体](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) 和 [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6)。  
  
## <a name="requirements"></a>惠?  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [资源编辑器](../windows/resource-editors.md)   
 [字符串](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [有关字符串](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)

