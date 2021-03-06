# Monetra Module for Magento 2

The Monetra Module for Magento 2 allows you to easily configure your Magento 2 instance to process payments through a
Monetra server. The module utilizes the Monetra PaymentFrame feature, receiving payment information in an iframe provided by the Monetra server. This ensures that sensitive payment data is never entered into your website's front end or sent to your Magento server.

## Installation

The module can be installed with Composer. From the root directory of your Magento 2 installation, run the following commands:
```
composer require monetra/monetra_magento2
bin/magento-cli setup:upgrade
```

## Configuration

Once the Monetra Module is installed on your Magento instance, you will need to provide some configuration values for it
in the Magento admin. Navigate to Stores => Configuration => Sales => Payment Methods. You should see "Monetra PaymentFrame"
in the list of payment methods. Click on the arrow icon to expand the configuration option list.

- **Enabled**: Must be set to "Yes" in order to use the Monetra PaymentFrame payment method.

- **Payment Action**: If this is set to "Authorize Only", initial placement of an order will only authorize (not capture) the provided card. In other words, when an order is placed, the `sale` transaction sent to Monetra will include `capture=no`. If this option is set to "Authorize and Capture", the `sale` transaction will omit the `capture` parameter (which defaults to `yes`).

- **Title**: The name for the payment method that will be displayed on the user-facing checkout page.

- **New Order Status**: The default status that will be assigned to newly placed orders.

- **Monetra Host**: Hostname (FQDN) of the Monetra server that your Magento instance will be sending transactions to.

- **Monetra Port**: Port number on the Monetra server that transactions will be sent to. Usually this will be 8665.

- **Monetra Username**: The username of the Monetra user (for authentication on the Monetra server).

- **Monetra Password**: The password of the Monetra user (for authentication on the Monetra server). Stored encrypted via `Magento\Config\Model\Config\Backend\Encrypted`

- **Expiration Date Format**: Format of the expiration date input on the payment form.

- **Auto-reload**: If "Yes", automatically reload the checkout page every 15 minutes to avoid payment form timing out. Defaults to "Yes".

- **Autocomplete**: If "Yes", enable browser autocomplete for payment form fields. Defaults to "No".

- **CSS Path**: Path to CSS file that will be used to style the payment form. Must be hosted on same domain as Magento store. If empty, no custom CSS will be applied.

- **User-Facing Payment Denial Message**: The message that the user will see during the checkout process if their provided credit card is denied for any reason.

- **User-Facing Payment Error Message**: The message that the user will see during the checkout process if an internal error within the module prevents the sale from successfully completing.

- **Sort Order**: Determines where this payment method will appear in relation to other payment methods on the checkout page. For example, if the sort order for this method is set to 1, and the sort order for another payment method is set to 2, this one will appear above the other one on the list of payment method options.

## More Information

For details on how the Monetra PaymentFrame feature works, please see the Monetra PaymentFrame Guide available at [https://www.monetra.com/developers](https://www.monetra.com/developers).
