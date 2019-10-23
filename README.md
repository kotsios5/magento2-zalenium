# Magento 2 Zalenium
Integrates Zalenium for improved testing with the functional testing framework

# Features
Zalenium will still work with Magento 2's functional testing framework and automated browser testing but will not 
display test steps, name tests within Zalenium correctly or record if the test passed or failed.

This library aims to make the integration much better by setting the correct cookies with the Magento web driver to make
Zalenium correctly report how tests are passing or failing.

# Configuration
When working with your Magento 2 acceptance tests, after you have generated the tests and configuration files you
can add the Zalenium plugin as a module in the Codeception configuration.

Add the module to the modules enabled list in `dev/tests/acceptance/tests/functional.suite.yml`
Your configuration should then look like:

```yaml
class_name: AcceptanceTester
namespace: Magento\FunctionalTestingFramework
modules:
    enabled:
        - \Magento\FunctionalTestingFramework\Module\MagentoWebDriver
        - \Magento\FunctionalTestingFramework\Helper\Acceptance
        - \Magento\FunctionalTestingFramework\Helper\MagentoFakerData
        - \EdmondsCommerce\TestOverrides\Zalenium
        - \Magento\FunctionalTestingFramework\Module\MagentoSequence
        - \Magento\FunctionalTestingFramework\Module\MagentoAssert
        - Asserts
```

