# Embed Checkout Form in Kajabi Pages
[![jsDelivr hits (npm)](https://img.shields.io/jsdelivr/npm/hm/osi4kjb-embed-checkout-form?color=blue&label=downloads&logo=jsdelivr)](https://www.jsdelivr.com/package/npm/osi4kjb-embed-checkout-form) [![GitHub](https://img.shields.io/github/license/jasongodev/osi4kjb-embed-checkout-form?&color=blue&logo=github)](LICENSE) [![CodeQL](https://github.com/jasongodev/osi4kjb-embed-checkout-form/actions/workflows/github-code-scanning/codeql/badge.svg)](https://github.com/jasongodev/osi4kjb-embed-checkout-form/actions/workflows/github-code-scanning/codeql) [![](https://img.shields.io/badge/Code%20Style-Standard-brightgreen?logo=javascript)](https://standardjs.com/)

Popularly known as the ECF script, this utility script makes it easy to embed Kajabi checkout forms inside any Kajabi site pages and product pages from the same Kajabi site.

## Features
- Embeds checkout forms seamlessly.
- Works with couponized checkout urls.
- Works with "logged in" checkouts.
- Works even on product/course pages.
- Multiple checkout forms can be embedded in a page.
- Easy to install. One and same script to embed to Kajabi site header setting and checkout header setting.
- Works with Checkmate Integration.

## Installation
Installation has two parts. First, you need to add the script so that when your Kajabi site loads, the script is also loaded. Usually you will only do the first part once.

Second part is telling the script which checkout form is embedded to a specific page. You will do this part every time you will embed a checkout form in a specific page.

### Part 1: Add the script to your Kajabi settings.
1. Copy the script code below:

```html
<script src="https://cdn.jsdelivr.net/npm/osi4kjb-embed-checkout-form@1/dist/ecf.min.js"></script>
```

2. Paste the code in **two locations**. Yep, not one, but two locations. Not doing so will make the script useless.

 * **1st Location:** Kajabi Admin Settings => Site Details => Page Scripts

 * **2nd Location:** Kajabi Admin Settings => Checkout Settings => Header Tracking Code
3. Always click Save for each settings.

### Part 2: Embed a specific checkout form in a Kajabi page.

1. In any Kajabi Page within your domain, add a Custom Code Block

2. Copy and paste this code in the Custom Code Block

```html
<script>
ECF("https://www.yourdomain.com/offers/abcdefgh/checkout");
</script>
```
3. Change the url inside the **ECF("...")** function, and replace it with your own Kajabi Checkout URL.

4. Click Save.

## Advanced Configuration
**ECF( url, config);**

**url** = The checkout url. You can only embed checkout forms that are under the same Kajabi Site. Custom domain name and mykajabi.com versions of your checkout page will both work to any of the pages within your site.

**config** = javascript object with the following default format:

```js
{
    width: '100%', // Width of the checkout form iframe. Change to suit your design.
    height: 'auto', // Height of the iframe. Change it to CSS values if you need to have a fixed height.
    id: autogenerated, // Specify a unique iframe id if you need to access the DOM element or CSS selector
    spinner: true, // Set to false if you don't want a spinner
    animation: 'animate__fadeIn', // Set to 'none' to disable animation. You can have other animation styles by using the animate.css classes at https://animate.style
    resizer: { // The resizer options corresponding to the IframeResizer library. See here: https://github.com/davidjbradshaw/iframe-resizer
        log: false,
        heightCalculationMethod: 'taggedElement' // The taggedElement estimation works best with Kajabi. The data-iframe-height attribute needed to detect the height is attached to #new_checkout_offer. See the documentation for other options if height is not adjusting with your design.
    }
}
```