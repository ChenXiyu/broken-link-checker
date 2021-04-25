# Broken Link Checker
Broken Link Checker is a tool deployed at AWS and can help you monitor your page protect you from hyper-link failure.

The broken link checker was implemented base on AWS Synthetics, but it is slightly different compare with the native one provided by AWS.
It is a more precise version of the broken link checker.

> What's different compare with the native one?

This revised version will not dive into the page to check sub-links which is not in the domains we are willing to check.

For example, We got a page that referenced an external link like `apple.com`.
* This revised broken link checker will check `apple.com` but will not check any sub-links inside the `apple.com`.
* The native implementation will check `apple.com` as well as the sub-links inside the `apple.com` as long as the `limit(depth)` has been set big enough.

## How to use it?
* Mutating `deployments/prod/parameters.yml` file to fulfill your requirements.
    Change the `TagetUrls` to the URL list you are willing to check, multi-value are supported, just separate the list with a comma(`,`).
* Authenticating to you AWS account(exported `AWS_SESSION_TOKEN`, `AWS_SECRET_ACCESS_KEY`, `AWS_DEFAULT_REGION`, `AWS_ACCESS_KEY_ID` in your terminal).
* Deploy Broken Link Checker by execute `auto/deploy prod`
