---
title: 内访问版本信息从你的程序 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
ms.openlocfilehash: 028ea6126b75b914e7ff9a4ded2d08efa9d35b28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644621"
---
# <a name="accessing-version-information-from-within-your-program-c"></a>内访问版本信息从你的程序 （c + +）

### <a name="to-access-version-information-from-within-your-program"></a>在程序内访问版本信息

1. 如果想要在程序内访问版本信息，请使用 [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) 函数和 [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) 函数。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[版本信息编辑器](../windows/version-information-editor.md)<br/>
[版本信息 (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)