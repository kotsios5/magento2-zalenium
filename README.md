# Magento2 Zalenium Plugin
Integrates Zalenium for improved testing with the functional testing framework

## Setup
To use the Zalenium plugin inside your acceptance tests you need to add `EdmondsCommerce\Zalenium\Zalenium`
to your `dev/tests/acceptance/tests/functional.suite.yml` in the `modules area.

**Partial Example**
```yaml
class_name: AcceptanceTester
namespace: Magento\FunctionalTestingFramework
modules:
    enabled:
        - \Magento\FunctionalTestingFramework\Module\MagentoWebDriver
        - \Magento\FunctionalTestingFramework\Helper\Acceptance
        - \Magento\FunctionalTestingFramework\Helper\MagentoFakerData
        - \Magento\FunctionalTestingFramework\Module\MagentoSequence
        - \Magento\FunctionalTestingFramework\Module\MagentoAssert
        - \Magento\FunctionalTestingFramework\Module\MagentoActionProxies
        - Asserts
        - EdmondsCommerce\Zalenium\Zalenium

```

You must also ensure that (depending on your installation) self signed certificates are accepted.
This is set using the Chrome capabilities options in teh same file.

```yaml
    config:
        \Magento\FunctionalTestingFramework\Module\MagentoWebDriver:
            url: "%MAGENTO_BASE_URL%"
            backend_url: "%MAGENTO_BACKEND_BASE_URL%"
            backend_name: "%MAGENTO_BACKEND_NAME%"
            browser: 'chrome'
            restart: true
            window_size: 1280x1024
            username: "%MAGENTO_ADMIN_USERNAME%"
            password: "%MAGENTO_ADMIN_PASSWORD%"
            pageload_timeout: "%WAIT_TIMEOUT%"
            host: "%SELENIUM_HOST%"
            port: "%SELENIUM_PORT%"
            protocol: "%SELENIUM_PROTOCOL%"
            path: "%SELENIUM_PATH%"
            capabilities:
                acceptInsecureCerts: true # This one
                chromeOptions:
                    args: ["--window-size=1280,1024", "--disable-extensions", "--enable-automation", "--disable-gpu", "--enable-Passthrough"]
```
