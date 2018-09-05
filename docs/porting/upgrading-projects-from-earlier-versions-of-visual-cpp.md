---
title: 从 Visual C++ 早期版本升级项目 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 32-bit code porting
- upgrading Visual C++ applications, 32-bit code
ms.assetid: 18cdacaa-4742-43db-9e4c-2d9e73d8cc84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed8a8ab088f3fbb10b5f477d125dbf3f2a7ac932
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "42578293"
---
# <a name="upgrading-projects-from-earlier-versions-of-visual-c"></a>从 Visual C++ 早期版本升级项目
在大多数情况下，你可以打开在 Visual Studio 早期版本中创建的项目。 但是，为实现这一点，Visual Studio 将升级项目。 如果你保存升级的该项目，它将无法在早期版本中打开。  
  
> [!IMPORTANT]
> 如果你尝试转换已转换的项目，Visual Studio 会要求确认，因为重新转换会删除现有文件。  
  
许多升级后的项目和解决方案无需修改即可成功生成。 但是，某些项目可能需要更改设置和/或源代码。 我们建议你采用以下指导方针先解决设置问题，如果项目仍未生成，然后再解决代码问题。 有关详细信息，请参阅[潜在的升级问题概述](../porting/overview-of-potential-upgrade-issues-visual-cpp.md)。  
  
1. 复制现有项目和解决方案文件。 并行安装 Visual Studio 当前版本和早期版本，以便比较文件的版本（如果需要）。  
  
2. 在 Visual Studio 的当前版本中，打开（并因此升级）项目或解决方案的副本并保存。  
  
3. 对于每个转换的项目，打开快捷菜单并选择 **“属性”**。 在 **“配置属性”** 下，选择 **“常规”** ，然后为 **“平台工具集”** 选择当前版本。 （例如，为 Visual Studio 2017 选择 v141。）  
  
4. 生成解决方案。 如果生成失败，请修改设置并重新生成。  
  
数据源包含在单独的数据库项目中，以便你更轻松地在这些源中修改和调试存储过程。 如果你升级包含数据源的 C++ 项目，则会自动创建单独的数据库项目。  
  
有关如何更新目标 Windows 版本的信息，请参阅[修改 WINVER 和 _WIN32_WINNT](../porting/modifying-winver-and-win32-winnt.md)。  
  
## <a name="see-also"></a>请参阅  

[生成系统更改](../build/build-system-changes.md)  
[Visual Studio 2017 中 Visual C++ 的新增功能](../what-s-new-for-visual-cpp-in-visual-studio.md) 
[Visual C++ 更改历史记录（2003 - 2015）](../porting/visual-cpp-change-history-2003-2015.md)   
[非标准行为](../cpp/nonstandard-behavior.md)