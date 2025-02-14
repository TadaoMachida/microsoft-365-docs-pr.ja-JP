---
title: 正確なデータ一致の機密情報ソース テーブル ファイルを更新する
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: 機密情報ソース テーブル ファイルを更新します。
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 310663caae55bb9b5e0d07cb38ba9fa4b45e8a73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621669"
---
# <a name="refresh-your-exact-data-match-sensitive-information-source-table-file"></a>正確なデータ一致の機密情報ソース テーブル ファイルを更新する 

機密情報データベースは、24 時間ごとに最大 5 回更新できます。 機密情報のソース テーブルを再ハッシュしてアップロードする必要があります。

1. 機密データを Microsoft Excel などのアプリに再エクスポートし、ファイルを.csv、.tsv 形式、またはパイプ (|) 区切り形式で保存します。 以前にファイルをハッシュしてアップロードしたときに使用したものと同じファイル名と場所を保持します。 機密データをエクスポートして正しい形式に取得する方法の詳細については、「 [完全一致ベースの機密情報の種類のソース](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type) データをエクスポートする」を参照してください。

      > [!NOTE]
      > 機密情報ソース テーブル ファイルの構造 (フィールド名) に変更がない場合は、データを更新するときにデータベース スキーマ ファイルを変更する必要はありません。 ただし、変更が必要な場合は、必要に応じてデータベース スキーマとルール パッケージを編集してください。 スキーマを編集または削除する手順については、 [完全なデータ一致スキーマを管理](sit-use-exact-data-manage-schema.md#manage-your-exact-data-match-schema) します。 EDM SIT/rule パッケージを編集または削除する手順については、「 [厳密なデータ一致の機密情報の種類/規則](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) パッケージを作成する」を参照してください。

2. ハッシュの手順を使用 [し、厳密なデータ一致の機密情報の種類の機密情報ソース テーブル](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types) をアップロードして、機密情報テーブルのソース ファイルをアップロードします。

3. [タスク スケジューラを](/windows/desktop/TaskSchd/task-scheduler-start-page)使用してハッシュを自動化[し、厳密なデータ一致の機密情報の種類のプロシージャの機密情報ソース テーブルをアップロード](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)できます。 タスクのスケジュールを設定するにはいくつかの方法があります。

   |メソッド|操作|
   |---|---|
   |PowerShell|[ScheduledTasks](/powershell/module/scheduledtasks/) のドキュメントと、この記事の [PowerShell スクリプトの例](#example-powershell-script-for-task-scheduler)を参照してください。|
   |タスク スケジューラ API|[Task Scheduler](/windows/desktop/TaskSchd/using-the-task-scheduler) のドキュメントを参照してください。|
   |Windows のユーザー インターフェイス|Windows の場合、**[スタート]** をクリックし、「タスク スケジューラ」と入力します。 次に、結果のリストで **[タスク スケジューラ]** を右クリックし、**[管理者として実行]** を選択します。|

## <a name="example-powershell-script-for-task-scheduler"></a>タスク スケジューラの PowerShell スクリプトの例

このセクションには、データをハッシュしたり、ハッシュされたデータをアップロードするタスクのスケジュールに使用できる PowerShell スクリプトの例が含まれています。

### <a name="schedule-hashing-and-upload-in-a-combined-step"></a>結合された手順でハッシュとアップロードをスケジュールする

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext"
$uploadDataArgs = '/UploadData /DataStoreName ' + $dataStoreName + ' /DataFile ' + $dataFile + ' /HashLocation' + $hashLocation + ' /Schema ' + $schemaFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadDataArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```

### <a name="schedule-hashing-and-upload-as-separate-steps"></a>ハッシュをスケジュールし、別の手順としてアップロードする

```powershell
param(\[string\]$dataStoreName,\[string\]$fileLocation)
\# Assuming current user is also the user context to run the task
$user = "$env:USERDOMAIN\\$env:USERNAME"
$edminstallpath = 'C:\\Program Files\\Microsoft\\EdmUploadAgent\\'
$edmuploader = $edminstallpath + 'EdmUploadAgent.exe'
$csvext = '.csv'
$edmext = '.EdmHash'
$schemaext = '.xml'
\# Assuming file name is same as data store name and file is in .csv format
$dataFile = "$fileLocation\\$dataStoreName$csvext"
$hashFile = "$fileLocation\\$dataStoreName$edmext"
\# Assuming Schema file name is same as data store name
$schemaFile = "$fileLocation\\$dataStoreName$schemaext "

\# Assuming location to store hash file is same as the location of csv file
$hashLocation = $fileLocation
$createHashArgs = '/CreateHash' + ' /DataFile ' + $dataFile + ' /HashLocation ' + $hashLocation + ' /Schema ' + $schemaFile
$uploadHashArgs = '/UploadHash /DataStoreName ' + $dataStoreName + ' /HashFile ' + $hashFile
\# Set up actions associated with the task
$actions = @()
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $createHashArgs -WorkingDirectory $edminstallpath
$actions += New-ScheduledTaskAction -Execute $edmuploader -Argument $uploadHashArgs -WorkingDirectory $edminstallpath
\# Set up trigger for the task
$trigger = New-ScheduledTaskTrigger -Weekly -DaysOfWeek Sunday -At 2am
\# Set up task settings
$principal = New-ScheduledTaskPrincipal -UserId $user -LogonType S4U -RunLevel Highest
$settings = New-ScheduledTaskSettingsSet -RunOnlyIfNetworkAvailable -StartWhenAvailable -WakeToRun
\# Create the scheduled task
$scheduledTask = New-ScheduledTask -Action $actions -Principal $principal -Trigger $trigger -Settings $settings
\# Get credentials to run the task
$creds = Get-Credential -UserName $user -Message "Enter credentials to run the task"
$password=\[Runtime.InteropServices.Marshal\]::PtrToStringAuto(\[Runtime.InteropServices.Marshal\]::SecureStringToBSTR($creds.Password))
\# Register the scheduled task
$taskName = 'EDMUpload\_' + $dataStoreName
Register-ScheduledTask -TaskName $taskName -InputObject $scheduledTask -User $user -Password $password
```
