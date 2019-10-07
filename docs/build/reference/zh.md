---
title: /ZH （调试信息中用于计算文件校验和的哈希算法）
description: 使用/ZH 编译器选项在调试信息中启用 MD5、SHA-1 或 256 SHA-1 源文件校验和
ms.date: 09/16/2019
f1_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
helpviewer_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
- /ZH compiler option
- /ZH:MD5 compiler option
- /ZH:SHA1 compiler option
- /ZH:SHA_256 compiler option
- Hash algorithm for file checksum in debug info
ms.openlocfilehash: f05dc2bc3b8ce4502ff16a6e19fdbb10763b34ba
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686934"
---
# <a name="zh-hash-algorithm-for-calculation-of-file-checksum-in-debug-info"></a>/ZH （调试信息中用于计算文件校验和的哈希算法）

指定要使用哪个加密哈希算法生成每个源文件的校验和。

## <a name="syntax"></a>语法

> **/ZH：** {**MD5**|**SHA1**|**SHA_256**}

## <a name="arguments"></a>参数

**/ZH： MD5**\
为校验和使用 MD5 哈希。 此选项是默认选项。

**/ZH： SHA1**\
对校验和使用 SHA-1 哈希。

**/ZH： SHA_256**\
对校验和使用 SHA-256 哈希。

## <a name="remarks"></a>备注

PDB 文件存储编译到关联的可执行文件中的对象代码中的每个源文件的校验和。 校验和允许调试器验证加载的源代码是否与可执行文件匹配。 编译器和调试器支持 MD5、SHA-1 和 256 SHA-1 哈希算法。 默认情况下，编译器使用 MD5 哈希生成校验和。 可以使用 **/ZH： MD5**选项显式指定此选项。

由于 MD5 和 SHA-1 中出现冲突的风险，Microsoft 建议使用 **/ZH： SHA_256**选项。 SHA-256 哈希可能会导致编译时间增加。

如果指定了多个 **/ZH**选项，则使用最后一个选项。

从 Visual Studio 2019 版本16.4 开始，可以使用 **/ZH**选项。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 将**配置**下拉箭头设置为 "**所有配置**"。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 修改 "**附加选项**" 属性以添加 **/ZH： MD5**、 **/ZH： SHA1**或 **/ZH： SHA_256**选项，然后选择 **"确定"** 。

## <a name="see-also"></a>请参阅

[编译器选项](compiler-options.md)\
[源服务器](/windows/win32/debug/source-server-and-source-indexing)
