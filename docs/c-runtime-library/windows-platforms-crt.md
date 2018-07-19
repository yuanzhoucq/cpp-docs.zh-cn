---
title: Windows 平台 (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility [C++], C run-time libraries
- compatibility [C++], C run-time libraries
- MBCS [C++], Win32 platforms
- operating systems [C++]
- Unicode [C++], Win32 platforms
ms.assetid: 0aacaf45-6dc4-4908-bd52-57abac7b39f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d53e8020bbb7649d78232025ef9c63c1dc868fee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409002"
---
# <a name="windows-platforms-crt"></a>Windows 平台 (CRT)

用于 Visual Studio 的 C 运行时库支持当前版本的 Windows 和 Windows Server、[!INCLUDE[win8](../build/reference/includes/win8_md.md)]、[!INCLUDE[winserver8](../build/reference/includes/winserver8_md.md)]、[!INCLUDE[win7](../build/includes/win7_md.md)]、[!INCLUDE[winsvr08](../build/reference/includes/winsvr08_md.md)] 和 Windows Vista ，并选择性地支持适用于 x86 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3)、适用于 x64 的 [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) 和同时适用于 x86 和 x64 的 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2)。 所有这些操作系统都支持 Windows 桌面 API (Win32) 并提供 Unicode 支持。 此外，所有 Win32 应用程序都能使用多字节字符集 (MBCS)。

> [!NOTE]
> Visual Studio 2017 中的**使用 C++ 的桌面开发**工作负载的默认安装不包括 [!INCLUDE[winxp](../build/includes/winxp_md.md)] 支持和 [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] 开发。 必须安装可选组件**针对 C++ 的 Windows XP 支持**，用于启用 Windows XP 平台工具集。

## <a name="see-also"></a>请参阅

[兼容性](../c-runtime-library/compatibility.md)  
