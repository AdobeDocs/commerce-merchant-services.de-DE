---
title: '"Beheben von Problemen bei der [!DNL Quick Checkout]"'
description: '"Beheben Sie Fehler, bekannte Probleme, die bei der Verwendung des [!DNL Quick Checkout] für die Adobe Commerce-Erweiterung."'
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Fehlerbehebung [!DNL Quick Checkout] für Adobe Commerce

Verwenden Sie die folgenden Methoden zur Fehlerbehebung, um diese spezifischen Probleme zu beheben.

## Falsch [!DNL Composer keys]

Wenn die folgende Fehlermeldung angibt, dass Sie die falsche [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Stellen Sie sicher, dass [!DNL Composer keys] sind mit der Magento-ID verknüpft, die während der Schnellauscheckregistrierung verwendet wird.

Welche [!DNL Composer keys] konfiguriert werden:

1. Suchen Sie den Speicherort der `auth.json` Datei:

   ```bash
   composer config --global home
   ```

1. Anzeigen der `auth.json` Datei:

   ```bash
   cat /path/to/auth.json
   ```

1. Siehe [welche Schlüssel Ihrer Magento-ID zugeordnet sind](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

## Mindeststabilität im `composer.json` ist auf &quot;stable&quot;eingestellt

Wenn die folgende Fehlermeldung angibt, dass Sie die falsche [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Setzen Sie die Mindeststabilität auf `RC` im `composer.json` -Datei.

## Nicht genügend Speicher für PHP

Wenn Sie den folgenden Fehler sehen, der angibt, dass Sie nicht genügend Speicher für PHP haben:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Erhöhen Sie die Speicherbegrenzung.](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) für PHP in Ihrer Umgebung in `php.ini`.

Alternativ können Sie die Speicherbegrenzung mit diesem Befehl angeben: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Beispiel:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Ungültige Versandadresse

Es gibt ein bekanntes Problem für die [!DNL Quick Checkout].

Wenn die standardmäßige Lieferadresse ungültig ist, wird der Kunde zum Schritt Lieferadresse weitergeleitet. Storefront zeigt nur gültige Lieferadressen an.

>[!WARNING]
>
> wenn keine gültige Lieferadresse vorhanden ist, wird dem Kunden keine Lieferadresse angezeigt.

Siehe Abschnitt [Versanddetails](../quick-checkout/shipping-details.md) für weitere Informationen.

## Hinzufügen von Adresszeilen mit neuer Lieferadresse

Es gibt ein bekanntes Problem für die [!DNL Quick Checkout].

Wenn Sie [mit einem [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) Sie können eine neue Lieferadresse mit einer Begrenzung von 4 Zeilen pro Straßenadresse hinzufügen.

Adobe Commerce kann in der Regel so konfiguriert werden, dass bis zu 20 Adresszeilen unterstützt werden.

## Kontrollkästchen `enable terms and conditions` nicht ordnungsgemäß angezeigt

Es gibt ein bekanntes Problem für die [!DNL Quick Checkout].

Wenn Sie die `Enable terms and conditions` in der Admin-Checkbox und melden Sie sich mit einem [!DNL Bolt] -Konto, `Enable terms and conditions` wird während des Checkout nicht angezeigt. Siehe Abschnitt [Anmelden](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] für weitere Informationen.

Siehe [Bedingungen](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) Thema für weitere Informationen zur Admin-Konfiguration.

## Unerwartetes Verhalten bei `Display Billing Address On` auf `payment page`

Es gibt ein bekanntes Problem für die [!DNL Quick Checkout].

Wenn Sie `Display Billing Address On` Parameter auf `payment page` und [Anmeldung mit [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) Wenn Sie die `My billing and shipping address are the same` Kontrollkästchen, das das Optionsfeld anzeigt `use existing card`.

![Gleiche Adresse](assets/checked-address.png)

Siehe [Checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) Weitere Informationen zum Thema `Display Billing Address On` Parameter.

## Übersetzen der [!DNL Quick Checkout] Erweiterung

Mit Adobe Commerce können Sie Ihren Store für mehrere Regionen und Märkte lokalisieren. Sie können sogar Fehlermeldungen in Ihrer Admin-Ansicht lokalisieren.

Siehe Abschnitt [Übersetzen und Lokalisieren](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) für weitere Informationen.

## Cache leeren

1. Navigieren Sie zu **[!UICONTROL System]** > **[!UICONTROL Cache Management]** und klicken Sie auf **[!UICONTROL Flush Cache]** , um alle ungültigen Caches zu aktualisieren.

## Hilfe erhalten

Kontakt [Adobe Commerce-Support](mailto:quick-checkout-support@adobe.com) Hilfe.
