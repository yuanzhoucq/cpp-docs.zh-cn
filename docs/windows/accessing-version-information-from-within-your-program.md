---
title: 内访问版本信息从你的程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79520523ebeda2cb0260d1bc79d0b6b35d33aa23
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646954"
---
# <a name="accessing-version-information-from-within-your-program"></a>从程序内访问版本信息
### <a name="to-access-version-information-from-within-your-program"></a>在程序内访问版本信息  
  
如果想要在程序内访问版本信息，请使用 [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) 函数和 [VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) 函数。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求
 Win32  
  
## <a name="see-also"></a>请参阅  
 [版本信息编辑器](../windows/version-information-editor.md)   
 [版本信息 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)