---
title: Voids
description: Mit Voids können Sie die Gelder in einem Kredit- oder Debitkartenkonto freigeben, das durch eine Genehmigung für die Höhe eines Kaufs gesperrt oder zurückgehalten wird.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Voids

Mit [!DNL Payment Services]können Sie bestehende Commerce-Funktionen verwenden, um Transaktionen zu vermeiden. Mit Voids können Sie die Gelder in einem Kredit- oder Debitkartenkonto freigeben, das durch eine Genehmigung für die Höhe eines Kaufs gesperrt oder zurückgehalten wird.

>[!NOTE]
>
>Sie können eine Transaktion nur dann aufheben, wenn die Zahlung noch nicht erfasst wurde.

Wenn Ihr Store [konfiguriert](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} um nur (nicht erfassen) Mittel an der Verkaufsstelle zu genehmigen, führt ein Kauf in Ihrem Geschäft zu einer Bestellung mit einer `Processing` -Status in der Commerce-Admin.

Sie können auch [Bestellung stornieren](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} nicht in Rechnung gestellt wird. Nicht erfasste Berechtigungen werden im Rahmen dieses Löschungsprozesses ebenfalls aufgehoben.

>[!NOTE]
>
>Das Abbrechen einer Bestellung führt ebenfalls zu einer Nichtigkeit, aber die Nichtigerklärung einer Bestellung Trigger keine Stornierung.

Weitere Informationen zu den grundlegenden Schritten, die eine Bestellung durchführt, finden Sie in der [Workflow &quot;Auftrag&quot;](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} Thema im Benutzerhandbuch.

Weitere Informationen zur Funktion &quot;Leere&quot;und zum Nichterheben einer Bestelltransaktion finden Sie unter [Verarbeitung einer Bestellung](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} im Benutzerhandbuch zu zentralen Themen.
