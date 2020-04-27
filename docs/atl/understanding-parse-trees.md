---
title: ATL 注册器和分析树
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: de2cea9b0e7b7c62236f708f9aa8217eaa5df51d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168691"
---
# <a name="understanding-parse-trees"></a>了解分析树

你可以在注册器脚本中定义一个或多个分析树，其中每个分析树具有以下形式：

> \<根密钥> {\<注册表表达式>} +

其中：

> \<根密钥>：： = HKEY_CLASSES_ROOT |HKEY_CURRENT_USER | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_LOCAL_MACHINE |HKEY_USERS | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_PERFORMANCE_DATA |HKEY_DYN_DATA | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_CURRENT_CONFIG |HKCR |HKCU | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKLM |HKU 开头 |HKPD |HKDD |HKCC

> \<注册表表达式>：： = \<Add Key> |\<删除密钥>

> \<Add key>：： = [**ForceRemove** | **NoRemove** | **val**]\<key Name> [\<键值>] [{\<Add Key>}]

> \<删除密钥>：： =**删除**\<密钥名称>

> \<项名称>：： = **'**\<字母数字>+**'**

> \<字母数字>：： =*任意字符 NOT NULL，即 ASCII 0*

> \<键值>：： = \<键类型>\<密钥名称>

> \<键类型>：： = **s** | **d**

> \<键值>：： = **'**\<字母数字>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT`和`HKCR`等效;`HKEY_CURRENT_USER`和`HKCU`等效;依此类推。

分析树可以将多个密钥和子项添加到\<> 的根密钥。 在此过程中，它会使子项的句柄处于打开状态，直到分析器完成分析其所有子项。 此方法比每次对一个键进行操作更高效，如以下示例中所示：

```rgs
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

此时，注册机构最初会打开（创建`HKEY_CLASSES_ROOT\MyVeryOwnKey`）。 然后， `MyVeryOwnKey`它会发现具有子项。 注册器会保留句柄`MyVeryOwnKey`，并使用此父句柄打开（创建） `HasASubKey` ，而不是将键关闭。 （如果没有打开的父句柄，系统注册表会变慢。）因此，作为`HKEY_CLASSES_ROOT\MyVeryOwnKey`父代打开`HasASubKey`和`MyVeryOwnKey`打开的速度比打开`MyVeryOwnKey`、关闭`MyVeryOwnKey`和打开`MyVeryOwnKey\HasASubKey`的速度更快。

## <a name="see-also"></a>另请参阅

[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
