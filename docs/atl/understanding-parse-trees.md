---
title: ATL 注册器和分析树
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: e1aea573e78e6f6a9a86bc4e3987ee448815f329
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196163"
---
# <a name="understanding-parse-trees"></a>了解分析树

你可以定义一个或多个分析树中注册器脚本，其中每个分析树具有以下形式：

```
<root key>{<registry expression>}+
```

其中：

```
<root key> ::= HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |
    HKEY_LOCAL_MACHINE | HKEY_USERS |
    HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |
    HKEY_CURRENT_CONFIG | HKCR | HKCU |
    HKLM | HKU | HKPD | HKDD | HKCC
<registry expression> ::= <Add Key> | <Delete Key>
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name> [<Key Value>][{<Add Key>}]
<Delete Key> ::= Delete<Key Name>
<Key Name> ::= '<AlphaNumeric>+'
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0
<Key Value> ::== <Key Type><Key Name>
<Key Type> ::= s | d
<Key Value> ::= '<AlphaNumeric>'
```

> [!NOTE]
> `HKEY_CLASSES_ROOT` 和`HKCR`相等，则`HKEY_CURRENT_USER`和`HKCU`是等效的; 依此类推。

分析树可以添加多个项和子项到\<根密钥 >。 在执行此操作，它维护子项的句柄打开直到分析器完成分析所有子项。 这种方法是比一次对一个密钥操作更高效，如下面的示例中所示：

```
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

在这里，注册机构最初打开 （创建） `HKEY_CLASSES_ROOT\MyVeryOwnKey`。 然后可以看到，`MyVeryOwnKey`有一个子项。 而不是关闭的关键`MyVeryOwnKey`，注册机构会保留该句柄，并打开 （创建）`HasASubKey`使用此父句柄。 （系统注册表可能要慢时没有父句柄处于打开状态。）因此，打开`HKEY_CLASSES_ROOT\MyVeryOwnKey`，然后打开`HasASubKey`与`MyVeryOwnKey`快于打开父原样`MyVeryOwnKey`，正在关闭`MyVeryOwnKey`，然后打开`MyVeryOwnKey\HasASubKey`。

## <a name="see-also"></a>请参阅

[创建注册器脚本](../atl/creating-registrar-scripts.md)
