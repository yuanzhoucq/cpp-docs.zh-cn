---
title: CRegKey 类
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: 3faf446f74577034a3d0676b90ebe7027ef6da06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496540"
---
# <a name="cregkey-class"></a>CRegKey 类

此类提供用于操作系统注册表中的项的方法。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CRegKey
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRegKey::CRegKey](#cregkey)|构造函数。|
|[CRegKey:: ~ CRegKey](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRegKey::Attach](#attach)|调用此方法, 通过将[m_hKey](#m_hkey)成员句`CRegKey`柄设置为`hKey`来将 HKEY 附加到对象。|
|[CRegKey:: Close](#close)|调用此方法可释放[m_hKey](#m_hkey)成员句柄并将其设置为 NULL。|
|[CRegKey::Create](#create)|调用此方法以创建指定的密钥 (如果它不作为的子项`hKeyParent`存在)。|
|[CRegKey::DeleteSubKey](#deletesubkey)|调用此方法以从注册表中移除指定的键。|
|[CRegKey::DeleteValue](#deletevalue)|调用此方法可从[m_hKey](#m_hkey)中删除值字段。|
|[CRegKey::Detach](#detach)|调用此方法可将[m_hKey](#m_hkey)成员句柄与`CRegKey`对象分离, 并将设置`m_hKey`为 NULL。|
|[CRegKey::EnumKey](#enumkey)|调用此方法以枚举打开的注册表项的子项。|
|[CRegKey:: Flush](#flush)|调用此方法将打开的注册表项的所有属性写入注册表。|
|[CRegKey::GetKeySecurity](#getkeysecurity)|调用此方法以检索保护打开的注册表项的安全描述符的副本。|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|此方法通知调用方对打开的注册表项的属性或内容所做的更改。|
|[CRegKey::Open](#open)|调用此方法以打开指定的密钥, 并将[m_hKey](#m_hkey)设置为此密钥的句柄。|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|调用此方法可以检索指定的值名称的二进制数据。|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|调用此方法可以检索指定的值名称的 DWORD 数据。|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|调用此方法可以检索指定的值名称的 GUID 数据。|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|调用此方法可以检索指定的值名称的多字符串数据。|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|调用此方法可以检索指定值名称的 QWORD 数据。|
|[CRegKey::QueryStringValue](#querystringvalue)|调用此方法可以检索指定的值名称的字符串数据。|
|[CRegKey::QueryValue](#queryvalue)|调用此方法来检索[m_hKey](#m_hkey)的指定值字段的数据。 此方法的早期版本不再受支持, 并且已标记为 ATL_DEPRECATED。|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|调用此方法以从注册表中删除指定的键, 并显式删除所有子项。|
|[CRegKey::SetBinaryValue](#setbinaryvalue)|调用此方法可设置注册表项的二进制值。|
|[CRegKey::SetDWORDValue](#setdwordvalue)|调用此方法可设置注册表项的 DWORD 值。|
|[CRegKey::SetGUIDValue](#setguidvalue)|调用此方法可设置注册表项的 GUID 值。|
|[CRegKey::SetKeySecurity](#setkeysecurity)|调用此方法可设置注册表项的安全性。|
|[CRegKey::SetKeyValue](#setkeyvalue)|调用此方法可将数据存储在指定键的指定值字段中。|
|[CRegKey::SetMultiStringValue](#setmultistringvalue)|调用此方法可设置注册表项的多字符串值。|
|[CRegKey::SetQWORDValue](#setqwordvalue)|调用此方法可设置注册表项的 QWORD 值。|
|[CRegKey::SetStringValue](#setstringvalue)|调用此方法可设置注册表项的字符串值。|
|[CRegKey::SetValue](#setvalue)|调用此方法可将数据存储在[m_hKey](#m_hkey)的指定值字段中。 此方法的早期版本不再受支持, 并且已标记为 ATL_DEPRECATED。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CRegKey:: operator HKEY](#operator_hkey)|`CRegKey`将对象转换为 HKEY。|
|[CRegKey:: operator =](#operator_eq)|赋值运算符。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|包含与`CRegKey`对象关联的注册表项的句柄。|
|[CRegKey::m_pTM](#m_ptm)|指向对象`CAtlTransactionManager`的指针|

## <a name="remarks"></a>备注

`CRegKey`提供用于创建和删除系统注册表中的键和值的方法。 注册表包含系统组件的特定于安装的一组定义, 如软件版本号、已安装硬件的逻辑到物理映射以及 COM 对象。

`CRegKey`为给定计算机的系统注册表提供编程接口。 例如, 若要打开特定的注册表项, 请`CRegKey::Open`调用。 若要检索或修改数据值, 请`CRegKey::QueryValue`分别`CRegKey::SetValue`调用或。 若要关闭某个键, `CRegKey::Close`请调用。

关闭某个键后, 其注册表数据会写入 (刷新) 到硬盘。 此过程可能需要几秒钟的时间。 如果你的应用程序必须将注册表数据显式写入硬盘, 则可以调用[RegFlushKey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32 函数。 但是, `RegFlushKey`使用多个系统资源, 只应在绝对必要时进行调用。

> [!IMPORTANT]
>  允许调用方指定注册表位置的任何方法都有可能读取不受信任的数据。 使用[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)的方法应考虑此函数不显式处理 NULL 终止的字符串。 调用代码应检查两个条件。

## <a name="requirements"></a>要求

**标头:** atlbase.h

##  <a name="attach"></a>CRegKey:: Attach

调用此方法, 通过将[m_hKey](#m_hkey)成员句`CRegKey`柄设置为*HKEY*, 将 HKEY 附加到对象。

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>参数

*hKey*<br/>
注册表项的句柄。

### <a name="remarks"></a>备注

`Attach`如果`m_hKey`为非 NULL, 将断言。

##  <a name="close"></a>CRegKey:: Close

调用此方法可释放[m_hKey](#m_hkey)成员句柄并将其设置为 NULL。

```
LONG Close() throw();
```

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS;否则, 将返回错误值。

##  <a name="create"></a>CRegKey:: Create

调用此方法以创建指定的密钥 (如果它不作为*hKeyParent*的子项存在)。

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>参数

*hKeyParent*<br/>
打开键的句柄。

*lpszKeyName*<br/>
指定要创建或打开的项的名称。 此名称必须是*hKeyParent*的子项。

*lpszClass*<br/>
指定要创建或打开的键的类。 默认值为 REG_NONE。

*dwOptions*<br/>
用于密钥的选项。 默认值为 REG_OPTION_NON_VOLATILE。 有关可能的值和说明的列表, 请参阅 Windows SDK 中的[RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) 。

*samDesired*<br/>
密钥的安全访问权限。 默认值为 KEY_READ &#124; KEY_WRITE。 有关可能的值和说明的列表, 请`RegCreateKeyEx`参阅。

*lpSecAttr*<br/>
指向[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))结构的指针, 该结构指示键的句柄是否可以由子进程继承。 默认情况下, 此参数为 NULL (表示无法继承句柄)。

*lpdwDisposition*<br/>
弄如果非 NULL, 则检索 REG_CREATED_NEW_KEY (如果键不存在并且已创建) 或 REG_OPENED_EXISTING_KEY (如果该键存在并已打开)。

### <a name="return-value"></a>返回值

如果成功, 将返回 ERROR_SUCCESS 并打开该密钥。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

`Create`将[m_hKey](#m_hkey)成员设置为此项的句柄。

##  <a name="cregkey"></a>CRegKey::CRegKey

构造函数。

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
对 `CRegKey` 对象的引用。

*hKey*<br/>
注册表项的句柄。

*pTM*<br/>
指向 CAtlTransactionManager 对象的指针

### <a name="remarks"></a>备注

创建一个新的 `CRegKey` 对象。 可以从现有`CRegKey`对象或从注册表项的句柄创建对象。

##  <a name="dtor"></a>CRegKey:: ~ CRegKey

析构函数。

```
~CRegKey() throw();
```

### <a name="remarks"></a>备注

析构函数将`m_hKey`释放。

##  <a name="deletesubkey"></a>CRegKey::D eleteSubKey

调用此方法以从注册表中移除指定的键。

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>参数

*lpszSubKey*<br/>
指定要删除的密钥的名称。 此名称必须是[m_hKey](#m_hkey)的子项。

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

`DeleteSubKey`只能删除没有子项的键。 如果该注册表项具有子项, 请改为调用[RecurseDeleteKey](#recursedeletekey) 。

##  <a name="deletevalue"></a>CRegKey::D eleteValue

调用此方法可从[m_hKey](#m_hkey)中删除值字段。

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>参数

*lpszValue*<br/>
指定要删除的值字段。

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

##  <a name="detach"></a>CRegKey::D etach

调用此方法可将[m_hKey](#m_hkey)成员句柄与`CRegKey`对象分离, 并将设置`m_hKey`为 NULL。

```
HKEY Detach() throw();
```

### <a name="return-value"></a>返回值

与`CRegKey`对象关联的 HKEY。

##  <a name="enumkey"></a>CRegKey::EnumKey

调用此方法以枚举打开的注册表项的子项。

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>参数

*iIndex*<br/>
子项索引。 对于第一次调用, 此参数应为零, 并在后续调用中递增

*pszName*<br/>
指向接收子项名称 (包括终止 null 字符) 的缓冲区的指针。 仅将子项的名称复制到缓冲区, 而不是复制到整个键层次结构。

*pnNameLength*<br/>
指向变量的指针, 该变量指定由*pszName*参数指定的缓冲区的大小 (以 TCHARs 为大小)。 此大小应包括终止 null 字符。 当该方法返回时, 由*pnNameLength*指向的变量包含缓冲区中存储的字符数。 返回的计数不包括终止 null 字符。

*pftLastWriteTime*<br/>
指向一个变量的指针, 该变量接收上次写入枚举子项的时间。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

若要枚举子项, 请`CRegKey::EnumKey`调用索引为零的。 递增索引值, 并重复此方法, 直到方法返回 ERROR_NO_MORE_ITEMS。 有关详细信息, 请参阅 Windows SDK 中的[RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) 。

##  <a name="flush"></a>CRegKey:: Flush

调用此方法将打开的注册表项的所有属性写入注册表。

```
LONG Flush() throw();
```

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

有关详细信息, 请参阅 Windows SDK 中的[RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) 。

##  <a name="getkeysecurity"></a>CRegKey::GetKeySecurity

调用此方法以检索保护打开的注册表项的安全描述符的副本。

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>参数

*si*<br/>
[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)值, 指示请求的安全信息。

*psd*<br/>
指向缓冲区的指针, 该缓冲区接收请求的安全描述符的副本。

*pnBytes*<br/>
*Psd*所指向的缓冲区的大小 (以字节为单位)。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值是在 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

有关详细信息, 请参阅[RegGetKeySecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity)。

##  <a name="m_hkey"></a>CRegKey::m_hKey

包含与`CRegKey`对象关联的注册表项的句柄。

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>CRegKey::m_pTM

指向 `CAtlTransactionManager` 对象的指针。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>备注

##  <a name="notifychangekeyvalue"></a>CRegKey::NotifyChangeKeyValue

此方法通知调用方对打开的注册表项的属性或内容所做的更改。

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>参数

*bWatchSubtree*<br/>
指定一个标志, 该标志指示是报告指定键及其所有子项中的更改还是仅报告指定键中的更改。 如果此参数为 TRUE, 则方法会报告键及其子项中的更改。 如果参数为 FALSE, 则方法仅报告键中的更改。

*dwNotifyFilter*<br/>
指定一组用于控制应报告哪些更改的标志。 此参数可以是下列值的组合:

|值|含义|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|如果添加或删除了子项, 请通知调用方。|
|REG_NOTIFY_CHANGE_ATTRIBUTES|通知调用方对密钥属性的更改, 例如安全描述符信息。|
|REG_NOTIFY_CHANGE_LAST_SET|通知调用方对密钥值的更改。 这可能包括添加或删除值, 或更改现有值。|
|REG_NOTIFY_CHANGE_SECURITY|通知调用方对密钥的安全描述符进行了更改。|

*hEvent*<br/>
事件的句柄。 如果*bAsync*参数为 TRUE, 则方法将立即返回, 并通过发出此事件的信号来报告更改。 如果*bAsync*为 FALSE, 则将忽略*hEvent* 。

*bAsync*<br/>
指定一个标志, 该标志指示方法如何报告更改。 如果此参数为 TRUE, 则方法立即返回, 并通过发出指定的事件信号来报告更改。 如果此参数为 FALSE, 则在发生更改之前, 方法不会返回。 如果*hEvent*未指定有效事件, 则*bAsync*参数不能为 TRUE。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

> [!NOTE]
>  如果删除了指定的密钥, 则此方法不通知调用方。

有关更多详细信息和示例程序, 请参阅[RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue)。

##  <a name="open"></a>CRegKey:: Open

调用此方法以打开指定的密钥, 并将[m_hKey](#m_hkey)设置为此密钥的句柄。

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>参数

*hKeyParent*<br/>
打开键的句柄。

*lpszKeyName*<br/>
指定要创建或打开的项的名称。 此名称必须是*hKeyParent*的子项。

*samDesired*<br/>
密钥的安全访问权限。 默认值为 KEY_ALL_ACCESS。 有关可能的值和说明的列表, 请参阅 Windows SDK 中的[RegCreateKeyEx](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) 。

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS;否则为 WINERROR.H 中定义的非零错误值。高.

### <a name="remarks"></a>备注

如果*lpszKeyName*参数为 NULL 或指向一个空字符串, `Open`则会打开由*hKeyParent*标识的密钥的新句柄, 但不会关闭任何以前打开的句柄。

与[CRegKey:: Create](#create)不同`Open` , 如果不存在指定的键, 则不会创建它。

##  <a name="operator_hkey"></a>CRegKey:: operator HKEY

`CRegKey`将对象转换为 HKEY。

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>CRegKey:: operator =

赋值运算符。

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>参数

*key*<br/>
要复制的键。

### <a name="return-value"></a>返回值

返回对新密钥的引用。

### <a name="remarks"></a>备注

此运算符从当前的对象中分离*键*, 并改为`CRegKey`将其分配给对象。

##  <a name="querybinaryvalue"></a>CRegKey::QueryBinaryValue

调用此方法可以检索指定的值名称的二进制数据。

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要查询的值的名称。

*pValue*<br/>
指向接收值的数据的缓冲区的指针。

*pnBytes*<br/>
指向变量的指针, 该变量指定*pValue*参数指向的缓冲区的大小 (以字节为单位)。 当该方法返回时, 此变量包含复制到缓冲区的数据的大小。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 ERROR_SUCCESS。 如果该方法无法读取值, 则它将返回在 WINERROR.H 中定义的非零错误代码。高. 如果引用的数据的类型不是 REG_BINARY, 则返回 ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`和确认返回了正确的数据类型。 有关更多详细信息, 请参阅[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 。

> [!IMPORTANT]
>  此方法允许调用方指定任何注册表位置, 可能会读取无法信任的数据。 此外, 此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不显式处理 NULL 终止的字符串。 调用代码应检查两个条件。

##  <a name="querydwordvalue"></a>CRegKey::QueryDWORDValue

调用此方法可以检索指定的值名称的 DWORD 数据。

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要查询的值的名称。

*dwValue*<br/>
指向接收 DWORD 的缓冲区的指针。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 ERROR_SUCCESS。 如果该方法无法读取值, 则它将返回在 WINERROR.H 中定义的非零错误代码。高. 如果引用的数据不是 REG_DWORD 类型, 则返回 ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`和确认返回了正确的数据类型。 有关更多详细信息, 请参阅[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 。

> [!IMPORTANT]
>  此方法允许调用方指定任何注册表位置, 可能会读取无法信任的数据。 此外, 此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不显式处理 NULL 终止的字符串。 调用代码应检查两个条件。

##  <a name="queryguidvalue"></a>CRegKey::QueryGUIDValue

调用此方法可以检索指定的值名称的 GUID 数据。

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要查询的值的名称。

*guidValue*<br/>
指向接收 GUID 的变量的指针。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 ERROR_SUCCESS。 如果该方法无法读取值, 则它将返回在 WINERROR.H 中定义的非零错误代码。高. 如果引用的数据不是有效的 GUID, 则返回 ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`CRegKey::QueryStringValue` [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)并将字符串转换为 GUID。

> [!IMPORTANT]
>  此方法允许调用方指定任何注册表位置, 可能会读取无法信任的数据。

##  <a name="querymultistringvalue"></a>CRegKey::QueryMultiStringValue

调用此方法可以检索指定的值名称的多字符串数据。

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要查询的值的名称。

*pszValue*<br/>
指向接收多字符串数据的缓冲区的指针。 多字符串是以 null 结尾的字符串数组, 以两个 null 字符结尾。

*pnChars*<br/>
*PszValue*指向的缓冲区的大小 (以 TCHARs 为大小)。 当方法返回时, *pnChars*包含检索到的多字符串的大小 (以 TCHARs 为限), 其中包括终止 null 字符。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 ERROR_SUCCESS。 如果该方法无法读取值, 则它将返回在 WINERROR.H 中定义的非零错误代码。高. 如果引用的数据不属于类型类型, 则返回 ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`和确认返回了正确的数据类型。 有关更多详细信息, 请参阅[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 。

> [!IMPORTANT]
>  此方法允许调用方指定任何注册表位置, 可能会读取无法信任的数据。 此外, 此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不显式处理 NULL 终止的字符串。 调用代码应检查两个条件。

##  <a name="queryqwordvalue"></a>CRegKey::QueryQWORDValue

调用此方法可以检索指定值名称的 QWORD 数据。

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要查询的值的名称。

*qwValue*<br/>
指向接收 QWORD 的缓冲区的指针。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 ERROR_SUCCESS。 如果该方法无法读取值, 则它将返回在 WINERROR.H 中定义的非零错误代码。高. 如果引用的数据的类型不是 REG_QWORD, 则返回 ERROR_INVALID_DATA。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`和确认返回了正确的数据类型。 有关更多详细信息, 请参阅[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 。

> [!IMPORTANT]
>  此方法允许调用方指定任何注册表位置, 可能会读取无法信任的数据。 此外, 此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不显式处理 NULL 终止的字符串。 调用代码应检查两个条件。

##  <a name="querystringvalue"></a>CRegKey::QueryStringValue

调用此方法可以检索指定的值名称的字符串数据。

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要查询的值的名称。

*pszValue*<br/>
指向接收字符串数据的缓冲区的指针。

*pnChars*<br/>
*PszValue*指向的缓冲区的大小 (以 TCHARs 为大小)。 当方法返回时, *pnChars*包含所检索的字符串的大小 (以 TCHARs 为限), 其中包括终止 null 字符。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 ERROR_SUCCESS。 如果该方法无法读取值, 则它将返回在 WINERROR.H 中定义的非零错误代码。高. 如果引用的数据不是 REG_SZ 类型, 则返回 ERROR_INVALID_DATA。 如果该方法返回 ERROR_MORE_DATA, 则*pnChars*等于零, 而不是所需的缓冲区大小 (以字节为单位)。

### <a name="remarks"></a>备注

此方法使用`RegQueryValueEx`和确认返回了正确的数据类型。 有关更多详细信息, 请参阅[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 。

> [!IMPORTANT]
>  此方法允许调用方指定任何注册表位置, 可能会读取无法信任的数据。 此外, 此方法使用的[RegQueryValueEx](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)函数不显式处理 NULL 终止的字符串。 调用代码应检查两个条件。

##  <a name="queryvalue"></a>CRegKey::QueryValue

调用此方法来检索[m_hKey](#m_hkey)的指定值字段的数据。 此方法的早期版本不再受支持, 并且已标记为 ATL_DEPRECATED。

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向以 null 结尾的字符串的指针, 该字符串包含要查询的值的名称。 如果*pszValueName*为 NULL 或空字符串 "", 则方法将检索密钥的未命名值或默认值 (如果有) 的类型和数据。

*pdwType*<br/>
指向一个变量的指针, 该变量接收指示指定值中存储的数据类型的代码。 如果类型代码不是必需的, 则*pdwType*参数可以为 NULL。

*pData*<br/>
指向接收值的数据的缓冲区的指针。 如果数据不是必需的, 则此参数可以为 NULL。

*pnBytes*<br/>
指向变量的指针, 该变量指定*pData*参数指向的缓冲区的大小 (以字节为单位)。 当该方法返回时, 此变量包含复制到 PData 的数据的大小 *。*

*dwValue*<br/>
值字段的数值数据。

*lpszValueName*<br/>
指定要查询的值字段。

*szValue*<br/>
值字段的字符串数据。

*pdwCount*<br/>
字符串数据的大小。 其值最初设置为*szValue*缓冲区的大小。

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS;否则为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

的两个原始版本`QueryValue`已不再受支持, 并标记为 ATL_DEPRECATED。 如果使用这些窗体, 编译器将发出警告。

其余方法调用 RegQueryValueEx。

> [!IMPORTANT]
>  此方法允许调用方指定任何注册表位置, 可能会读取无法信任的数据。 此外, 此方法使用的 RegQueryValueEx 函数不显式处理 NULL 终止的字符串。 调用代码应检查两个条件。

##  <a name="recursedeletekey"></a>CRegKey::RecurseDeleteKey

调用此方法以从注册表中删除指定的键, 并显式删除所有子项。

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>参数

*lpszKey*<br/>
指定要删除的密钥的名称。 此名称必须是[m_hKey](#m_hkey)的子项。

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS;否则为 WINERROR.H 中定义的非零错误值。高.

### <a name="remarks"></a>备注

如果该注册表项具有子项, 则必须调用此方法以删除该项。

##  <a name="setbinaryvalue"></a>CRegKey::SetBinaryValue

调用此方法可设置注册表项的二进制值。

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向字符串的指针, 该字符串包含要设置的值的名称。 如果具有此名称的值尚不存在, 则该方法会将其添加到键。

*pValue*<br/>
指向缓冲区的指针, 该缓冲区包含要使用指定的值名称存储的数据。

*nBytes*<br/>
指定由*pValue*参数指向的信息的大小 (以字节为单位)。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将该值写入注册表。

##  <a name="setdwordvalue"></a>CRegKey::SetDWORDValue

调用此方法可设置注册表项的 DWORD 值。

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向字符串的指针, 该字符串包含要设置的值的名称。 如果具有此名称的值尚不存在, 则该方法会将其添加到键。

*dwValue*<br/>
要与指定的值名称一起存储的 DWORD 数据。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将该值写入注册表。

##  <a name="setguidvalue"></a>CRegKey::SetGUIDValue

调用此方法可设置注册表项的 GUID 值。

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向字符串的指针, 该字符串包含要设置的值的名称。 如果具有此名称的值尚不存在, 则该方法会将其添加到键。

*guidValue*<br/>
对要与指定的值名称一起存储的 GUID 的引用。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

此方法使用`CRegKey::SetStringValue` [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2)将 GUID 转换为字符串。

##  <a name="setkeyvalue"></a>CRegKey::SetKeyValue

调用此方法可将数据存储在指定键的指定值字段中。

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>参数

*lpszKeyName*<br/>
指定要创建或打开的注册表项的名称。 此名称必须是[m_hKey](#m_hkey)的子项。

*lpszValue*<br/>
指定要存储的数据。 此参数必须为非 NULL。

*lpszValueName*<br/>
指定要设置的值字段。 如果密钥中不存在具有此名称的值字段, 则会将其添加。

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS;否则为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

调用此方法可创建或打开*lpszKeyName*键, 并将*lpszValue*数据存储在*lpszValueName*值字段中。

##  <a name="setkeysecurity"></a>CRegKey::SetKeySecurity

调用此方法可设置注册表项的安全性。

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>参数

*si*<br/>
指定要设置的安全描述符的组件。 该值可以是下列值的组合:

|值|含义|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|设置密钥的自由访问控制列表 (DACL)。 密钥必须具有 WRITE_DAC 访问权限, 或者调用进程必须是对象的所有者。|
|GROUP_SECURITY_INFORMATION|设置密钥的主要组安全标识符 (SID)。 密钥必须具有 WRITE_OWNER 访问权限, 或者调用进程必须是对象的所有者。|
|OWNER_SECURITY_INFORMATION|设置密钥的所有者 SID。 密钥必须具有 WRITE_OWNER 访问权限, 或者调用进程必须是对象的所有者或已启用 SE_TAKE_OWNERSHIP_NAME 特权。|
|SACL_SECURITY_INFORMATION|设置密钥的系统访问控制列表 (SACL)。 密钥必须具有 ACCESS_SYSTEM_SECURITY 访问权限。 获取此访问权限的正确方法是在调用方的当前访问令牌中启用 SE_SECURITY_NAME[权限](/windows/win32/secauthz/privileges), 打开 ACCESS_SYSTEM_SECURITY access 的句柄, 然后禁用该权限。|

*psd*<br/>
指向[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)结构的指针, 该结构指定要为指定键设置的安全特性。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

设置键的安全特性。 有关更多详细信息, 请参阅[RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) 。

##  <a name="setmultistringvalue"></a>CRegKey::SetMultiStringValue

调用此方法可设置注册表项的多字符串值。

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向字符串的指针, 该字符串包含要设置的值的名称。 如果具有此名称的值尚不存在, 则该方法会将其添加到键。

*pszValue*<br/>
指向多字符串数据的指针, 该数据将与指定的值名称一起存储。 多字符串是以 null 结尾的字符串数组, 以两个 null 字符结尾。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将该值写入注册表。

##  <a name="setqwordvalue"></a>CRegKey::SetQWORDValue

调用此方法可设置注册表项的 QWORD 值。

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向字符串的指针, 该字符串包含要设置的值的名称。 如果具有此名称的值尚不存在, 则该方法会将其添加到键。

*qwValue*<br/>
要与指定的值名称一起存储的 QWORD 数据。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将该值写入注册表。

##  <a name="setstringvalue"></a>CRegKey:: SetStringValue

调用此方法可设置注册表项的字符串值。

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向字符串的指针, 该字符串包含要设置的值的名称。 如果具有此名称的值尚不存在, 则该方法会将其添加到键。

*pszValue*<br/>
指向要以指定的值名称存储的字符串数据的指针。

*dwType*<br/>
要写入注册表的字符串类型: REG_SZ (默认值) 或 REG_EXPAND_SZ (对于 sql-dmo)。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回值为 ERROR_SUCCESS。 如果该方法失败, 则返回值为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

此方法使用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)将该值写入注册表。

##  <a name="setvalue"></a>CRegKey:: SetValue

调用此方法可将数据存储在[m_hKey](#m_hkey)的指定值字段中。 此方法的早期版本不再受支持, 并且已标记为 ATL_DEPRECATED。

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>参数

*pszValueName*<br/>
指向字符串的指针, 该字符串包含要设置的值的名称。 如果具有此名称的值不在该键中, 则该方法会将其添加到键。 如果*pszValueName*为 NULL 或空字符串 "", 则方法将为密钥的未命名值或默认值设置类型和数据。

*dwType*<br/>
指定指示*pValue*参数指向的数据类型的代码。

*pValue*<br/>
指向缓冲区的指针, 该缓冲区包含要使用指定的值名称存储的数据。

*nBytes*<br/>
指定由*pValue*参数指向的信息的大小 (以字节为单位)。 如果数据的类型为 REG_SZ、REG_EXPAND_SZ 或 REG_MULTI_SZ, 则*nBytes*必须包含终止 null 字符的大小。

*hKeyParent*<br/>
打开键的句柄。

*lpszKeyName*<br/>
指定要创建或打开的项的名称。 此名称必须是*hKeyParent*的子项。

*lpszValue*<br/>
指定要存储的数据。 此参数必须为非 NULL。

*lpszValueName*<br/>
指定要设置的值字段。 如果密钥中不存在具有此名称的值字段, 则会将其添加。

*dwValue*<br/>
指定要存储的数据。

*bMulti*<br/>
如果为 false, 则指示字符串的类型为 REG_SZ。 如果为 true, 则指示字符串是类型为 REG_MULTI_SZ 的多字符串。

*nValueLen*<br/>
如果*bMulti*为 true, 则*nValueLen*是*lpszValue*字符串的长度 (以字符为限)。 如果*bMulti*为 false, 则值为-1 表示方法将自动计算长度。

### <a name="return-value"></a>返回值

如果成功, 则返回 ERROR_SUCCESS;否则为 WINERROR.H 中定义的非零错误代码。高.

### <a name="remarks"></a>备注

的两个原始版本`SetValue`标记为 ATL_DEPRECATED, 不应再使用。 如果使用这些窗体, 编译器将发出警告。

第三个方法调用[RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)。

## <a name="see-also"></a>请参阅

[DCOM 示例](../../overview/visual-cpp-samples.md)<br/>
[类概述](../../atl/atl-class-overview.md)
