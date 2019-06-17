---
title: Managed 偵錯與 Unity IL2CPP
description: 這篇文章說明如何對 Unity IL2CPP UWP 專案中執行 managed 偵錯工具。
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: unity，visual studio 中，偵錯，il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148853"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Managed 偵錯與 Unity IL2CPP

請遵循下列步驟來將受管理的偵錯工具附加至 Unity IL2CPP UWP 組建。 原本是本指南所開發的 HoloLens 和 HoloLens 2。

1. 請確認**InternetClientServer**並**PrivateNetworkClientServer**簽入 Unity 在 UWP 的發行設定功能。

    ![UWP 發佈設定功能](images/il2cpp-debugging-capabilities.png)

1. 設定 Unity UWP 建置設定：
    - 開發組建
    - 指令碼偵錯
    - 等候 （選擇性） Managed 偵錯工具

    ![UWP 建置設定](images/il2cpp-debugging-build.png)

1. 在 Unity 中建置。
1. 建置並從 Visual Studio 方案部署到您的裝置。 您應該使用建置**偵錯**或是**發行**組態。 **主要**組態停用 Unity 分析工具，並可防止最佳的偵錯。 （選擇性） 請確認**網際網路 （用戶端和伺服器）** 並**私人網路 （用戶端和伺服器）** 方案中的 在 Package.appxmanifest 中的功能清單中。
1. 在您的裝置上啟動應用程式。 請確定您的裝置連線到您的電腦相同的網路。
1. 請確定裝置**不是**連線到您的電腦透過 USB。
1. 移至 Visual Studio 方案，當您按兩下在 Unity 中，您可以在其中檢視和編輯指令碼會建立您C#指令碼。
1. 偵錯]-> [附加 Unity 偵錯工具。

    ![附加 Unity 偵錯工具](images/il2cpp-debugging-attach.png)

1. 在清單中選取您的裝置，然後按一下 [確定] 以附加。

    ![裝置清單](images/il2cpp-debugging-machines.png)
