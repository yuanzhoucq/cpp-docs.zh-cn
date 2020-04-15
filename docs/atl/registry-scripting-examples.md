---
title: 注册表脚本示例
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 7bcdb7076982e2f0bd08f4fd82bb45f21e61ef20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329328"
---
# <a name="registry-scripting-examples"></a>注册表脚本示例

本主题中的脚本示例演示如何向系统注册表添加密钥、注册注册商 COM 服务器以及指定多个解析树。

## <a name="add-a-key-to-hkey_current_user"></a>添加密钥以HKEY_CURRENT_USER

以下分析树说明了向系统注册表添加单个密钥的简单脚本。 特别是，脚本将键`MyVeryOwnKey`添加到`HKEY_CURRENT_USER`。 它还将 的`HowGoesIt`默认字符串值分配给新键：

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

此脚本可以轻松扩展以定义多个子键，如下所示：

```
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

现在，脚本将子键`HasASubkey`添加到`MyVeryOwnKey`。 到此子键，它同时`PrettyCool`添加子键（默认值`DWORD`为 55）和`ANameValue`命名值（字符串值为`WithANamedValue`）。

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>注册注册商 COM 服务器

以下脚本注册注册商 COM 服务器本身。

```
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

在运行时，此解析树将`ATL.Registrar`键添加到`HKEY_CLASSES_ROOT`。 到此新密钥，它然后：

- 指定`ATL Registrar Class`为键的默认字符串值。

- 添加`CLSID`为子键。

- 为`{44EC053A-400F-11D0-9DCD-00A0C90391D3}``CLSID`指定 。 （此值是注册器的 CLSID，用于`CoCreateInstance`.

由于`CLSID`是共享的，因此不应在取消注册模式下将其删除。 `NoRemove CLSID`语句 ， 通过指示`CLSID`应在注册模式下打开并在取消注册模式下忽略来这样做。

语句`ForceRemove`通过在重新创建密钥之前删除键及其所有子键来提供内务管理功能。 如果子键的名称已更改，这非常有用。 在此脚本示例中，`ForceRemove`检查是否存在。 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 如果是， `ForceRemove`

- 递归删除`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`及其所有子键。

- 重新创建`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

- 添加`ATL Registrar Class`为 的默认字符串值`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。

解析树现在向`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`中添加了两个新的子键。 第一个键`ProgID`获取默认字符串值，该值是 ProgID。 第二个键`InprocServer32`获取默认字符串值`%MODULE%`，这是本文"[使用可替换参数（注册器的预处理器"）](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)部分中解释的预处理器值。 `InprocServer32`还获取命名值 ，`ThreadingModel`字符串值 为`Apartment`。

## <a name="specify-multiple-parse-trees"></a>指定多个分析树

要在脚本中指定多个解析树，只需将一个树放在另一个树的末尾即可。 例如，以下脚本将键`MyVeryOwnKey`、 添加到 和`HKEY_CLASSES_ROOT``HKEY_CURRENT_USER`的解析树中：

```
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> 在注册器脚本中，4K 是最大令牌大小。 （令牌是语法中的任何可识别元素。在前面的脚本`HKCR`示例中，`HKEY_CURRENT_USER`和`'MyVeryOwnKey'``'HowGoesIt'`都是令牌。

## <a name="see-also"></a>另请参阅

[Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
